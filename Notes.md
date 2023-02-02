# Python Full Stack Application

Flask - MySQL - Bcrypt - sdfs
___
#### `1. Create a Project Folder with the basic files and folders required for every Flask App`
- ido_events
    - server.py
    - flask_app
        - init.py
        - config
            - mysqlconnection.py
        - controllers
        - models
        - static
        - templates

---

#### `2. Create your web app design using a wireframe tool like Balsamiq Wireframes, save file into Project Folder, and identify/define all of your visible and invisble routes`
- Routes should be identified in CRUD order and must include path variables < int:id >
- Visable routes are usually displayed as URLs in the wireframe
- Invisible routes are usually hyperlinks and buttons ~ Will this take us to a route we have already identified or a new invisble route?
- Example ~ The list of routes for this project are as follows:
    - `/`
    - `/events`
    - `/events/mydashboard`
    - `/events/new`
    - `/events/<int:id>/view`
    - `/events/<int:id>/edit`
    - `/events/<int:id>/delete`
    - `/billing`
    - `/billing/new`
    - `/billing/<int:id>/view`
    - `/billing/<int:id>/edit`
    - `/billing/<int:id>/delete`
---

#### `3. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database and save files into Project Folder`

<sup>* MySQL Workbench is a GUI that allows us to interact with MySQL, one of the most popular relational databases in the world. </sup><br>
<sup>* One of the most important things to remember about database design is <u>ORGANIZE DATA IN A WAY THAT MINIMIZES REPETITION</u></sup><br>
<sup>* Our database is the **backbone** of our application so its important to organize it in a way that maximizes efficiency and minimizes data queries.</sup>

> ### MYSQL STEPS
- Open MySQL Workbench, click on the model icon second one down on the left side, and create a new model
- Double click mydb and change the Schema Name
    - Best Practice for naming schemas ~ **lower case and use underscore to separate words.**
    - Example ~ `ido_event_schema`
- Click the 'Add Diagram' Button and begin building your ERD (entity relationship diagram)
    - ERD is a process of designing our tables and establishing relationships between them (relational data). How our database looks and behaves
- Screenshot the ERD and then go to File > Save Model As a `.mwb` file inside the project folder
    - Example ~ `ido_event_schema.mwb`
    - When any model changes are performed MySQL Workbench will automatically create a backup of the model file and this file type will end in  `.mwb.bak` 
- Forward engineer the model by clicking Database > Forward Engineer...
    - On first page, change nothing and click continue
    - Second page, checkbox the following:
        - DROP objects before each CREATE object
        - Generage DROP SCHEMA
            - If we are starting over with our database, this will delete our old databse so we will lose our previous data. (Best Practice to always click this because incase we have to reverse engineer and go back. This essentially allows us to 'start over')
        - Click Continue - This will prompt us to type in your password that was set up when you intially downloaded MySQL
    - Third and Fourth page, change nothing and click continue - Ths will again prompt us to type in our password.
    - If successful you will see 4 green check marks and the statement 'Forward Engineer Finished Successfully' > CLICK CLOSE
> ### REVERSE ENGINEER STEPS
- We can utilize reverse engineering when we have started our application but realize that we need to add something to the database. 
- First Open Model -> Add column 
> ### MYSQL TIPS / BEST PRACTICES
- When you add a new table to your ERD Diagram double click the table 
    - Rename the table to whatever your class name will be
        - Example ~ `users`
    - Checkmark the AI (auto increment) box for the first line item which is usually your primary key. This will auto checkmark PK and NN which stand for Primary Key and Not Null
    - Always include `create_at` and `update_at` as columns 
        - datatype ~ `DATETIME`
        - default/expression ~ `NOW()` and `NOW() ON UPDATE NOW()` must be all caps or there will be an error down the road.
- When identifying how many tables you need and what relationships each table has to one another ask yourself
    - Does one of x have many of y? 
    - Can one of y have many of x?
- Examples of different types of relationships in MySQL
    - One-to-One
        - *Event and Reciept - Every event has one reciept and every Reciept belongs to one event.*
        - <sup>Customers and Credit Cards - Every Customer Has one Credit Card, Every Credit Card belongs to One Customer</sup>
        - <sup>Product and Image - Every product has an Image and every Image is of a Product</sup>
    - One-to-Many
        - Event and Tasks - One event has many tasks, each task belongs to one event
        - States and Cities - One city is only in one state, but one state can have many cities
        - Messages and Comments - One comment belongs to one message but one message can have many comments
        - Customers and Orders - One order only has one customer, but one customer can have many orders
    - Many-to-Many
        - Each Event can have many planners, each planner can have many events
        - Actors and Movies - One movie can have many Actors, and One Actor can be in many movies
