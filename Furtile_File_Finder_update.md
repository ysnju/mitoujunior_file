Current function

<img width="851" alt="Screenshot 2022-04-14 at 1 16 54" src="https://user-images.githubusercontent.com/89366347/163660238-14a664ab-69e3-4de5-aa31-ce007ee5dc1b.png">



https://user-images.githubusercontent.com/89366347/163660304-08c638a5-ba59-4aad-80c5-659431154cce.mov

# Unit 3:Project (develop for client) 

# Criteria A: Planning

## Problem definition
Because my client Bea uses her computer daily for years, she has files that use space on her computer. She wants to identify such files with a application, by file name, file size, file types, last updated date, date of the file created and file address. This is because the client does not want to delete any personal files that are kept on purpose. The application also requires a username and password to log in to insure private data can only be accessed by her.

## Proposed Solution
**Design Statement**
I will be solving my client's problem by creating an application that shows information about a file in a table. To do so, I will create the function of the application with the Python3.9 programming language, and the GUI(Graphical user interface) with KivyMD. The data needed in this application will be stored in SQLite.

Python3.9 will be the programming language used for this project since it is the most commonly used programming language, thus has more resources compared to others, which has helped the programmer learn more about the language, and now is the most useful programming language for the programmer personally. Other than this personal opinion, Python3.9 is an accessible language since it has a simple syntax and is close to natural language. It also is strong in a variety of libraries and frameworks that are beneficial for making the coding process easier. It records the most population for the usage of the language.

Kivy.MD will be used for the GUI since it allows to import, cross-platform and link with a Python library, in this case, Python3.9. Other than the easy installation, Kivy.MD allows the user to code in a language that is extremely similar to natural language. It also has a similar composition as python, which uses indentation and colons. Because of Kivy.MD is a framework that creates a GUI for the developer, it will run by opening a GUI screen as the output. 

SQLite will be used to create and manage the information provided by the user into a database. SQL is one of the most popular languages to interact with databases, with the ability to have almost all the functions related to data table creation. This fits with the client's need, to show their files on a table. Also, because of its file format and cross-platform, and easy interaction with Python3, it has been chosen as the implementor of the SQL database engine. 


## Success Criteria

1.There is a log-in screen that requires a username and password to log in

2.Screen after the log-in screen shows **file names** of files in oldest Last updated date order

3.Screen after the log-in screen shows **file size** of files in oldest Last updated date order

4.Screen after the log-in screen shows **file types** of files in oldest Last updated date order

5.Screen after the log-in screen shows the **last updated date** of files in oldest Last updated date order

6.Screen after the log-in screen shows the **date of the file created** in oldest Last updated date order

7.Screen after the log-in screen shows **file address** of files in oldest Last updated date order

## appendix(evidence of client aproving the sucsess criteria)(voice video script email exchange)
https://user-images.githubusercontent.com/89366347/157995571-2c2406aa-52a2-4bfa-88c7-36c9f4a6b6fa.MOV



