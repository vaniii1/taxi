# taxi-service

<h2>Description 📝</h2>

Taxi-service is a web application with convenient design and functionality which allows you to register, login and
logout using the credentials that are stored in DB. 


<h2>Instructions 📒</h2>

When you [_follow the link_](http://taxi-env.eba-68shdjjt.eu-north-1.elasticbeanstalk.com), the main page appears in front of you. It gives you a choice of all the actions you can
perform if you are logged in. If not, you are only allowed to two pages: _Login_ and _Create new Driver_.

<h3><center>Features</center></h3>

- Registration, logging in and logging out system.
- Display of drivers, manufacturers and cars.
- Display of cars of current driver
- Creating drivers, manufacturers and cars.
- Updating drivers, manufacturers and cars.
- Removing drivers, manufacturers and cars.


<h3><center>Usage</center></h3>
<table>
   <tr>
      <td><b><i>Method</i></b></td>
      <td><b><i>Url</i></b></td>
      <td><b><i>Response</i></b></td>
      <td><b><i>Fields to fill</i></b></td>
   </tr>
   <tr>
      <td>GET</td>
      <td><i>/index</i></td>
      <td>You are taken to the homepage</td>
      <td><i>NONE</i></td>
   </tr>
   <tr>
      <td>POST</td>
      <td><i>/login</i></td>
      <td>Log in to the application</td>
      <td>'login', 'password'</td>
   </tr>
   <tr>
      <td>POST</td>
      <td><i>/drivers/add or /register</i></td>
      <td>Creating a new driver to the DB</td>
      <td>'name', 'license_number', 'login', 'password'</td>
   </tr>
   <tr>
      <td>POST</td>
      <td><i>/manufacturers/add</i></td>
      <td>Creating a new manufacturer to the DB</td>
      <td>'name', 'country'</td>
   </tr>
   <tr>
      <td>POST</td>
      <td><i>/cars/add</i></td>
      <td>Creating a new car to the DB</td>
      <td>'model', 'manufacturer ID'</td>
   </tr>
   <tr>
      <td>POST</td>
      <td><i>/cars/drivers/add</i></td>
      <td>Adding driver to the car</td>
      <td>'car ID', 'driver ID'</td>
   </tr>
   <tr>
      <td>GET</td>
      <td><i>/drivers</i></td>
      <td>Displaying drivers</td>
      <td><i>NONE</i></td>
   </tr>
   <tr>
      <td>GET</td>
      <td><i>/manufacturers</i></td>
      <td>Displaying manufacturers</td>
      <td><i>NONE</i></td>
   </tr>
   <tr>
      <td>GET</td>
      <td><i>/cars</i></td>
      <td>Displaying cars</td>
      <td><i>NONE</i></td>
   </tr>
   <tr>
      <td>GET</td>
      <td><i>/driver/cars</i></td>
      <td>Displaying cars of currently logged in driver</td>
      <td><i>NONE</i></td>
   </tr>
</table>


<h2>Startup guide 🚀</h2>

If you decided to start up this project, you need to obtain at least java 17 and MySQL. The file with SQL code
(package named "resources" on the same level with "java" package) you can compile in MySQL environment. When your DB is
ready for use you need to change some fields in ConnectionUtil.class:  
```
private static final String URL = "YOUR URL";
private static final String USERNAME = "YOUR USERNAME";
private static final String PASSWORD = "YOUR PASSWORD";
private static final String JDBC_DRIVER = "YOUR JDBC DRIVER";
```

___Tomcat configuration:___

To add tomcat configuration you need to choose: Run  ->  Edit Configurations  ->  click the plus in the top left corner  ->
search for Tomcat Server  ->  local  ->  configure... (in the right window that appears)  ->  insert the path where your
tomcat is installed  ->  OK  ->  Fix (in the right bottom corner)  ->  choose 'war exploded artifact'  ->  deployment (on the top bar)  ->  change application context to "/".
<p>
I use tomcat 10 on this application, but if you want to use tomcat 9 you have to change jakarta to javax dependency.
In addition, you will have to change some class imports which contains `jakarta`. Then, you need to rebuild your project (Ctrl + F9).
</p>

```
<dependency>                                                            
        <groupId>jakarta.servlet</groupId>
        <artifactId>jakarta.servlet-api</artifactId>
        <version>5.0.0</version>
        <scope>provided</scope>
</dependency> 
```
```
<dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>4.0.1</version>
        <scope>provided</scope>
</dependency>
```

<h2>Technologies 🕹️</h2>

1. Java
2. MySQL
3. Amazon Web Services:
    - Amazon Relational Database Service
    - Elastic Beanstalk
4. Java Database Connectivity
5. Web API
6. Tomcat
7. Maven
8. Jsp
9. Jstl


<h2>Project Structure 📂</h2>

**Taxi Service has an N-Tier Architecture**

1) ___Controller layer___ - responsible for communication between client and server, displays .jsp pages.
2) ___DAO layer___ - responsible for CRUD operations on the database.
3) ___Util layer___ - provides a connection to the database.
4) ___Service layer___ - responsible for the business logic of the application.
5) ___Filter layer___ - responsible for filtering requests (client) and responses (server).

<h3><center>Database diagram</center></h3>


<img src="src/main/resources/Screenshot 2023-08-01 230709.png">
