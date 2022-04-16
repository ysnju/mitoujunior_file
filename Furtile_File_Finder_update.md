Current function

<img width="851" alt="Screenshot 2022-04-14 at 1 16 54" src="https://user-images.githubusercontent.com/89366347/163660238-14a664ab-69e3-4de5-aa31-ce007ee5dc1b.png">



https://user-images.githubusercontent.com/89366347/163660304-08c638a5-ba59-4aad-80c5-659431154cce.mov

must do
Login screen に問題あり
日程の選択をカレンダーにする

want to do 
file typeを選択型にする
addressの決まっているところは初めから入っているようにする


*Passoword hash successful
<img width="1227" alt="Screenshot 2022-04-16 at 12 48 29" src="https://user-images.githubusercontent.com/89366347/163660347-34d0148c-95d2-481d-90f5-5f9dfa8da3b8.png">

```py
import random

from kivy.lang import Builder
from kivymd.app import MDApp
from kivymd.uix.datatables import MDDataTable
from kivymd.uix.screen import MDScreen
import sqlite3

from passlib.context import CryptContext

pwd_context = CryptContext(
    schemes=["pbkdf2_sha256"],
    default="pbkdf2_sha256",
    pbkdf2_sha256__default_rounds=30000
)


def encrypt_password(password):
    return pwd_context.encrypt(password)


def check_password(password, hashed):
    return pwd_context.verify(password, hashed)


hash_pwd = encrypt_password("password123")
# print(hash_pwd)
# print(check_password("password", hash_pwd))
# print(check_password("password123", hash_pwd))

class my_database_handler:
    def __init__(self,name):
        self.name = name
        #connect to the database
        self.connection = sqlite3.connect(self.name)
        #track where we are in table 何列めか
        self.cursor = self.connection.cursor()


    def close(self):
        self.connection.close()


#not null means it must be filled 必須項目
    def create(self):
        self.cursor.execute("""CREATE TABLE if not exists Users(
            id INTEGER primary key autoincrement,
            username VARCHAR(200),
            email VARCHAR(255) not null unique,
            password VARCHAR(256) not null       
        );
        """)
        self.cursor.execute("""CREATE TABLE if not exists Files(
                    id INTEGER primary key autoincrement,
                    filename VARCHAR(200),
                    filetype VARCHAR(255),
                    filesize INTEGER,    
                    lastopened VARCHAR(255), 
                    firstcreated VARCHAR(255), 
                    address VARCHAR(255) 
                );
                """)
        self.connection.commit()

    def create_test_user(self):
        #set username password email

        self.cursor.execute("""INSERT into Users values (1,"test", "test@test","qwerty");
                """)
        self.connection.commit()
    def create_new_user(self, username, password, email):
        print(username,password,email)
        self.cursor.execute("INSERT into Users values (?,?,?,?)",(random.randint(1,1000000),username, email, encrypt_password(password)))
        self.connection.commit()

    def create_new_file(self,filename,filetype,filesize,lastopened,firstcreated,address):
        print(filename,filesize,firstcreated)
        self.cursor.execute("INSERT into Files values (?,?,?,?,?,?,?)",(random.randint(1,1000000),filename,filetype,filesize,lastopened,firstcreated,address))
        self.connection.commit()


    def get_all_users(self):
        result = self.cursor.execute("SELECT * from Users;")
        print(result.fetchall())

    def query_user(self,email,password):
        result = self.cursor.execute(f"SELECT * from Users where email='{email}';")
        #this function returns none if the usser does not exist or the id if it does
        return result.fetchone()
    def query_files(self):
        result = self.cursor.execute("SELECT * from Files;")
        return result.fetchall()

class RegistrationScreen(MDScreen):
    def register(self):
        print("registering")
        email_entered = self.ids.email.text
        username_entered = self.ids.username.text
        password_entered = self.ids.password.text
        print(email_entered, password_entered)
        db = my_database_handler("app_database.db")
        db.create_new_user(username=username_entered, email=email_entered,password=password_entered)
        db.close()
        self.parent.current = "Welcome Screen"

class WelcomeScreen(MDScreen):
    pass

class LoginScreen(MDScreen):
    def try_login(self):
        print("trying loging")
        email_entered = self.ids.email.text
        password_entered = self.ids.password.text

        print(email_entered, password_entered)


        #we need to query the database
        db = my_database_handler("app_database.db")
        user = db.query_user(email = email_entered, password = password_entered)
        print(f"{user}")
        if user:
            id,username,email,password_hash = user
            if check_password(password_entered,password_hash) == True:
                self.parent.current = "Welcome Screen"
            else:
                self.ids.login_label.text = "user does not exist"
        #we need to query the database
        #user exists go to welcome screen
        #The parent of the login schreen is the screen manager





    def go_to_register(self):
        self.parent.current = "Registration Screen"

class login(MDApp):
    def build(self):
        return

class NewitemScreen(MDScreen):
    def register_new_file(self):
        print("registering")
        filename_entered = self.ids.filename.text
        filetype_entered = self.ids.filetype.text
        filesize_entered = self.ids.filesize.text
        lastopened_entered = self.ids.lastopened.text
        firstcreated_entered = self.ids.firstcreated.text
        address_entered = self.ids.address.text
        print(filename_entered, filetype_entered)
        nf = my_database_handler("file_database.db")
        nf.create_new_file(filename=filename_entered, filetype=filetype_entered,filesize=filesize_entered,lastopened=lastopened_entered,firstcreated=firstcreated_entered,address=address_entered)
        db.close()
        self.parent.current = "Table Screen"


class TableScreen(MDScreen):
    deta_tables = None #class attribute
    def on_pre_enter(self,*args):
        """get data from database"""
        db = my_database_handler("app_database.db")
        query = db.query_files()
        db.close()

        self.data_tables = MDDataTable(
            size_hint=(1, 0.5),
            pos_hint={"center_x": .5, "top": 0.8},
            use_pagination=False,
            check=True,
            # name column, width column, sorting function column(optional)
            column_data=[
                ("id", 28),
                ("filename", 30),
                ("filetype", 50),
                ("filesize", 40),
                ("lastopened", 40),
                ("firstcreated", 40),
                ("address", 40)
            ],
            row_data=query
        )
        self.data_tables.bind(on_row_press=self.on_row_press)
        self.data_tables.bind(on_row_press=self.on_check_press)
        self.add_widget(self.data_tables)


    def on_row_press(self,Files,row):
        print(f"Item was clicked",row)
        print(row.text)

    def on_check_press(self,table,current_row):
        print("row pressed",current_row)
        id,username,password,email = current_row
        print(f"the user selected was {id}")

db = my_database_handler("app_database.db")
db.create()
# db.create_test_user()
nf = my_database_handler("file_database.db")
nf.create()

m = login()
m.run()
db.close()
nf.close()





```


