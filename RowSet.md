# RowSet
- It is alternative to ResultSet.
- We can use RowSet to handle a group of records in more effective way than ResultSet, RowSet interface present interface present in javax.sql.package.
- RowSet is child interface of ResultSet.
- RowSet implementations will be provide by java vender and database vender.
- BY default RowSet is scrollable and updatable.
- By default RowSet is serializable and hence we can send RowSet object across the network, But ResultSet object not serializable.
- ResultSet is connected i.e to use ResultSet compulsary database connection must be required.
- RowSet is disconnrcted i.e to use RowSet database connection is not required.

## Types Of RowSet
- There are two type of RowSet

### 1) Connected RowSet
- Connected RowSets are just like ResultSets.
- To access RowSet data complusary should be available to database.
- we con not serialize connected RowSets.
- Eg - JdbcRowSet

```jdbc
import javax.sql.rowset.JdbcRowSet;
import com.sun.rowset.JdbcRowSetImpl;
import java.sql.SQLException;

public class JdbcRowSetExample {
    public static void main(String[] args) {
        try {
            // Create JdbcRowSet instance
            JdbcRowSet rowSet = new JdbcRowSetImpl();

            // Set database connection details
            rowSet.setUrl("jdbc:mysql://localhost:3306/mydb");
            rowSet.setUsername("root");
            rowSet.setPassword("password");

            // Set SQL query
            rowSet.setCommand("SELECT id, name, email FROM users");
            rowSet.execute();  // Executes the SQL query

            // Iterate over results
            while (rowSet.next()) {
                int id = rowSet.getInt("id");
                String name = rowSet.getString("name");
                String email = rowSet.getString("email");

                System.out.println(id + " | " + name + " | " + email);
            }

            // Close the rowSet
            rowSet.close();

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

### 2) Disconnected RowSet
- Without having Connection to the database we can access RowSet data.
- We can serialize Disconnected RowSets.
- Eg - CachedRowSet, WebRowSet

![Image](https://github.com/user-attachments/assets/cdf8bb3f-9895-4aee-bb5f-8e877a88e304)

```jdbc
import javax.sql.rowset.CachedRowSet;
import com.sun.rowset.CachedRowSetImpl;
import java.sql.SQLException;

public class RowSetExample {
    public static void main(String[] args) {
        try {
            // Create CachedRowSet object
            CachedRowSet rowSet = new CachedRowSetImpl();

            // Set database connection details
            rowSet.setUrl("jdbc:mysql://localhost:3306/mydb");
            rowSet.setUsername("root");
            rowSet.setPassword("password");

            // SQL command to execute
            rowSet.setCommand("SELECT id, name, email FROM users");
            
            // Execute the query (fetches and disconnects)
            rowSet.execute();

            // Iterate and print results (no DB connection needed here)
            while (rowSet.next()) {
                int id = rowSet.getInt("id");
                String name = rowSet.getString("name");
                String email = rowSet.getString("email");

                System.out.println(id + " | " + name + " | " + email);
            }

            // Optional: close the RowSet
            rowSet.close();

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```
