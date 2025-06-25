# Life Cycle Of SQL Query Execution
- From java application if we submit SQL Query by using statement object execute method.
- Then Database engine will perform the following sequence of activities.

### 1. Compilation 
- As the part of compilation, Odatabase engine will perform the following activities.

#### a) Query Tokenization 
- In this step total SQL query will be divided into number of tokens and generate a steram of tokens as output.

#### b) Query Parsing
- In this step database engine will create parse tree with stream with stream of tokens. if the query tree is proper then there are no syntactical mistake in that query.

#### c) Query Optimization 
- The main purpose of query optimization is to improve performance. in this step otimized query tree will be constructed.

### 2. Execution Of SQL Query
- once compilation success then database engine will take that query tree as input and excute that query by using interpreter.

### 3. Fetch The Result
- Database engine will provide result of SQL query either in the form of resultset or in the form of rowCount to the java apllication.

![Image](https://github.com/user-attachments/assets/5be0aa69-3406-4865-99a5-2b2fb8f9cae2)
