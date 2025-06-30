# Transaction
- A transaction is a group of operations combined into a single unit of work, executed based on the rule: "Either all operations succeed, or none of them take effect."

### Types of Transaction 
- there are 2 type of transaction :-

#### 1. Local Transaction 
- All operation in a transaction are execute over same database.
- Eg - Funds transfer from one account to another where both accounts in the same bank.

#### 2. Global Transaction 
- All operation in a transaction are expected over different database.
- Eg - Funds transfer from one account to another and accounts are related to different.

## Note 
- JDBC can provide support only for local transactions.
- If we want global transaction then we have to g for EJB or spring framework.

### Process of Transaction Management in JDBC 
- By default auto commit mode is enabled, after executing every sql query, the changes will be committed automatically in the database.

                           con.setAutocommit(false);
- If all operation completed then we can commit the transaction by using the following method.

                                 con.commit();
- If any sql query fails then we have to rollback operation which are already completed by using rollback() method

                                 con.rollback();

```java
import java.sql.*;

public class TransactionExample {
    public static void main(String[] args) {
        Connection con = null;
        PreparedStatement ps1 = null;
        PreparedStatement ps2 = null;

        try {
            // Step 1: Register Driver & Get Connection
            Class.forName("com.mysql.cj.jdbc.Driver");
            con = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/testdb", "root", "your_password");

            // Step 2: Disable auto-commit
            con.setAutoCommit(false);

            // Step 3: First operation - Deduct 500 from Account 1
            ps1 = con.prepareStatement("UPDATE accounts SET balance = balance - 500 WHERE id = ?");
            ps1.setInt(1, 1);
            ps1.executeUpdate();

            // Step 4: Second operation - Add 500 to Account 2
            ps2 = con.prepareStatement("UPDATE accounts SET balance = balance + 500 WHERE id = ?");
            ps2.setInt(1, 2);
            ps2.executeUpdate();

            // Step 5: If both succeed, commit the transaction
            con.commit();
            System.out.println("Transaction successful. Amount transferred.");

        } catch (Exception e) {
            try {
                if (con != null) {
                    con.rollback(); // Step 6: Rollback on failure
                    System.out.println("Transaction failed. Rolled back.");
                }
            } catch (SQLException se) {
                se.printStackTrace();
            }
            e.printStackTrace();

        } finally {
            // Step 7: Close resources
            try {
                if (ps1 != null) ps1.close();
                if (ps2 != null) ps2.close();
                if (con != null) con.close();
            } catch (SQLException ex) {
                ex.printStackTrace();
            }
        }
    }
}
```

# Savepoint
- Savepoint is an interface present in java.sql.package.
- Savepoint concept is applicable only in transactions.
- Within a transaction if we want to rollback a particular group of operation based on some condition then we should go for Savepoint.
- We can set Savepoint by using setSavepoint() method of connection interface.

                      Savepoint sp = con.setSavepoint();
- To perform rollback operation for a particular group of operation with repect to Savepoint, we can use rollback() method as follow

                      con.rollback(sp);
- We can release or delete Savepoint by using release Savepoint() method of connection interface.

                      con.releaseSavepoint(sp);

