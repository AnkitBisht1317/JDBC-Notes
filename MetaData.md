# Meta Data
- Meta data means data about data. i.e Metadata provides extra infromation about our original data.
- Eg - Metadata about database is nothing but database product name, database version etc.
- Meta data about ResultSet menas no. of columns, each column name, column type etc.
- JDBC provide three type of metadata

### 1) DatabaseMetadata
- It is a interface present in java sql package
- Driver software vender is responsible to provide implementation
- We can use DatabaseMetaData to get information about our database like database product name, driver name, versions, number of tables etc.
- We can get DatabaseMetaData object by using getMetaData() method of connection interface.

                       DatabaseMetaData dbmd = con.getMetaData();
- Once we got DatabaseMetaData object we can call several methods on that object like.

                       dbmd.getDatabaseProdectName();
                       dbmd.getDatabaseProdectVersion();
                       dbmd.getMaxColumsInTable();
                       dbmd.supportsStroedProcedures();
  
### 2) ResultSetMetadata
- It is an interface present in java.sql.package.
- Driver software vender is responsible to provide implementation.
- It provide information about database table repersented by ResultSet object.
- Useful to get number of columns, Column types etc
- We can get ResultSetMetaData object by using getMetaData() method of resultSet interface.

                     ResultSetMetaData esmd = rs.getMetaData();
- Once we got ResultSetMetaData object we can call the following method on that object like

                       esmd.getColumsCount();
                       esmd.getColumnName();
                       esmd.getColumnType();
  
### 3) ParameterMetadata
- It is an interface and present in java.sql.package.
- Driver software vender is responsible to provide implementation.
- In general we can use positional parameters(?) while creating PreparedStatement object.
- we can use ParameterMetaData to get infromation about positional parameter

                    ParameterMetaData pmd = pst.getParameterMetaData();
- Once we got ParameterMetaData object we can call the following method on that object like

                       pmd.getParameterCount();
                       pmd.getParameterMode();
                       pmd.getParameterType();
                     
