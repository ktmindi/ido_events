# Python Full Stack Application

#### `1. Create your web app design using a wireframe tool like Balsamiq Wireframes and identify/define all of your visible and invisble routes`
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

#### `2. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database.`

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
---
##### `Now we will create a virtual enviornment`
- Install pipenv globally 
    - mac: `pip3 install pipenv`
    - windows: `pip install pipenv`
- Inside project folder install flask (this is essentially like adding a script tag to our html document. we are connecting the python to our html documents using flask as our package)
    - `pipenv install flask`
- Start / Activate the enviornment
    - `pipenv shell`
---
#### `3. Create your Project Folder and .`
---
#### `3. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database.`
---
#### `3. Examine your design and using a GUI (graphical user interface) like MySQL Workbench create a relational database.`
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