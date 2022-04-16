Current function

<img width="851" alt="Screenshot 2022-04-14 at 1 16 54" src="https://user-images.githubusercontent.com/89366347/163660238-14a664ab-69e3-4de5-aa31-ce007ee5dc1b.png">



https://user-images.githubusercontent.com/89366347/163660304-08c638a5-ba59-4aad-80c5-659431154cce.mov




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
