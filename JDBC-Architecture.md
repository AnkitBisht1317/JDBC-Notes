JDBC ARCHITECTURE 
- JDBC API provide drivermanager to java application.
- Java application can communicate with any database with the help of driver manager and database specific driver software.

### Driver Manager
- It is the key component in  JDBC Architeture.
- It is a class present in java.sql.package.
- it is respossible to manage all database driver.
- It is reponssible to register and unregister database driver.
                           DriverManager.registerDriver(driver)
                           DriverManager.unregisterDriver(driver)
- It is responssible to establish connection to the database with the help of driver software.
      Connection con = DriverManager.getConnection(JDBCUrl,username,pwd)

### DataBase Driver
- It is very improtant component of JDBC Architecture.
- without driver software we con not touch databse.
- It acts as bridge between java application and database.
- It responssible to connect java call it's data sepecific call and vice vrsa.


![Image](https://github.com/user-attachments/assets/b6c5838d-9121-4beb-8b65-954eba5a8acf)
