# JDBC
- JDBC is a technology which can be used to communicatewith databasefrom java appliacation.
  
![Image](https://github.com/user-attachments/assets/fa880c0e-9ae9-49db-85b5-ebe632eb87fb)

- JDBC is part of java standard edition(J2SE/JSE).
- JDBC is a specification(guidelines) defined by java vender.
- Database vender provided implementation is called driver software.

### Feature 
- JDBC is a standard API we can communicate with any database without rewriting our application means it is database independent API.
- Most of JDBC drives are developed in java and hence JDBC concept can work for any platform( it is platform independent).
- By using JDBC API we can perform basic CRURD opration easily.

## JDBC vs ODBC
- ODBC is open database connectivity, and JDBC is for java database connectivity.
- Introduced by Microsoft, JDBC introduced by SUN micerosystem.
- We can use ODBC for any Language like C, C++, Java etc. but we can use JDBC only for java language.
- We can use ODBC for only windows platform and we can use JDBC for any platform.
- Mostly ODBC drivers are delevped in native language C, C++. But JDBC are developed in java.
- Most java application is not recommended to use ODBC because performence will be down . JBDC is highly recommended to use because it is platform independent.

## JDBC API 
- JDBC API provide sevreal classes and interface
- Program an use these classes and interface comunicate with databse
- Driver software vender can use JDBC API while developing driver software
- Java.sql.package contain basic  classes and interface which can used for databse communication
- javax.sql.package contaon more advanced classes and interface which be used for databse comunication 
