#database

import MySQLdb

#open database connection
db = MySQLdb.connect("localhost","testuser","test123","TESTDB")
cursor = db.cursor()
cursor.execute("DROP TABLE IF EXISTS EMPLOYEE")

#create table as per requirement
sql = """CREATE TABLE EMPLOYEE ( FIRST_NAME CHAR(20) NOT NULL,LAST_NAME CHAR(20),AGE INT,INCOME FLOAT)"""

#sql query to insert a record into database.
sql = """INSER INTO EMPLOYEE(FIRST_NAME,LAST_NAME, AGE, INCOME)
          VALUES ('%s', '%s', '%d', '%d')""" % \
          ('dan', 'bil', 25, 2000)
try:
    #execute the SQL command 
    cursor.execute(sql)
    #commint your changes in the database
    db.commit()
except:
    #rollback in case there is any error
    db.rollback()
