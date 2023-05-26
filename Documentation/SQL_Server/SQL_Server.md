[Back](../Documentation.md)

# SQL_Server

## Microsoft SQL Server Management Studio

Command to execute previous commands `GO`

Create Database:

```sql
CREATE DATABASE database_name
```

Select Database:

```sql
USE database_name
```

- **Value manipulation**
    - **Selects**
        - Base Select
            
            ```sql
            -- Select base with WHERE condition
            	SELECT column1, column2, ...
            	FROM table_name
            	WHERE condition;
            ```
            
        - Distinct
            
            ```sql
            -- Select distinct values
            	SELECT DISTINCT column1
            	FROM table_name;
            ```
            
        - Alias
            
            ```sql
            -- Select with alias
            	SELECT column_name AS alias_name
            	FROM table_name;
            ```
            
        - Order by
            
            ```sql
            -- Order By
            	SELECT column1, column2, ...
            	FROM table_name
            	ORDER BY column1 ASC, column2 DESC, ... ASC|DESC;
            ```
            
        - Group by
            
            ```sql
            SELECT column1, COUNT(*)
            	FROM table_name
            	GROUP BY column1
            ```
            
        - EXAMPLE:
            
            ```sql
            SELECT Projecto.designacao, COUNT(*)
            	FROM Projecto, Atribuicao
            	WHERE Projecto.proj_num = Atribuicao.proj_num
            	GROUP BY Projecto.designacao
            ```
            
    - **Inserts**
        
        ```sql
        INSERT INTO table_name (column1, column2, column3, ...)
        VALUES 
        	(value1, value2, value3, ...), 
        	(value1, value2, value3, ...);
        ```
        
    - **Updates**
        
        ```sql
        UPDATE table_name
        	SET column1 = value1, column2 = value2, ...
        	WHERE condition;
        ```
        
    - **Deletes**
        
        ```sql
        DELETE FROM table_name 
        WHERE condition;
        ```
        
    - **Functions**
        
        ```sql
        MIN(column_name) --smallest value of the selected column
        MAX(column_name) --largest value of the selected column
        COUNT(column_name) --returns the number of rows that matches a specified criterion
        AVG(column_name) --returns the average value of a numeric column
        SUM(column_name) --returns the total sum of a numeric column
        
        ANY(Query) --returns true if any of the subquery values meet the condition.
        
        GETDATE() --returns current date
        ```
        
    - **Operators → *WHERES***
        
        Operators are used in a `WHERE`
        
        > You can always use the `NOT` key word to negate
        > 
        - **Like**
            
            ```sql
            SELECT column1, column2, ...
            FROM table_name
            WHERE columnN LIKE pattern;
            
            -- In the “pattern” you can use '%' or '_' to build the pattern
            -- % is the 0 or more wildcard
            -- _ is the 1 wildcard
            -- []	Represents any single character within the brackets	ex:h[oa]t
            -- ^	Represents any character not in the brackets ex:h[^oa]t
            -- -	Represents any single character within the specified range ex:c[a-b]t
            
            WHERE Column LIKE 'a_%’
            ```
            
        - **IN**
            
            ```sql
            -- checks if the value in the column is IN the 'array'
            WHERE column IN (value1, value2, value3)
            ```
            
        - BETWEEN
            
            ```sql
            -- selects values within a given range
            WHERE column_name BETWEEN value1 AND value2;
            ```
            
        - **AND**
            
            ```sql
            WHERE condition1 AND condition2 AND condition3 ...;
            ```
            
        - **OR**
            
            ```sql
            WHERE condition1 OR condition2 OR condition3 ...;
            ```
            
        - **IS NULL**
            
            ```sql
            WHERE column1 IS NULL
            ```
            
- **Table manipulation**
    - **Create**
        - **Create a table**
            
            ```sql
            CREATE TABLE table1(
            	-- Columns go here
            )
            ```
            
        - **Columns**
            
            ```sql
            -- AutoIncrement integer
            id INT IDENTITY(1, 1) 
            
            -- variable size string / obligatory field
            word1 VARCHAR(50) NOT NULL   
            
            -- constant size string / optional field
            word2 CHAR(10)
            
            -- integer / optional field
            number1 INT
            ```
            
        - **Keys**
            
            ```sql
            -- AutoIncrement integer primary key
            id INT PRIMARY KEY IDENTITY(1, 1) 
            
            -- Composite primary Key
            PRIMARY KEY(ref1, ref2)
            ```
            
        - **Constraints**
            
            ```sql
            CONSTRAINT constraint_name
            	FOREIGN KEY (column1)
            	REFERENCES table1(column2)
            /*
            NOT NULL - Ensures that a column cannot have a NULL value
            UNIQUE - Ensures that all values in a column are different
            PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
            FOREIGN KEY - Prevents actions that would destroy links between tables
            CHECK - Ensures that the values in a column satisfies a specific condition
            DEFAULT - Sets a default value for a column if no value is specified
            CREATE INDEX - Used to create and retrieve data from the database very quickly
            */
            ```
            
        - EXAMPLE:
            
            Atribuicao (***proj_num***, ***emp_num***, funcao)
            
            ```sql
            CREATE TABLE Atribuicao(
            	proj_num INT NOT NULL,
            	emp_num INT NOT NULL,
            	funcao VARCHAR(50),
            	CONSTRAINT fk_proj_num
            		FOREIGN KEY (proj_num)
            		REFERENCES Projecto(proj_num),
            	CONSTRAINT fk_emp_num
            		FOREIGN KEY (emp_num)
            		REFERENCES Empregado(emp_num),
            	PRIMARY KEY(proj_num, emp_num)
            )
            ```
            
    - **Alter**
        
        ```sql
        ALTER TABLE table_name
        ADD column_name datatype; --this line can be changed
        ```
        
        - Add column
            
            ```sql
            ADD column_name datatype;
            ```
            
        - Delete column
            
            ```sql
            DROP COLUMN column_name;
            ```
            
        - Rename
            
            ```sql
            RENAME COLUMN old_name to new_name;
            ```
            
        - Alter data type
            
            ```sql
            ALTER COLUMN column_name datatype;
            ```
            
        - EXAMPLE:
            
            ```sql
            ALTER TABLE Atribuicao
            	ALTER COLUMN funcao VARCHAR(50) NOT NULL
            GO
            ```
            
    - **Drop**
        
        Deletes table
        
        ```sql
        DROP TABLE table_name;
        ```
        
- Joins

---