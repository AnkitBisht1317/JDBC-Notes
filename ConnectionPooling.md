# Connection Pooling
- If we required to communicate with database multiple times then it is not recommended to create separate Connection object every time, because creating and destroying Connection object every time creates performance problem.
- To overcome this problem we should go for connection pool.
- Connection pool is a pool of already created Connection object which are ready to use.
- If we want to communicate with database then we request Connection pool to provide Connection. once we got the coonection by using that we can communicate with database. After completing our work we can return Connection to the pool instead of destroying.
- Hence the main advantage of Connection Pool is we can reuse same Connection object multiple times, so that overall performance of application will be improved.

### Process To Implement Connection Pooling
##### 1). Creation of DataSource Object
- DataSource is responsible to manage connection in Connection Pool.
- DataSource is an interface present in javax.sql.package.
- Oracle people provide implementation class name is

      OracleConnectionPoolDataSource ds =  new OracleConnectionPoolDataSource()
  
##### 2). Set Required JDBC Properties to the DataSource Object
- ds.setURL("jdbc:oracal:thin:@localhost:1521:XE);
- ds.setUser("ankit")
- ds.setPassword("root")

##### 3). Get Connection From DataSource Object
- Connection con = ds.getConnection();
- once we got Connection object then remaining process is as usual.

```sql
import java.sql.*;
import javax.sql.*;
import oracle.jdbc.pool.OracleConnectionPoolDataSource;

public class ConnectionPoolingDemo {
    public static void main(String[] args) {
        Connection con = null;

        try {
            // Step 1: Create DataSource Object
            OracleConnectionPoolDataSource ds = new OracleConnectionPoolDataSource();

            // Step 2: Set required JDBC properties
            ds.setURL("jdbc:oracle:thin:@localhost:1521:XE");
            ds.setUser("ankit");
            ds.setPassword("root");

            // Step 3: Get Connection from DataSource
            con = ds.getConnection();

            // Step 4: Use Connection
            Statement st = con.createStatement();
            ResultSet rs = st.executeQuery("SELECT * FROM person");

            while (rs.next()) {
                System.out.println("Name: " + rs.getString("name"));
            }

            // Step 5: Return connection to pool (close)
            con.close(); // Actually returns it to pool, not destroys

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
