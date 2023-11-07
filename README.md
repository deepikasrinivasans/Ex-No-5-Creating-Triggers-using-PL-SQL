# Ex. No: 5 Creating Triggers using PL/SQL
## Date:

## AIM:
To create a Trigger using PL/SQL.

## Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

## Program:
## Create employee table
```
SQL> create table EmployeeDB(Empno NUMBER,Empname VARCHAR2(10),Dept VARCHAR2(10),Desig VARCHAR2(20),Salary NUMBER);
```
![sql0 1](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/45f1d42a-9bb4-44d6-bf01-7d22c1cdbf3a)

## Create salary_log table
```
SQL> create table Wage(Login_ID NUMBER GENERATED ALWAYS AS IDENTITY,Empno NUMBER,Empname VARCHAR2(10),Old_Salary NUMBER,New_Salary NUMBER,Updated_on DATE);
```
![sqlsalwages](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/983513da-e100-43bb-82c5-991be0594050)
## Inserting data into the employed table:
```
SQL> insert into EmployeeDB values(101,'Deepika','AI-DS','Senior Architect',300000);
SQL> insert into EmployeeDB values(102,'Vasundra','AI-ML','System Engineer',250000);
SQL> insert into EmployeeDB values(103,'Abinaya','CSE','Software Tester',230000);
SQL> insert into EmployeeDB values(104,'Mike','EEE','Electrical Asst',130000);
SQL> insert into EmployeeDB values(105,'Srini','IT','System Admin',110000);
```
![sql0 2](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/07fed900-23d4-45f4-934f-6e6c6886f01b)
## Update the salary of an employed:
```
SQL> update EmployeeDB SET Salary=120000 where Empno=103;
```
![sqlrowupd](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/d16c99b5-62c8-4ebb-8869-2fdfb9382ae1)

## PLSQL Trigger code
```
SQL> CREATE OR REPLACE TRIGGER Salary_Update BEFORE UPDATE ON EmployeeDB FOR EACH ROW BEGIN IF :OLD.Salary != :NEW.Salary THEN INSERT INTO Sal_Wages(Empno, Empname, Old_Salary, New_Salary, Updated_on) VALUES (:OLD.Empno, :OLD.Empname, :OLD.Salary, :NEW.Salary, SYSDATE);
  2  END IF;
  3  END;
  4  /
```
![sql0 3](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/6ae564bb-f550-4938-a937-e1d169cf2999)

## Output:
![sqlemployyee](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/e8b54341-55e2-490b-8a46-bb574d682eb7)
![sql salaryout](https://github.com/deepikasrinivasans/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119393935/1900030f-6202-417b-8c5f-4846b2c95e01)

## Result:
Thus the program for creating triggers has been implemented successfully.
