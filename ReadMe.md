# Install MySQL
Go [MySQL](https://www.mysql.com) official website and download the [MySQL Community](https://dev.mysql.com/downloads/) (GPL) version which fit your work system(windows, Linux, etc).

# Before Connect 
Before we use powershell to connect MySQL. We have a problem need to face first.

This problem was happened when I want to load the local data(your dataset) into the database.

I got this error prompt:
  
    ERROR: 3948 (42000): Loading local data is disabled; this must be enabled on both the client and server sides

this is a security feature to prevent the loading of local files into the server unless explicitly permitted.

## how to handdle this problem?
### step 1
open the **my.cnf** or **my.ini** file. It usually in :
    
    C:\ProgramData\MySQL\MySQL Server x.x\  

### step 2
Find or search the key word **[mysql]** and edit the MySQL server configuration to enable local file loading like the following cell:

    [mysqld]
    local-infile=1

### step 3
Open the **PowerShell** and use the folloing command to connect MySQL.Please cd to your mysql.exe location's path.

    ./mysql --local-infile=1 -u username -p
    
# Connect 
You will get the require to enter the password When you connect with the command:**mysql --local-infile=1 -u username -p**.\
Just enter your password and keep going.

# Build Database
## Create Database

      CREATE DATABASE DATABASENAME;
## Select Database

    SELECT DATABASENAME;
## Verify Your Current Database

    SELECT DATABASE();

# Create Table

    CREATE TABLE YOURTABLENAME (
    Column1 VARCHAR(255),
    Column2 INT,
    Column3 FLOAT,
    -- etc.
    );
# Import the Dataset

    LOAD DATA LOCAL INFILE '/path/to/your/dataset.csv'
    INTO TABLE MyDataset
    FIELDS TERMINATED BY ','
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS;  -- If your CSV has a header row

# Check the Data

    SELECT * FROM your_table_name LIMIT 10;

-------keep updateing...-------
