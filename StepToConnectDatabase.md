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

### 2. Establish Connection Between Java Application and Database
- The getConnection() method of DriverManager class is used to establish connection with the database.

       Connection con = DriverMnager.getConnection(jdkurl,username,password);
- JDK URL have 3 part - main protocol(which is always JDBC) : subProtocol(which is depend on database : subname(Hostname, port, database name))

      Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/studentdb","root", 1317);

### 3. Creation of Statement Object
- We use createStatement() method, which is used to send and execute SQL queries to the database.
- createStatement() create a Statement object.

                           Statement stmt = con.createStatement();

 ### 4. Perpare, Send & Execute SQL Query
 - There are 3 method we execute SQL query in JDBC

##### i) executeQuery() 
 - If we know the tyoe of query at the begining and it is always select query then we should go for executeQuery() method.
 - Return type in this query always ResultSet.
```
ResultSet rs = stmt.executeQuery("SELECT * FROM students");
while (rs.next()) {
    System.out.println(rs.getInt("id") + " " + rs.getString("name"));
}
```

##### ii) executeUpdate() 
- If we know the tyoe of query at the begining and it is always non-select query then we should go for executeUpdate() method.
-  Return type in this query always int.
```
int rows = stmt.executeUpdate("INSERT INTO students (id, name) VALUES (3, 'Ankit')");
System.out.println("Rows inserted: " + rows);
```

##### ii) execute() 
- If we do not know the type of query at the beginning and it is available dynamically at runtime(may be from properties file or form command propmt) then we should go for execute() method.
- Return type in this query always boolean . if it return ture then it is select query otherwise non-select query.
```
boolean isResultSet = stmt.execute("SELECT * FROM students");

if (isResultSet) {
    ResultSet rs = stmt.getResultSet();
    while (rs.next()) {
        System.out.println(rs.getInt("id") + " " + rs.getString("name"));
    }
} else {
    int count = stmt.getUpdateCount();
    System.out.println("Rows affected: " + count);
}
```

```
By mistake if we provide select query to non-select statement then the result depends on driver to driver.
```

 ### 5. Process Result From ResultSet
 - Result follows Iterater design pattern
 - RsultSet object is always assoiatted with statement object
 - per statement only one ResultSet is possible at a time if we are trying to open another ResultSet then automatically first ResultSet will be closed.
```
 Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/testdb", "root", "password");

            // 2. Create Statement
            Statement stmt = con.createStatement();

            // 3. Execute Query (returns ResultSet)
            ResultSet rs = stmt.executeQuery("SELECT id, name FROM students");

            // 4. Process ResultSet using Iterator-style (next())
            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                System.out.println("ID: " + id + ", Name: " + name);
            }
```

 ### 6. Close the Connection
 - By closing connection object, statement and ResultSet will be closed automatically. The close() method of Connection interface is used to close the connection.

```
import java.sql.*;

public class JdbcFullExample {
    public static void main(String[] args) {
        Connection con = null;
        Statement stmt = null;
        ResultSet rs = null;

        try {
            // Step 1: Load and Register Driver Class (optional from JDBC 4.0)
            Class.forName("com.mysql.cj.jdbc.Driver"); // MySQL Type 4 Driver

            // Step 2: Establish Connection
            con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/testdb", "root", "password");

            // Step 3: Create Statement
            stmt = con.createStatement();

            // Step 4: Execute SQL Query
            rs = stmt.executeQuery("SELECT id, name FROM students");

            // Step 5: Process ResultSet
            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                System.out.println("ID: " + id + ", Name: " + name);
            }

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 6: Close Resources
            try {
                if (rs != null) rs.close();
                if (stmt != null) stmt.close();
                if (con != null) con.close(); // Closing connection will close stmt and rs too
                System.out.println("Connection closed successfully.");
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```
