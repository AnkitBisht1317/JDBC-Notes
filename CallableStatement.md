# Stored Procedures
- In java programming if any code repeatedly requireed, then we can define that code inside a method and we can call that method multiple times based on our requirement.
- Hence method is the best reusuable component in java programming.
- Similarly in the database programming if any group of sql statement is repeatedly required then we can define those sql statement in a single group and we can call that group repeatedly based on our requirement.
- This group of sql statement that perform a particular task is nothing but stroed procedure. Hence stroed procedure is the best reuseable component at database level.
- Hence stroed prodecure is a group of sql statement that perform a particular task.

```SQL
create or replace procedure demo(X IN number, Y IN number, Z IN number) as
BEGIN
Z := X + Y;
END;
/
variable sum number;
execute demo(100,200. :sum);
print sum;
```

# Callable Statement
- If we want to call stored procedure from java application thenwwe should go for callable Statement.
- callableStatement is an interface present in java.sql.package and it is the child interface of preparedStatement.

          CallavleStatement cst = con.prepareCall("{call demo(?,?,?)}");
- where call is a JDBC keyword, demo is the procedure name, ? is a parameters.
