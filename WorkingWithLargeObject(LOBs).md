# Working With Large Object
- Sometimes as the part of programming requirement, we have to insert and retrive large files like images, viedo files, audio files, resume etc.
- Eg - Upload images in matrinomial web sites, upload resume in job related web site.
- To store and retrive large information we should go for large object(LOBs).
- There are 2 types of Large object

## 1. Binary Large Object(BLOB)
- A BLOB is a collection of binary data stored as a single entity in the database.
- BLOB type object can be images, viedo files, audio files etc.
- BLOB datatype can store maximum of "4GB" binary data.

### Step to insert BLOB tpye into database
- Create a table in the database which can accept BLOB type data.(create table person (name varchar(10), image BLOB);
- Represent image file in the form of java file object ( File f = new File(ankit.jpg));
- Create FileInputStream to read binary data represented by image file (FileInputStream fis = new FileInputSteam(f));
- Create preparedStatement with insert query (PrepraedStatement pst = con.prepareStatement("insert into person value(?,?));
- Set values to positional parametere 

            pst.setString(1,ankit);
            pst.setBinaryStream(2.fis);
- Execute query(pst.executeUpdate());

```sql
import java.sql.*;
import java.io.*;

public class InsertImage {
    public static void main(String[] args) {
        try {
            // Step 1: Connect to DB
            Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/dbname", "root", "password");

            // Step 2: Represent image file
            File f = new File("ankit.jpg");

            // Step 3: Read binary data
            FileInputStream fis = new FileInputStream(f);

            // Step 4: Create PreparedStatement
            PreparedStatement pst = con.prepareStatement("INSERT INTO person VALUES (?, ?)");

            // Step 5: Set parameter values
            pst.setString(1, "ankit");
            pst.setBinaryStream(2, fis, (int) f.length());

            // Step 6: Execute update
            int result = pst.executeUpdate();
            System.out.println("Rows inserted: " + result);

            // Close resources
            fis.close();
            pst.close();
            con.close();

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## 2. Character Large Object(CLOB)
- A CLOB is a collection of character data stored as a single entity in the database.
- CLOB can be used to store large text document(may be plain text or xml documents).
- CLOB Type can store maximum of 4GB data.

### Step to insert BLOB tpye into database
- Create a table in the database which can accept BLOB type data.(create table person (name varchar(10), image BLOB);
- Represent image file in the form of java file object ( File f = new File(ankit.jpg));
- Create FileReader to read binary data represented by image file (FileReader fr = new FileRedaer(f));
- Create preparedStatement with insert query (PrepraedStatement pst = con.prepareStatement("insert into person value(?,?));
- Set values to positional parametere 

            pst.setString(1,ankit);
            pst.setCharacterStream(2.fis);
- Execute query(pst.executeUpdate());

```sql
import java.sql.*;
import java.io.*;

public class InsertClob {
    public static void main(String[] args) {
        try {
            // Step 1: Establish DB Connection
            Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/dbname", "root", "password");

            // Step 2: Represent text file
            File f = new File("ankit.txt");

            // Step 3: Read character data from file
            FileReader fr = new FileReader(f);

            // Step 4: Prepare insert statement
            PreparedStatement pst = con.prepareStatement("INSERT INTO person VALUES (?, ?)");

            // Step 5: Set values to parameters
            pst.setString(1, "ankit");
            pst.setCharacterStream(2, fr, (int) f.length());

            // Step 6: Execute query
            int result = pst.executeUpdate();
            System.out.println("Rows inserted: " + result);

            // Close resources
            fr.close();
            pst.close();
            con.close();

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
