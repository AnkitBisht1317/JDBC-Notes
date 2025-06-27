# CURSORS
- The results of SQL Queries will be stored in special memory area inside database software. This memory area is called context Area.
- To access Result of this context Area, some pointer are required and these pointer are nothing but cursors.
- Hence the main objective of cursor is to access result of SQL Queries.
- There are 2 type of cursors

### 1) Implicit Cursor
- These cursors will be created automatically by database software to hold result whwnever a particular type of sql query got executed.

### 2) Explicit Cursor 
- These cursors will be created explicitly by the deve;oper to hold result of particular sql queries.

- Eg - SYS_REFCURSOR can be used to access result of select query to access ResultSet.
- Eg - %ROWCOUNT is an implict cursor provided by ORACLE to represent the number of rows effected.
- Eg - %FOUND is an implict cursor provided by ORACLE to represent the number of rows effected.
