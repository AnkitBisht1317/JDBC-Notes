# Handle Date Value For Database Operation
- Sometimes as the part od progeaming requirement, we have to insert and retrieve Date like DOB,DOJ,DOM,DOP...
- It is not recommended to maintain data value in the form of string
- in java we have two Date classes
  - java.util.Date
  - java.sql.Date

- java.util.Date can represent both Date and TIme where as java.sql.Date represent only Date but not Time.

```
import java.sql.*;
import java.text.SimpleDateFormat;
import java.util.Scanner;

public class DateInsertRetrieve {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/testdb";
        String user = "root";
        String pass = "password";

        try (
            Scanner sc = new Scanner(System.in);
            Connection con = DriverManager.getConnection(url, user, pass)
        ) {
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Input from user
            System.out.print("Enter name: ");
            String name = sc.nextLine();

            System.out.print("Enter DOB (yyyy-MM-dd): ");
            String dobStr = sc.nextLine();

            // Parse String to java.util.Date
            java.util.Date utilDate = new SimpleDateFormat("yyyy-MM-dd").parse(dobStr);

            // Convert to java.sql.Date
            java.sql.Date sqlDate = new java.sql.Date(utilDate.getTime());

            // Insert into DB
            String insertSQL = "INSERT INTO student (name, dob) VALUES (?, ?)";
            PreparedStatement ps = con.prepareStatement(insertSQL);
            ps.setString(1, name);
            ps.setDate(2, sqlDate);
            ps.executeUpdate();
            System.out.println("Record inserted.");

            // Retrieve from DB
            String query = "SELECT name, dob FROM student";
            ResultSet rs = con.createStatement().executeQuery(query);
            System.out.println("\nStudent List:");
            while (rs.next()) {
                System.out.println(rs.getString("name") + " - " + rs.getDate("dob"));
            }

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
