# conn
### 1. Install MySQL Connector for Python
MySQL Connector is the official MySQL driver for Python. You can install it using pip inside VS Code's terminal.

Open the VS Code terminal by pressing Ctrl + ~.
Run the following command to install the MySQL Connector:
```
pip install mysql-connector-python
```
### 2. Create a Python Script to Connect to MySQL
After installing the MySQL connector, you can create a Python script that connects to your MySQL database.Make sure to create a databse first

Create a new Python file, e.g., mysql_connection.py.

```
import mysql.connector 
def MYSQLconnectionCheck ():
    global conn
    global userName
    global password
    userName = input("enter mysql server's username:")
    password = input("enter password:")
    conn = mysql.connector.connect(host="localhost",passwd=password,user=userName,auth_plugin="mysql_native_password")
    if conn:
        #print("congratulations!")
        a=conn.cursor()
        q=("create database if not exists test;")
        a.execute(q)
        a.execute("commit")
        a.close()
        return conn
    else:
        print("so sad")

# Replace the following details with your MySQL database information
def mysqlconnection():
    global conn
    global userName
    global password
    conn = mysql.connector.connect(host="localhost",user=userName,passwd=password,database="test",auth_plugin="mysql_native_password" )
    if conn:
        print("Connected to MySQL database ")
        return conn
    else:
        print("Connection failed")
        conn.close()
conn=MYSQLconnectionCheck()
if conn:
    mysqlconnection()
    if(True):
        print("Connection is successfull")
        
else:
    print("Unable to connect Python with MySQL")
```
### 3. Open the Terminal of that current file script only
   * Navigate to the current directory
   * Go to the directory where you have saved the file ((mysql_connection.py) here)
   * Run the following command
```
python mysql_connection.py
```


