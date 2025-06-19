# JDBC SOFTWARE(DRIVER)
- Programmer are not responsible to provide implementation for JDBC API interface.
- Most of the time database vender is responsible to provide the implementation as the part of driver software
- Evrey driver software is a collection of classes implementing various interface of JDBC API, which can be use to communicate with particular databse.
- for example driver software for oracle means collection of implementation classes of JDBC API, which can be used to communicate with oracle databse.
- It Is the collection of implementation classes of various interface present in JDBC API.
- It Is responsible to convert java call to database specific call and vice vrsa.
- Every driver software  is identified with a special class which is nothing but Driver Class.
- Usually driver software are available in the form of JAR file

## TYPE OF JDBC DRIVER  
- While communicating with database we have to convert java calls into database specific calls and vica vrsa.
- In the market thousands of driver are available but based on functionlity and architecture all driver are divied into four part

### TYPE-1 DRIVER(JDBC-ODBC BRIDGE DDRIVER) 
- Type-1 driver convert JDBC call into ODBC call and ODBC driver convert ODBC call into database specific calls.
- Hence type-1 driver act as bridge between JDBC and ODBC.


  ![Image](https://github.com/user-attachments/assets/b1b02e79-8496-4443-a52e-4a619bd6f7ee)

#### Advantage 
- It is very esay to use and maintane
- Type-1 driver won't communicate databse directly hence it is database independent driver because of this migrating from one database to another databse will become esay

#### Disadvantage 
- It is slower driver amonng all driver because first it is convert JDBC to ODBC then ODBC to database specific calls.
- this driver internally dependent on ODBC driver which will work only on window hence it is platform dependent driver
