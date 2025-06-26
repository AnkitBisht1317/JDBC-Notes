# Prepared Statement 
- In the case of normal statement, whenever we are executing SQL Query, every time compilation and execution will be happened at database side.
- Statement object work only static query.

![Image](https://github.com/user-attachments/assets/b22a214c-617c-44d0-817f-dd397203014b)

- sometimes in our application we required to execute same query multiple times with same or different input value.
- Example - In IRCTC application it is common requirement to list out all possible trains between 2 places.
- For the above requirement if we use statement object then the query is required to compile and execute every time which create performance problem.
- To overcome this problem we should go for preparedStatement.
- The main advantage of preparedStatement is the query will be compiled only once even though we are executing multiple times, so that overalll performance of the application will be improved.
- We can create preparedStatement by using prepareStatement(String query) throws SQLException.
- It is work for both static and dynamic query.

![Image](https://github.com/user-attachments/assets/2557a5a0-3794-4cdf-a8c6-272ef34eb0fe)

```
import java.sql.*;
import java.util.Scanner;

public class MultipleInsertExample {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/your_database";
        String user = "root";
        String password = "your_password";

        Scanner sc = new Scanner(System.in);

        try {
            // Load Driver (for older JDBC versions)
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Create Connection
            Connection con = DriverManager.getConnection(url, user, password);

            // SQL insert query with placeholders
            String query = "INSERT INTO student (rollno, name, email) VALUES (?, ?, ?)";

            // Create PreparedStatement
            PreparedStatement pst = con.prepareStatement(query);

            String choice;

            while (true) {
                // Take user input
                System.out.print("Enter Roll No: ");
                int rollno = sc.nextInt();
                sc.nextLine(); // consume newline

                System.out.print("Enter Name: ");
                String name = sc.nextLine();

                System.out.print("Enter Email: ");
                String email = sc.nextLine();

                // Set values in PreparedStatement
                pst.setInt(1, rollno);
                pst.setString(2, name);
                pst.setString(3, email);

                // Execute insert
                pst.executeUpdate();
                System.out.println("Record inserted successfully!");

                // Ask user if they want to insert more
                System.out.print("Do you want to insert another record? (yes/no): ");
                choice = sc.nextLine().toLowerCase();

                if (!choice.equals("yes")) {
                    break;
                }
            }

            // Close connection
            pst.close();
            con.close();
            sc.close();

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