ScreenManager:
    id:scr_manager
    LoginScreen:
        name:"Login Screen"

    RegistrationScreen:
        name:"Registration Screen"

    WelcomeScreen:
        name:"Welcome Screen"

    TableScreen:
        name:"Table Screen"

    NewitemScreen:
        name:"Newitem Screen"

<loginScreen>:
    BoxLayout:
        size_hint:0.95,0.95
        orientation:"vertical"
        pos_hint:{"center_x":0.5,"center_y":0.5,}

        FitImage:
            source:"files.jpeg"
            #how to resize image to fit as background
    MDCard:
        orientation:"vertical"
        size_hint: .85, .85
        elevation: 0
        pos_hint: {"center_x": .5, "center_y": .5}
        md_bg_color:[255/255, 255/255, 255/255, 0.2]

        MDBoxLayout:
            id: logincontent
            adaptive_height: True
            orientation: "vertical"
            padding: dp(60)
            spacing: dp(60)

            MDLabel:
                id: Program_label
                text:"Furtile-File-Finder"
                halign: "center"
                font_size: "80px"
            MDTextField:
                id:email
                hint_text: "email"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1
            MDTextField:
                id:password
                hint_text: "password"
                password: True
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1
            MDRaisedButton:
                text:"login"
                hint_text:"email"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.try_login()
            MDRaisedButton:
                text:"signup"
                hint_text:"register"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.parent.current = "Registration Screen"

<RegistrationScreen>
    BoxLayout:
        size_hint:0.95,0.95
        orientation:"vertical"
        pos_hint:{"center_x":0.5,"center_y":0.5,}

        FitImage:
            source:"files.jpeg"
            #how to resize image to fit as background
    MDCard:
        orientation:"vertical"
        size_hint: .85, .85
        elevation: 0
        pos_hint: {"center_x": .5, "center_y": .5}
        md_bg_color:[255/255, 255/255, 255/255, 0.2]

        MDBoxLayout:
            id: registerationcontent
            adaptive_height: True
            orientation: "vertical"
            padding: dp(60)
            spacing: dp(60)

            MDLabel:
                id: registration_label
                text:"Register"
                halign: "center"
                font_size: "80px"

            MDTextField:
                id:username
                hint_text: "username"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1

            MDTextField:
                id:email
                hint_text: "email"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1
            MDTextField:
                id:password
                hint_text: "password"
                line_color_focus: 9/225,1/225,169/225,1
            MDRaisedButton:
                text:"register"
                hint_text:"email"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.register()

