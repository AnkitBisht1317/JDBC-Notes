# STEP TO CONNECT DATABASE 
- There are 6 step to connect database.

### 1. Load And Ragister Driver Class 
- From java application if we want to communicate with database some special software is required which is nothing but driver software we have to make driver software available to our program.
- Every driver software is available in the form of JAR file and hence we have to place this jar file in classpath.
- Type-1 driver is available as the part of JDK and hence we are not requied to set any classpath.
- Every driver software is identified with some special class which is nothing but Driver Class.
  
                      Type-1 driver class name is sun.jbdc.odbc.JdbcOdbcDriver

- We have to load this driver class.
- Any java class we can load by using Class.forName() method, Hence we load driver class

                              Class.forName(sun.jbdc.odbc.JdbcOdbcDriver)