# Criteria B: Design
#Test plan
| instruction              | category                                  | input                                                               | expected output                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | description                                            | Success Criteria |
|--------------------------|-------------------------------------------|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|------------------|
| Test Registration Screen | Unit test/Integration test                | Email, username,password                                            | Unit test 1. Email, username, hashed password in the database 2. Shift to Welcome Screen when the register is pushed Integration test Check if the expected out put is produced when processes 1 and 2 are combined                                                                                                                                                                                                                                                                                                                                      | Test GUI Test SQLite cooperation                       | None             |
| Test Login Screen        | Unit test/Integration test                | email,password                                                      | Unit test 1.print user when input of user and user in database are the same 2. Shift to Welcome Screen when hash of password entered by user and hashed password match 3.Text on Login Screen becomes "wrong password" when hash of password entered by the user and hashed password do not match 4. Text on Login Screen becomes "wrong email" when email in database and email entered by user do not match Integration test.  Check if 1 2 3 and 4 work when user inputs multiple times orders tested 1-3-4-2 1-4-3-2 3-4-1-2 3-1-4-2 4-3-1-2 4-1-3-2 | Test GUI Test SQLite cooperation Test Python functions | 1                |
| Test Welcome Screen      | Unit test                                 | User clicks button                                                  | Unit test 1.User clicks New item screen and screen shifts to New item screen 2.User clicks Table and screen shifts to Table Screen 3.User clicks to back and screen shifts to log in screen                                                                                                                                                                                                                                                                                                                                                              | Test GUI                                               | None             |
| Test New table Screen    | Unit test/Integration test                | File name, file size, filetype, last opened, first created, address | Unit test 1.User inputs content, and data is saved in file 2. After file saved, screen shifts to table screen Integration test User does process 1 and 2 happens                                                                                                                                                                                                                                                                                                                                                                                         | Test GUI Test SQLite cooperation Test Python functions | None             |
| Test View table Screen   | Unit test                                 | User clicks button                                                  | Unit test 1.User clicks item in table and clicked item is printed  2.User clicks row in table and clicked row is printed 3.User clicks row that shows column type and all row is printed 4.User clicks edit file and screen shifts to edit screen 5.User clicks back file and screen shifts to Welcome screen                                                                                                                                                                                                                                            | Test GUI Test SQLite cooperation Test Python functions | 2,3,4,5,6,7      |
| Test Edit table Screen   | Usability test/Unit test/integration test | File name, file size, filetype, last opened, first created, address | Usability test 1.User can acsess all text fields and buttons needed on screen Unit test 1.User clicks row of file and content of file is in text field 2.User changes content in text field and clicks save and content in database is updated with the input in the text field 3.User clicks row and then clicks clear to delete content in text field 4.User clicks back and screen shifts to table screen Integration test All tests above function when conbined                                                                                     | Test GUI Test SQLite cooperation Test Python functions | None             |
| Test FAQ Screen          | Usability test/unit test                  | Problem ,date                                                       | Usability test                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Test GUI Test SQLite cooperation                       | None             |

## Record of Task
| Task No | Planned Action                    | Planned Outcome                                                                                              | Time estimate | Target completion date | Criterion |
|---------|-----------------------------------|--------------------------------------------------------------------------------------------------------------|---------------|------------------------|-----------|
| 1       | Meeting with client               | Identify their need                                                                                          | 20min         | 3/2                    | A         |
| 2       | Meeting with teacher              | Receive advice for appropriate methods that fulfill client needs effectively Discussion of proposed solution | 10min         | 3/4                    | A         |
| 3       | DecideProblem definition          | Embody the clients problem                                                                                   | 20min         | 3/4                    | A         |
| 4       | Identify success criteria         | To ensure the quality of the produced product                                                                | 10min         | 3/7                    | A         |
| 5       | Meeting with client               | To agree with the success criteria, if changes are needed, they are made here.                               | 10min         | 3/7                    | A         |
| 6       | Proposed solution                 | To justify the methods used for the project. To make sure the method used to solve the problem is effective. | 40min         | 4/20                   | A         |
| 7       | Screen creation                   | To understand the logistics of the method used to solve the problem                                          | 2 hr          | 3/28                   | B         |
| 8       | Meeting with client               | To agree with the method used, and meeting regarding wireframe diagram that suits client best                | 10min         | 3/30                   | A         |
| 9       | Create wireframe diagram          | To agree with the direction the solution is going                                                            | 40min         | 3/31                   | B         |
| 10      | Meeting with client               | New meeting to update success criteria(Client wanted more Privacy)                                           | 3hr           | 4/7                    | A         |
| 11      | Password encryption               | Learning password encryption                                                                                 | 2hr 30min     | 4/9                    | C         |
| 12      | Welcome Screen                    | Screen Transition                                                                                            | 1hr           | 4/11                   | C         |
| 13      | Registration Screen               | To allow the client to have multiple accounts                                                                | 1hr           | 4/15                   | C         |
| 14      | New Item Screen                   | To allow the client to add files                                                                             | 2hr           | 4/18                   | C         |
| 15      | Table Screen                      | To allow client to view files                                                                                | 2hr           | 4/16                   | C         |
| 16      | Edit Screen                       | To allow client to edit files                                                                                | 10hr          | 4/21                   | C         |
| 17      | Update Wireframe diagram          | To have a correlating wireframe diagram as the product                                                       | 1hr           | 4/4                    | B         |
| 18      | Create system/flow/ER/UML diagram | Create diagrams to help understand the code, and how it functions                                            | 5hr           | 4/21                   | C         |
| 19      | Final demonstration with client   | Final check with client                                                                                      | 20min         | 4/21                   | D         |
| 20      | Update Record of task   | To upddate record of task                                                                                     | 20min         | 4/22                   | B         |