<WelcomeScreen>
    BoxLayout:
        size_hint:0.95,0.95
        orientation:"vertical"
        pos_hint:{"center_x":0.5,"center_y":0.5,}

        FitImage:
            source:"files.jpeg"
            #how to resize image to fit as background

    MDCard:
        orientation:"vertical"
        size_hint: .85, .85
        elevation: 0
        pos_hint: {"center_x": .5, "center_y": .5}
        md_bg_color:[255/255, 255/255, 255/255, 0.2]

        MDBoxLayout:
            id:welcomecontent
            adaptive_height: True
            orientation: "vertical"
            padding: dp(60)
            spacing: dp(100)

            MDLabel:
                pos_hint: {"center_x": .5, "center_y": 0.5}
                text:"Welcome"
                halign:"center"
                font_size:"80px"

            MDRaisedButton:
                text:"New file"

                hint_text:"email"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.parent.current = "Newitem Screen"

            MDRaisedButton:
                text:"View table"

                hint_text:"email"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.parent.current = "Table Screen"

            MDRaisedButton:
                text:"Go back to login screen"
                hint_text:"login"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.parent.current = "Login Screen"


<TableScreen>
    BoxLayout:
        size_hint:0.95,0.95
        orientation:"vertical"
        pos_hint:{"center_x":0.5,"center_y":0.5,}

        FitImage:
            source:"files.jpeg"
            #how to resize image to fit as background

    MDCard:
        orientation:"vertical"
        size_hint: .85, .85
        elevation: 0
        pos_hint: {"center_x": .5, "center_y": .5}
        md_bg_color:[255/255, 255/255, 255/255, 0.2]

        MDBoxLayout:
            id:welcomecontent
            adaptive_height: True
            orientation: "vertical"
            padding: dp(60)
            spacing: dp(100)
            #Dr.Ruben code
            size_hint:.8,.08
            pos_hint:{"center_x":.5,"top":.2}

            MDLabel:
                pos_hint: {"center_x": .5, "center_y": 0.5}
                text:"Furtile Files"
                halign:"center"
                font_size:"80px"

            MDRaisedButton:
                text:"back to welcome screen"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.parent.current = "Welcome Screen"

<NewitemScreen>
    BoxLayout:
        size_hint:0.95,0.95
        orientation:"vertical"
        pos_hint:{"center_x":0.5,"center_y":0.5,}

        FitImage:
            source:"files.jpeg"
            #how to resize image to fit as background

    MDCard:
        orientation:"vertical"
        size_hint: .85, .85
        elevation: 0
        pos_hint: {"center_x": .5, "center_y": .5}
        md_bg_color:[255/255, 255/255, 255/255, 0.2]

        MDBoxLayout:
            size_hint:0.8,0.8
            orientation:"vertical"
            pos_hint:{"center_x":0.5}

            MDLabel:
                pos_hint: {"center_x": .5, "center_y": 0.5}
                text:"New Files"
                halign:"center"
                font_size:"80px"
            MDTextField:
                id:filename
                hint_text: "file name"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1

            MDTextField:
                id:filetype
                hint_text: "file type"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1
            MDTextField:
                id:filesize
                hint_text: "filesize"
                line_color_focus: 9/225,1/225,169/225,1

            MDTextField:
                id:lastopened
                hint_text: "last date"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1

            MDTextField:
                id:firstcreated
                hint_text: "create date"
                color_mode: 'accent'
                line_color_focus: 9/225,1/225,169/225,1

            MDTextField:
                id:address
                hint_text: "address"
                line_color_focus: 9/225,1/225,169/225,1

            MDRaisedButton:
                text:"back"
                hint_text:"back"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.back()
            MDRaisedButton:
                text:"create new file"
                hint_text:"create new file"
                md_bg_color:[1, 233/255, 165/255,  1]
                text_color:65/225,65/225,65/225,1
                on_release:
                    root.register_new_file()
