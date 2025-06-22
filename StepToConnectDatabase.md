# STEP TO CONNECT DATABASE 
- There are 6 step to connect database.

### 1. Load And Ragister Driver Class 
- From java application if we want to communicate with database some special software is required which is nothing but driver software we have to make driver software available to our program.
- Every driver software is available in the form of JAR file and hence we have to place this jar file in classpath.
- Type-1 driver is available as the part of JDK and hence we are not requied to set any classpath.
- Every driver software is identified with some special class which is nothing but Driver Class.
  
                      Type-1  sun.jbdc.odbc.JdbcOdbcDriver
                      Type 2	oracle.jdbc.driver.OracleDriver
                      Type 3	com.ddtek.jdbc.openedge.OpenEdgeDriver
                      Type 4	com.mysql.cj.jdbc.Driver, org.postgresql.Driver

- We have to load this driver class.
- Any java class we can load by using Class.forName() method, Hence we load driver class

                              Class.forName(sun.jbdc.odbc.JdbcOdbcDriver)
- But JDBC 4.0 version that is not required JDBC automatically load classpath.
- After load driver class, register driver class automatically.

### 1. Establish Connection Between Java Application and Database
- 
