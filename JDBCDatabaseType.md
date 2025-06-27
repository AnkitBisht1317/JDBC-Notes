# JDBC Bridge Type
- Java related data type and database related data types are not same. Some mechanism must be required to convert java types to database type and database types to java typees. This mechanism is nothing but "JDBC Types" which are also known as "Bridge Types".
- We use a method to convert JDBC type into database related type -

       cst.ragisterOutParameter(index, Type name(INTEGER));
