## MySQL

Our application utilizes MySQL as one of the primary database management systems. MySQL is an open-source relational database that provides a robust and scalable solution for storing and retrieving data.

### MySQL Workbench

For database design, management, and administration, we rely on MySQL Workbench. This powerful tool offers a visual representation of our database schema, making it easier to design and modify the structure of our data.

![image](https://github.com/jrykns-org/not-a-virus-map/assets/91504148/522beef3-2248-4e42-8f0f-50dc9d6f3d4c)

![image](https://github.com/jrykns-org/not-a-virus-map/assets/91504148/b2b9eedd-6d11-47e2-952a-3e6086f0ce65)

## Azure SQL Server

In addition to MySQL, we leverage Azure SQL Server for cloud-based data storage. Azure SQL Server provides a scalable and secure environment for our application, allowing us to store and retrieve data with high performance and reliability.

### Blob Storage for Images

To handle image storage efficiently, we make use of the Blob data type. Blobs (Binary Large Objects) allow us to store and retrieve large binary data, such as images, seamlessly. This is particularly useful for enhancing the visual elements of our application.

![image](https://github.com/jrykns-org/not-a-virus-map/assets/91504148/889461f1-ef24-48c7-a222-300d579eb627)

## Spring Boot App Connection

Our Spring Boot application is tightly integrated with the MySQL and Azure SQL Server databases. The application establishes a secure and efficient connection to these databases, allowing seamless communication for data retrieval and storage.

### Connecting to MySQL

To connect our Spring Boot application to the MySQL database, we configure the necessary properties in the `application.properties` file. This includes specifying the database URL, username, and password.

```
spring.datasource.url= jdbc:mysql://devops.mysql.database.azure.com/db
spring.datasource.username=hamza
spring.datasource.password=
spring.datasource.driver-class-name= com.mysql.jdbc.Driver
```