## System Diagram
Fig1
<img width="1336" alt="Screenshot 2022-04-21 at 19 32 58" src="https://user-images.githubusercontent.com/89366347/164440053-23b972e9-f700-484f-9149-ac41f8b4c64b.png">
Fig1 is a system diagram of the applications used for the program. The program receives its input from the user by a keyboard and trackpad. The output is produced by going through different systems which are Pycharm, and Kivy.MD and Python. The input is either saved in SQLite or when input is a click the GUI(application interface) responds accordingly. When the output is visible to the user, it uses a Screen, which is the application interface. All the above is inside the macOS, which is in a Macbook Pro.

## Wireframe Diagram
Fig2
![IMG_AA96B34F8671-1](https://user-images.githubusercontent.com/89366347/164055907-838a0dc6-4c40-424b-be52-b159aa54c819.jpeg)
Fig2 is a Wireframe Diagram. It is used to show the shifts in between screens, and how the GUI is supposed to respond to inputs such as button clicks.

## Flow Diagrams
Flow diagrams visualize the actions taken in the code. It is practical because all options are in one diagram, and combined with the code, it is easy for a programmer to communicate the intention of the code.
Fig3
![IMG_BD727F87F057-1](https://user-images.githubusercontent.com/89366347/164468642-ff84a11c-2bab-4f23-b6f3-4c9761397884.jpeg)
Fig3 is a Flow Diagram is a diagram from the Login screen (in Subroutine Symbol) to the Welcome screen. The login screen is explained in Fig4

Fig4
![Untitled drawing](https://user-images.githubusercontent.com/89366347/164475192-32c4d133-f928-49b3-8341-4484224b8cd1.jpg)
Fig4 is a Flow Diagram of the login screen which was omitted in a Subroutine Symbol in Fig3.

## ER Diagram
Fig5
![Untitled presentation (1)](https://user-images.githubusercontent.com/89366347/164715511-ef16c5c7-7644-4cb3-82df-be2996d45092.jpg)
Fig5 is an ER diagram showing the relationship between the File table and the User table. The User can have multiple Files, however, the File cannot have multiple Users since one file is designated for one person. Files contain 7 attributes made by the user in the circles, and Users have 4 attributes.

## UML Diagrams
Fig6
![IMG_7D01D712569D-1](https://user-images.githubusercontent.com/89366347/164238708-8481dae4-f7ec-45e1-984f-7f04f2f77087.jpeg)
Fig6 is a UML Diagram which shows what a class contains. The User class contains four attributes on the diagram and can inherit multiple attributes from the File class.

# Criteria C: Development
1.Tools used in the program
2.Random
3.Python3.9
4.Kivy. MD
5.SQLite3/Relational database
6.Passlib/Crypt Context


Production process
1. Login Screen(Passlib/Crypt Context, Kivy. MD, Python3.9, SQLite3/Relational database)
2. Welcome Screen(Kivy. MD)
3. Register Screen(Random, Kivy. MD, Python3.9, SQLite3/Relational database)
4. Table Screen
5. Newitem Screen
6. Edit Screen
7. Contact Screen(same as Register screen)

## Setting up enviroment

[Kivy.MD]
When programming the application, the programming language used was Python3.9. Since Kivy.MD was most suitable to make a GUI that responds to the code written in Python, it required to have several libraries imported. 
To connect the Kivy.MD file and the Python3.9 file, the code below was needed.

```.md
ScreenManager:
   id:scr_manager
   LoginScreen:
       name:"Login Screen"

   RegistrationScreen:
       name:"Registration Screen"

   WelcomeScreen:
       id: Welcomescreen
       name:"Welcome Screen"

   TableScreen:
       name:"Table Screen"

   NewitemScreen:
       name:"Newitem Screen"

   EditScreen:
       id: edit_screen
       name: "edit_screen"

   ContactScreen:
       name:"Contact Screen"

```


On Kivy.MD, in order to make different screens for corresponding use, it is necessary to switch between screens. ScreenManager makes this possible. A screen manager is a widget that can manage multiple screens in an application. Fig89 has 7 screens in total to fulfill the success criteria, and for the best user experience. Each screen has an id or name or that allows the Python file and the Kivy.MD to identify the difference between each screen. 

[Python setup]
```py
class my_database_handler:
   def __init__(self,name):
       self.name = name
       #connect to the database
       self.connection = sqlite3.connect(self.name)
       #track where we are in table 何列めか
       self.cursor = self.connection.cursor()


   def close(self):
       self.connection.close()

```
For the program to function, python needs to connect to the database and be able to update the database. To do so it needs a a constructor in object oriente. This can be done with __init__ because this allows an object to be created from a class and it allows the class to initialize the attributes of the class.

[create tables]
```py
self.cursor.execute("""CREATE TABLE if not exists FAQ(
                   id INTEGER primary key autoincrement,
                   date VARCHAR(200),
                   problem VARCHAR(255)
               );
               """)
self.connection.commit()

```
To create tables, python needs to know what the attribute is, and what type it is inorder to successfully transmit the input to the database. Therefore, this code explains what the input is, and wether it is a integer or a varchar(string) with the amont of letters it should be able to contain. The if not exists creates the table it self when it does not exist, such as when it is the first time for the user to put the input in to a table. The same method is taken for the User file and the Table file.

[create new content for table]
```py
def create_new_file(self,filename,filetype,file_size,lastopened,firstcreated,address):
   print(filename,file_size,firstcreated)
   self.cursor.execute("INSERT into Files values (?,?,?,?,?,?,?)",(random.randint(1,1000000),filename,filetype,file_size,lastopened,firstcreated,address))
   self.connection.commit()

```
For this function to work, it requires self to update the content to the initializer, and all attributes so the function knows what goes where.It also needs an id to be able to identify different files. The id is a random integer that does not over lap, nd makes the identification possible. Self.cursor.execute is used to insert input in to the values. The same process is used for different attributes. 

```py
def query_user(self,email,password):
   result = self.cursor.execute(f"SELECT * from Users where email='{email}';")
   #this function returns none if the user does not exist or the id if it does
   return result.fetchone()

```
This uses query to identify the existence of a attribute and use for other functions. If attributes does not exist, it returns none. We need this function to identify different attributes in the same table, and will be explained further with the try login function.



Crypt Context
The client requires an encrypted password for safety. To encrypt a password and use the hash, we need 3 steps

```py
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


```
I import CryptContext from passlib to setup the hash and encryption for the password. There are different types of crypt format, in this case I used passlib.hash.sha256_crypt to prevent the password from leaking. 

encrypt_password returns the password inputted by the user in to hash. Because the returned password is inhash, there is no way for the programmer to know what the user put as their password and keeps teh password safe.
check_password checks the hashed password and the password inputted by the user to check whether they match
SQLite

The login screen is the first screen shown to the user and is a requirement. Because the login screen requires comparing the information inputted by the user and the information it holds in the SQLite3 database beforehand, it uses the self class. A self-class allows a programmer to access attributes and methods. Attributes that change content while the program is running go into the self class so that when the program refers to the attribute, it always points to the current content in the attribute. 

```py
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
           id, username, email, password_hash = user
           if check_password(password_entered,password_hash) == True and email_entered == email:
               self.parent.current = "Welcome Screen"
               self.parent.ids.Welcomescreen.ids.welcometext.text = f"welcome {username}"
           elif check_password(password_entered,password_hash) == False and email_entered == email:
               self.ids.login_label.text = "wrong password"
           else:
               self.ids.login_label.text = "404 user does not exist"
       else:
           self.ids.login_label.text = "wrong email"
       #we need to query the database
       #user exists go to welcome screen
       #The parent of the login schreen is the screen manager

```

Screens made with Kivy. MD 
Screens cannot be made without the GUI, which is the Kivy.MD file. Kivy.MD can have multiple of the same object under control by differentiating them with ids and names. This is used for differentiating screens, labels, buttons, and text fields in this project. The names in quotation marks are recognized in the python file, which allows the coordination between the Kivy.MD file and Python file to happen.

Kivy.MD has a similar construction as python, they use indentation to put content inside the other.

```.md
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
           spacing: dp(40)

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
               md_bg_color:[1, 233/255, 165/255,  1]
               text_color:65/225,65/225,65/225,1
               on_release:
                   print("login pressed")
                   root.try_login()
           MDRaisedButton:
               text:"signup"
               hint_text:"register"
               md_bg_color:[1, 233/255, 165/255,  1]
               text_color:65/225,65/225,65/225,1
               on_release:
                   root.parent.current = "Registration Screen"

           MDRaisedButton:
               text:"Contact"
               md_bg_color:[1, 233/255, 165/255,  1]
               text_color:65/225,65/225,65/225,1
               on_release:
                   print("contact")
                   root.parent.current = "Contact Screen"

           MDLabel:
               id: login_label
               text:"Login status"
               halign: "center"
               font_size: "30px"

```
MDLabels are texts that show on the screen. They cannot be edited by the user. However, by using self.ids.login_label.text they are editable from the python file.

MDRaised Buttons are buttons that can detect clicks from users. 

MDText field allows 	the user to input information. Then functions made in the python file can transport the information to SQLite3.

[Welcome Screen]
```.md
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
               text: "Welcome {username}"
               id: welcometext
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

```

The Kivy.MD for the welcome screen is just to take users to one screen to another. To do this, the on_release detects the click of the button, and after the colon, the action needed to take is programmed. For the best user experience it is recommended to make the screens efficient and easy to understand. Having this screen is a convenient way for the user to go through the Screens.

[Register Screen(Random, Kivy. MD, Python3.9, SQLite3/Relational database)]
```py
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

```
```.md
MDRaisedButton:
   text:"register"
   md_bg_color:[1, 233/255, 165/255,  1]
   text_color:65/225,65/225,65/225,1
   on_release:
       root.register()

```
The registration screen needs to transmit new input to SQLite3 database to register a new user. For the new user information to be transferred, variables for te inputted information must be made. After variables are defined with self.ids.{attribute_name}.text, the database also needs a variable. The variable db and the .create_new_user(Explained wth create_new_file), the function is applied to the database. Updating the columns with the new variable for the input with an equal, and the content will be updated, and the database will close with the db.close function because the .close applies to the database variable name.

By putting the function above int he Kivy.MD file underneath root release, the function will be applied when the button is pressed.

[Table screen]
```py
class TableScreen(MDScreen):
   data_tables = None #class attribute
   def on_pre_enter(self,*args):
       """get data from database"""
       db = my_database_handler("app_database.db")
       query = db.query_files()
       db.close()

       if len(query)<2:
           query.append(["","","","","",""])

       self.data_tables = MDDataTable(
           size_hint=(1, 0.5),
           pos_hint={"center_x": .5, "top": 0.8},
           use_pagination=False,
           check=True,
           # name column, width column, sorting function column(optional)
           column_data=[
               ("id", 50),
               ("filename", 40),
               ("filetype", 40),
               ("file_size", 20),
               ("lastopened", 50),
               ("firstcreated", 50),
               ("address", 40)
           ],
           row_data=query
       )
       self.data_tables.bind(on_row_press=self.on_row_press)
       self.data_tables.bind(on_check_press=self.on_check_press)
       self.add_widget(self.data_tables)


   def on_row_press(self,table,row):
       print(f"Item was clicked",row)
       print(row.text)

   def on_check_press(self,table,current_row):
       print("row pressed",current_row)
       #filename,filetype,file_size,lastopened,firstcreated,address = current_row
       #print(f"the user selected was {filename}")

```
To view a table, on_pre_enter indicates the size and column size, data and what data to query. For this to work it also needs more than two files. Therefore there is a code to append empty data in columns to make the number of data more than two.  

[Edit Screen]
```py
class EditScreen(MDScreen):
   def on_pre_enter(self, *args):
       db = my_database_handler("app_database.db")
       data = db.query_all_changes()
       db.close()

       #The MDtable needs at least two values as input
       if len(data)<2:
           data.append(["","","","","",""])
       print(data)
       #create table. IMPORTANT name of the attribute is data_tables
       #cannot be changed
       self.data_tables = MDDataTable(
           size_hint =(1, 0.5),
           pos_hint = {"center_x":0.5, "top":0.8},
           check = True,
           column_data = [
               ("id", 50),
               ("filename", 40),
               ("filetype", 40),
               ("file_size", 20),
               ("lastopened", 50),
               ("firstcreated", 50),
               ("address", 40)
           ],
           row_data = data
       )
       # add the function to detect when a check in a row is pressed
       self.data_tables.bind(on_check_press=self.check_pressed)
       self.add_widget(self.data_tables)

   def check_pressed(self, table, row):
       # when a column is checked we read the id and price and put it in the TextEdit fields
       id, filename, filetype, file_size, lastopened, firstcreated, address = row
       self.ids.filename.text = filename
       self.ids.filetype.text = filetype
       self.ids.file_size.text = file_size
       self.ids.lastopened.text = lastopened
       self.ids.adress.text = address
       self.ids.id_text.text = id

   def edit_save(self):
       #here we update the database
       updated_id = self.ids.id_text.text
       updated_filename = self.ids.filename.text
       updated_filetype = self.ids.filetype.text
       updated_file_size = self.ids.file_size.text
       updated_lastopened = self.ids.lastopened.text
       updated_adress = self.ids.adress.text
       db = my_database_handler("app_database.db")
       db.update_row(id = updated_id,
           filename=updated_filename,
                     filetype=updated_filetype,
                     file_size=updated_file_size,
                     lastopened=updated_lastopened,
                     address=updated_adress)
       db.close()
       self.update_table()
       self.clear()
       print(updated_lastopened)

   def update_table(self):
       db = my_database_handler("app_database.db")
       data = db.query_all_changes()
       db.close()

       # The MDtable needs at least two values as input
       if len(data) < 2:
           data.append(["", "", "","", ""])

       self.data_tables.update_row_data(
           None, data
       )

   def clear(self):
       # clear the textfields
       self.ids.filename.text = ""
       self.ids.filetype.text = ""
       self.ids.file_size.text = ""
       self.ids.lastopened.text = ""
       self.ids.adress.text = ""

```
Edit screen requires to save, update and clear content. Clear is most self explanatory, it replaces the content with “” which contains nothing, to delete content. To update the table, the database needs to be opened and input from text field(refer to check_pressed) the content inside the textfield will replace the previous content by self.ids once again.

## Software updates
This application can collect any problem from the client when they use the contact button. The contact button is simmple, and less like ly to break, so I will be checking that once a week. However, there is a possibility for it to break, thus, I will be chevking the code with the test methods above once a month.
TextField https://kivymd.readthedocs.io/en/latest/components/textfield/?highlight=text+field TextField - KivyMD 1.0.0.dev0 documentation April 4, 2022

TextBox https://kivymd.readthedocs.io/en/latest/components/textbox/?highlight=text+field TextBox - KivyMD 1.0.0.dev0 documentation April 10, 2022

BoxLayout https://kivymd.readthedocs.io/en/latest/components/boxlayout/?highlight=sizehint BoxLayout - KivyMD 1.0.0.dev0 documentation April 10, 2022
# Criteria D: Functionality and Extensibility of the product

# Criteria E: Evaluation




