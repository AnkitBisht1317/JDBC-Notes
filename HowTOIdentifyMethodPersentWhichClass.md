# How To Identify Method Persent Which Class

##### Class.forName(driverClassName)
- Class class contain static method forName()

##### Connection con = DriverManager.getConnection(url,user,pwd)
- DriverManager class contain static method getConnection()

##### Statement st = con.createStatement() 
- Connection interface contain instance method createStatement()

##### ResultSet rs = st.executeQuery(selectquery)
- Statement interface contain instance method executeQuery()

##### rs.next(), rs.getInt(), rs.String()
- ResultSet interface contain instance method rs.next(), rs.getInt(), rs.String()

##### con.close()
- Connection interface contain instance method close()
