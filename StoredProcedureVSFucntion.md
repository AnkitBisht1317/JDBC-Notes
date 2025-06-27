# Stored Procedure VS Function
- Function are exactly same as procedures except thaat function has retuen statement directly.
- Procedure can also retuen values indirectly in the from of OUT parameter.
- Usually we can use procedure to define business logic and we can use fumction to perform some calculations like getAverage(), getMax(), etc.
```SQL
DELIMITER //

CREATE OR REPLACE FUNCTION GetSquare(num INT) RETURNS INT as
DETERMINISTIC
BEGIN
    RETURN num * num;
END //

DELIMITER ;
```
- We call this funtion into JDBC by the help of CallableStatement().