---
##### `Our Project Folder`
- **Project Folder**
    - *server.py file*
    <br><sup>Contains app itself and import ALL our controllers</sup>
    - **flask_app**
        - *_ _init_ _.py*
        <br><sup>Creates app and define secret key</sup>
        - **config**
            - *mysqlconnection.py*
            <br><sup>Allows us to talk to our database - code never really changes besides the password</sup>
        - **controllers**
        <br><sup>Where routes are defined. Essentially the names of our tables from our DB</sup>
        - **models**
        - **static**
            - **css**
                - *style.css*
            - **js**
                - *script.js*
        - **templates**
            - *something.html*
---
#### `3. Create and activate our Virtual Enviornment `
- Install pipenv globally 
    - mac: `pip3 install pipenv`
    - windows: `pip install pipenv`
- Inside project folder install flask, pymysql, and bcrypt
<br><sup>flask - this is essentially like adding a script tag to our html document. we are connecting the python to our html documents using flask as our package</sup>
<br><sup>pymysql - this allows us to connect with our database</sup>
<br><sup>bcrypt - </sup>
    - `pipenv install flask  PyMySQL flask-bcrypt`
- Start / Activate the enviornment
    - `pipenv shell`

---
#### `4. Create/Open server.py file and set up.`
- Input the following code and save
```PYTHON
from flask import Flask # By importing Flask we are allowing ourselves to create our app
app = Flask(__name__) #Create a new instance of the Flask class called "app"
@app.route('/') # The @ decorator associates this route with the function immediately following in this case hello_world
def hello_world():
    return 'Hello World!' # Returns Hello world as a response
if __name__=="__main__": # Ensures this file is being run directly and not from a differnt module
    app.run(debug=True) # runs the app in debug mode
```
```PYTHON
from flask import Flask 
app = Flask(__name__) 
@app.route('/') 
def hello_world():
    return 'Hello World!' 
if __name__=="__main__": 
    app.run(debug=True) 
```
- Once the Enviornment has been activated using `pipenv shell` in the terminal run the `server.py` file using `python server.py` and you should see the following inside the terminal
- To open the flask app in your browser you can copy and paste the link or you can press `CMD + CLICK THE LINK` And you should see **Hello World** in your browser.
> Serving Flask app 'server'<br>
> Debug mode: on<br>
> WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
> Running on http://127.0.0.1:5000 <br>
>Press CTRL+C to quit<br>
> Restarting with stat<br>
> Debugger is active!<Br>
> Debugger PIN: 411-191-804
- Once we have confirmed that our app is running correctly on our browser, we can start creating and organizing all necessary folders and files for our app.
- Or we can utilize a previously built template found in python-stack-assignments>lecture_tools>flask_template on my github
---
#### `5. Update our server.py file, init.py file, and connect to our database`
- In our `server.py` file we will now change the previous code to:
```PYTHON
from flask_app import app
# import all controllers here

if __name__=="__main__": 
    app.run(debug=True) 
```

- In our `init.py` file we will add the following code
```PYTHON
from flask import Flask 
app = Flask(__name__) 


app.secret_key = "ahhh"
```
- To connect to our database we will go into our config folder and open/create a file called `mysqlconnection.py` and enter the following code:
    - This code will almost never change, just make sure that your password is the correct password that you use for your mysql workbench
```PYTHON
# a cursor is the object we use to interact with the database
import pymysql.cursors
# this class will give us an instance of a connection to our database


class MySQLConnection:
    def __init__(self, db):
        # change the user and password as needed
        connection = pymysql.connect(host='localhost',
                                    user='root',
                                    password='rootroot',
                                    db=db,
                                    charset='utf8mb4',
                                    cursorclass=pymysql.cursors.DictCursor,
                                    autocommit=True)
        # establish the connection to the database
        self.connection = connection
    # the method to query the database

    def query_db(self, query, data=None):
        with self.connection.cursor() as cursor:
            try:
                query = cursor.mogrify(query, data)
                print("Running Query:", query)

                cursor.execute(query, data)
                if query.lower().find("insert") >= 0:
                    # INSERT queries will return the ID NUMBER of the row inserted
                    self.connection.commit()
                    return cursor.lastrowid
                elif query.lower().find("select") >= 0:
                    # SELECT queries will return the data from the database as a LIST OF DICTIONARIES
                    result = cursor.fetchall()
                    return result
                else:
                    # UPDATE and DELETE queries will return nothing
                    self.connection.commit()
            except Exception as e:
                # if the query fails the method will return FALSE
                print("Something went wrong", e)
                return False
            finally:
                # close the connection
                self.connection.close()
# connectToMySQL receives the database we're using and uses it to create an instance of MySQLConnection


def connectToMySQL(db):
    return MySQLConnection(db)
```
---
#### `3. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database.`
---
#### `3. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database.`
---
#### `3. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database.`
---













<br> enter

### H3
## H2
# H1
~~STRIKE THROUGH~~
**Bolded**

*Italicized*
`highlighted words`
 - D
 >Quoted Block

 ```JAVASCRIPT
var myName JAVASCRIPT CODE
 ```