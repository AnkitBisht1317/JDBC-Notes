# Prepared Statement 
- In the case of normal statement, whenever we are executing SQL Query, every time compilation and execution will be happened at database side.

![Image](https://github.com/user-attachments/assets/b22a214c-617c-44d0-817f-dd397203014b)

- sometimes in our application we required to execute same query multiple times with same or different input value.
- Example - In IRCTC application it is common requirement to list out all possible trains between 2 places.
- For the above requirement if we use statement object then the query is required to compile and execute every time which create performance problem.
- To overcome this problem we should go for preparedStatement.
- The main advantage of preparedStatement is the query will be compiled only once even though we are executing multiple times, so that overalll performance of the application will be improved.
- We can create preparedStatement by using prepareStatement(String query) throws SQLException.

![Image](https://github.com/user-attachments/assets/2557a5a0-3794-4cdf-a8c6-272ef34eb0fe)
