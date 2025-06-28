# Batch Update
- Whe we submit multiple SQL queries to the database one by one then lot of time will be wasted in request and reponse.
- To overcome this problem, we should go for batch update, we can group all related SQL Queries into a single batch and we can send that batch at a time to the database.
- Henece the main advantage of batch update are
    - We can reduce network traffic.
    - we can improve performence.
  
![Image](https://github.com/user-attachments/assets/df8cd7d2-d758-4d1b-b1c1-65805d6f4da6)

#### Steps to Perform Batch Update
- Load and register JDBC driver
- Create connection using DriverManager
- Create a PreparedStatement
- Set parameter values for each iteration
- Add the statement to the batch using addBatch()
- Execute the batch using executeBatch()
- Close connection

```sql
import java.sql.*;

public class BatchInsertExample {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/testdb";
        String user = "root";
        String pass = "password";

        try {
            // Load JDBC driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Create connection
            Connection con = DriverManager.getConnection(url, user, pass);

            // Disable auto-commit
            con.setAutoCommit(false);

            // Prepare SQL
            String sql = "INSERT INTO students (name, age) VALUES (?, ?)";
            PreparedStatement pstmt = con.prepareStatement(sql);

            // First record
            pstmt.setString(1, "Amit");
            pstmt.setInt(2, 22);
            pstmt.addBatch();

            // Second record
            pstmt.setString(1, "Ravi");
            pstmt.setInt(2, 23);
            pstmt.addBatch();

            // Third record
            pstmt.setString(1, "Neha");
            pstmt.setInt(2, 21);
            pstmt.addBatch();

            // Execute batch
            int[] result = pstmt.executeBatch();

            // Commit changes
            con.commit();

            System.out.println("Records inserted: " + result.length);
            
            // Close resources
            pstmt.close();
            con.close();

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### NOTE - 
- Select query not execute by the help of batch update.
