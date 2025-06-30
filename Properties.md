# Properties 
- If java program is anything which changes frequently (like jdcc url, username, pwd) is not recommended to hard code in our program.
- The problem in this approch is if there is any change in java program, to reflect that change we have to recompile, rebuild and redeploy total application and even some times server restart also required, which create a big impact to the client.
- To overcome this problem. we sholud go for properties file. The variable things we have to configure properties file and we have to read these properties from java program.
- The main advantage of this approach is if there is any change in properties file and to reflect that change just redeployment is enough, which won't create ny bussiness impact to the client.

### config.properties
```sql
# config.properties
db.url=jdbc:mysql://localhost:3306/mydb
db.username=root
db.password=admin123
```
### DBconfigReader.java
```java
import java.io.FileInputStream;
import java.io.IOException;
import java.util.Properties;

public class DBConfigReader {

    public static void main(String[] args) {
        Properties props = new Properties();
        try {
            // Load the properties file
            FileInputStream fis = new FileInputStream("config.properties");
            props.load(fis);

            // Read properties
            String url = props.getProperty("db.url");
            String username = props.getProperty("db.username");
            String password = props.getProperty("db.password");

            // Print values
            System.out.println("Database URL     : " + url);
            System.out.println("Database Username: " + username);
            System.out.println("Database Password: " + password);

        } catch (IOException e) {
            System.out.println("Error reading properties file: " + e.getMessage());
        }
    }
}
```
