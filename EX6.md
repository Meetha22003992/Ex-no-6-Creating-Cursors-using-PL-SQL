# Ex. No: 5 Creating Cursors using PL/SQL

## DATE: 8.09.2023

### AIM: To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
### Create employee table

CREATE TABLE employee (empid INT,empname VARCHAR(10),dept VARCHAR(10),salary DECIMAL(10, 2));


### PLSQL Cursor code
```
DELIMITER //
CREATE PROCEDURE display_employee_records()
BEGIN
    DECLARE done INT DEFAULT FALSE;
    DECLARE emp_id INT;
    DECLARE emp_name VARCHAR(10);
    DECLARE emp_dept VARCHAR(10);
    DECLARE emp_salary DECIMAL(10, 2);

    DECLARE cur CURSOR FOR
        SELECT empid, empname, dept, salary FROM employee;
    
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

    OPEN cur;

    read_loop: LOOP
        FETCH cur INTO emp_id, emp_name, emp_dept, emp_salary;
        IF done THEN
            LEAVE read_loop;
        END IF;
        
        -- Display the result
        SELECT emp_id, emp_name, emp_dept, emp_salary;
    END LOOP;

    CLOSE cur;
END //
DELIMITER ;

CALL display_employee_records();
```

### Output:
![image](https://github.com/Meetha22003992/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/119401038/713b6a82-51a8-4ad4-8b73-f0e09043acf6)

![image](https://github.com/Meetha22003992/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/119401038/9c5520db-13d7-466b-99cc-b2291f01595d)

### Result:
Thus the cursor code created successfully.
