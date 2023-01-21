
import logging as lg

lg.basicConfig(filename = "Logger.log",level = lg.DEBUG,filemode = 'w', format = "%(asctime)s %(levelname)s %(message)s")

class ListSearch:
    def __init__(self,data):
        self.data = data
    def search(self,value):
        try:
            lg.info("Searching..")
            for i in range(len(self.data)):
                if(self.data[i] == value):
                    lg.info("Succesful search")
                    return i , True
            lg.info("Unsuccesful Search")
            return False
        except Exception as e:
            lg.error("Error Occurred")
            lg.exception(e)




import logging
logging.basicConfig(filename='sol_2.log',level= logging.DEBUG,filemode='w', format="%(lineno)d-%(asctime)s-%(levelname)s-%(message)s")
class Add_into_dict():
    def __init__(self, diction):
        self.diction = diction

    def element_to_add(self, element):
        logging.info("into the element_to_add method")
        if type(element) == dict:
            try:
                logging.info("insinde the try>>>>>>>...")
                self.diction.update(element)
                logging.info("New element is added")
                logging.info(f"{self.diction}")
            except Exception as e:
                logging.error("there is some issue with the code")
                logging.error(e)
                
        else:
            logging.error(f"please check {element} is valid dict or not ")
            
            
            
            


class Tuple:
    def __init__(self,t1):
        self.t1=t1
    def extract(self):
            start=int(input('Enter the start index number'))
            end=int(input('Enter the start index number'))
            return self.t1[start:end]






import mysql.connector
class my_sql:

    def __init__(self, host, user,passward):
        self.host= host
        self.user = user
        self.passward= passward
    
    def get_conn(self):
            self.mydb = mysql.connector.connect(host=self.host, user=self.user, password=self.passward)
            return self.mydb
        
    def get_cursor(self):
        self.cursor = self.mydb.cursor()
        return self.cursor
    
    def database(self,db_name):
        try:
            self.db_name = db_name
            return self.cursor.execute(f"create database if not exists {self.db_name}")
        except Exception as e:
            print(e)

    def table(self,sqldata):
        try:
            self.sqldata = sqldata
            self.cursor.execute(f'use {self.db_name}') 
            self.cursor.execute(f"create table if not exists  {self.sqldata}")
        except Exception as e:
            print(e)
    
    def insert(self,data):
        try:    
            self.data=data
            self.cursor.execute(f'use ineuron')
            self.cursor.execute(self.data)
            self.mydb.commit()
        except Exception as e:
            print(e)

    def details(self, detail):
        self.detail= detail
        self.cursor.execute(self.detail)
        print(self.cursor.fetchall())

    def update(self,new_update):
        try:  
            self.new_update = new_update
            self.cursor.execute(self.new_update)
            self.mydb.commit()
        except Exception as e:
            print(e)

    def delete(self, dell):
        try:
            self.dell = dell
            self.cursor.execute(self.dell)
            self.mydb.commit()

        except Exception as e:
            print(e)

db1= my_sql("localhost", "abc", "password")
db1.get_conn()
db1.get_cursor()
db1.database("ineuron")
db1.table("tab2(rollno INT(10) ,name VARCHAR(30) ,address VARCHAR(30) ,age INT(10) )")
#db1.insert("insert into tab2 values(12345,'Mudit','Dehradun',30)")
db1.details("select * from ineuron.tab2")
db1.update("UPDATE ineuron.tab2 SET age = 50 where age = 30")
# db1.details("select * from mud.tab1")
db1.delete("delete from ineuron.tab2 where age= 50")







import pymongo
import logging

logging.basicConfig(filename='CRUDMongo_class.log', level=logging.DEBUG , filemode='w', format="%(asctime)s %(levelname)s %(message)s")

class CRUDMongo:
    """
    class for perform the creation, read, update and delete operations on data with MONGO DB
    """

    def __init__(self):
        # setting connection
        logging.info("CONNECTING TO DATABASE    ")
        client = pymongo.MongoClient("mongodb+srv://mongodb:mongodb@cluster0.qivyyos.mongodb.net/?retryWrites=true&w=majority")
        db = client.test


        # create database if not exist
        logging.info("CREATING DB IF NOT EXIST")
        database = client['task']

        # creating table with fields in the file
        logging.info("CREATING TABLE IF NOT EXIST")
        self.collection = database['user']

    def insert_data(self):
        try:
            logging.info("INSERTING DATA INTO DATABASE")
            id = int(input("Enter ID: "))
            fname = input("Enter First name: ")
            lname = input("Enter Last name: ")
            cname = input("Enter Course name: ")
            cno = int(input("Enter Contact Number: "))
            data = {
                'id' : id,
                'first_name' : fname,
                'last_name' : lname,
                'course':cname,
                'contact_no':cno,
            }
            self.collection.insert_one(data)
            logging.info("DATA INSERTED")
            print("Data Inserted Successfully!")
            pass
        except pymongo.errors.OperationFailure as err:
            logging.error("There is some error" )
            print("Something went wrong: {}".format(err))

    def get_all_data(self):
        try:
            logging.info("FETCHING ALL DATA FROM DB")
            data = self.collection.find()
            print("All Data Fetched Successfully!")
            print("######  The Data  ######")
            for i in data:
                print(i, sep=" , ")
            logging.info("FETCHED ALL DATA FROM DB")
        except pymongo.errors.OperationFailure as err:
            logging.error("There is some error" )
            print("Something went wrong: {}".format(err))

    def get_specific_data(self):
        try:
            logging.info("FETCHING SPECIFIC DATA FROM DB")
            id = int(input("Enter ID: "))
            data = self.collection.find({'id':id})
            print("Data Fetched Successfully!")
            print("######  The Data  ######")
            for i in data:
                print(i, sep=" , ")
            logging.info("FETCHED SPECIFIC DATA FROM DB")
        except pymongo.errors.OperationFailure as err:
            logging.error("There is some error" )
            print("Something went wrong: {}".format(err))

    def update_data(self):
        try:
            logging.info("UPDATING SPECIFIC RECORD IN DB")
            id = int(input("Enter ID To Update Data: "))
            data = self.collection.find({'id':id})
            if data:
                print(f"###  Data Found of ID: {id}  ###")
                for i in data:
                    print(i)
                fnm = input("Enter New First Name To Update: ")
                lnm = input("Enter New Last Name To Update: ")
                cnm = input("Enter New Course Name To Update: ")
                mno = int(input("Enter New Mo.No. To Update: "))
                self.collection.update_one({"id":id},{"$set":{"first_name":fnm, "last_name":lnm, "course":cnm, "contact_no":mno}})
                print("Data Updated Successfully!")
                logging.info("UPDATED RECORD IN DB")
        except pymongo.errors.OperationFailure as err:
            logging.error("There is some error" )
            print("Something went wrong: {}".format(err))

    def delete_specific_record(self):
        try:
            logging.info("DELETING SPECIFIC RECORD FROM DB")
            id = int(input("Enter ID To Delete Data: "))
            data = self.collection.find({'id':id})
            if data:
                print(f"###  Data Found of ID: {id}  ###")
                for i in data:
                    print(i)
                print("Are Sure Want to Delete This Record?")
                choice = input("Enter (Yes/No): ")
                if choice.lower() == 'yes':
                    self.collection.delete_one({"id":id})
                    print("Data Deleted Successfully!")
                    logging.info("DELETED SPECIFIC RECORD IN DB")
                else:
                    print("Cancelled! No Record Deleted!")
        except pymongo.errors.OperationFailure as err:
            logging.error("There is some error" )
            print("Something went wrong: {}".format(err))


instance = CRUDMongo()
print("Choose Operation To Be Performed: ")
print("Insert Record Into Database => 1")
print("Get All Data From DB => 2 ")
print("Get Specific Data From DB => 3 ")
print("Update Specific Data => 4 ")
print("Delete Specific Record => 5")

choice = int(input("Enter Option => "))
if choice == 1:
    instance.insert_data()
elif choice == 2:
    instance.get_all_data()
elif choice == 3: 
    instance.get_specific_data()
elif choice == 4:
    instance.update_data()
elif choice == 5:
    instance.delete_specific_record()
else:
    print("Invalid Input")






import logging

logging.basicConfig(filename='file_calss.log', level=logging.DEBUG, filemode='w', format="""%(asctime)s %(levelname)s %(message)""")

class q6_filefn:
    def __init__(self, filename):
        self.filename = filename

    def read(self):
        logging.info("this is a start of a read operation")
        try:
            logging.info("inside try block of read fn")

            with open(self.filename, "r") as fo:
                str = fo.read()

                logging.info("i m able to read the file")
                #print(f"Read String is : {str}")
                # Close opend file
                fo.close()
                return str
        except FileNotFoundError as e:
            #print(e)
            logging.error("there is some issue with read file operation")
            logging.error(e)

    def write(self, txt):
        logging.info("this is a start of a write operation")
        try:
            with open(self.filename, "a") as fo:
                fo.write(txt)
                # Close opend file
                fo.close()
                logging.info("complete write operation")
                return
        except Exception as e:
            logging.error("there is some issue with write file operation")
            logging.error(e)
            

class child_filefn(q6_filefn):
    def __init__(self, filename):
        q6_filefn.__init__(self, filename)


# obj = q6_filefn("abc.txt")
# #obj.write("Hello, This is text file created using pythong programming..")
# obj.write("Practice makes Perfect.. Keep it up..")
# obj.read()

obj = child_filefn("abc1.txt")
obj.write("\n Hello, This is text file created using pythong programming..")
obj.write("\n Practice makes Perfect.. Keep it up..")
obj.read()









logging.basicConfig(filename='record_from_mongo.log', level=logging.DEBUG , filemode='w', format="%(asctime)s %(levelname)s %(message)s")

class Import_from_Mongo():
    
    def __init__(self, clienturl, filename):
        self.clienturl = clienturl
        self.filename = filename
        try:
            self.client = pymongo.MongoClient(self.clienturl)
        except Exception as e:
            print("Connection not established", e)
            logging.error("Connection not established", e)
        else:
            print("Connection to MongoDB is successful")
            logging.info("Connection to MongoDB is successful")
            
    def connect_to_collection(self, db_name, collection_name):
        try:
            self.database = self.client[db_name]
            self.collection = self.database[collection_name]
        except Exception as e:
            print("Connection not established", e)
            logging.error("Connection not established", e)
        else:
            print("Connection to collection is successful")
            logging.info("Connection to collection is successful")
    
    def importing_record(self):
        try:
            record = []
            for i in self.collection.find():
                    record.append(i)
            with open(self.filename, 'a') as f:
                f.write(str(record))
        except Exception as e:
            print("Importing unsuccessful", e)
            logging.error("Importing unsuccessfull", e)
        else:
            print("Importing successful")
            logging.info("Importing successfull")
            
    def show_data(self):
        try:
            with open(self.filename, 'r') as f:
                record = f.read()
                print(record)
                logging.info("Reading operation is successful")
        except Exception as e:
            print("There is some error", e)
            logging.error("There is some error", e)
                
                
                
                
                
 ## Q8: create a class to a calculator functionalities add, sub,mul,div, log, exponenet, power

import logging
import math

logging.basicConfig(filename='file_calss.log', level=logging.DEBUG, filemode='w', format="""%(asctime)s %(levelname)s %(message)s""")


class q8_calculator:
    
    def addition(self, list_arg):

        logging.info("this is start of addition fn")
        try:
            logging.info("inside try block of addition fn")
            
            sum = 0
            for i in list_arg:
                sum = sum + i
            
            print(f"addition of list is {str(sum)}")
        except Exception as e:
            #print(e)
            logging.error("there is some issue with addition fn")
            logging.error(e)

    def subtraction(self, no1, no2):
        no1 = int(no1)
        no2 = int(no2)
        logging.info("this is start of subtraction fn")
        try:
            logging.info("inside try block of subtraction fn")
            
            if no1>no2:
                ans = no1-no2
            else:
                print("Given number 1 is grater than 2")
                return
            
            print(f"subtraction of {no1} and {no2} is {str(ans)}")
        except Exception as e:
            #print(e)
            logging.error("there is some issue with subtraction fn")
            logging.error(e)

    def multipy(self, list_arg):
        logging.info("this is start of multipy fn")
        try:
            logging.info("inside try block of multipy fn")
            
            ans = 1
            for i in list_arg:
                ans = ans * i
            
            print(f"multipy of given number is {str(ans)}")
        except Exception as e:
            #print(e)
            logging.error("there is some issue with multipy fn")
            logging.error(e)

    def division(self, no1, no2):
        no1 = int(no1)
        no2 = int(no2)
        logging.info("this is start of division fn")
        try:
            logging.info("inside try block of division fn")
            
            if no1>no2:
                ans = no1/no2
            else:
                print("Given number 1 is grater than 2")
                return
            
            print(f"division of {no1} and {no2} is {str(ans)}")
        except Exception as e:
            #print(e)
            logging.error("there is some issue with division fn")
            logging.error(e)
    
    def log(self, no1):
        no1 = float(no1)
        
        logging.info("this is start of logarithm fn")
        try:
            logging.info("inside try block of logarithm fn")
                     
            ans = math.log(no1)            
            print(f"log of {no1} is {ans}")
            return
            
            print(f"division of {no1} and {no2} is {str(ans)}")
        except Exception as e:
            #print(e)
            logging.error("there is some issue with .logarithm fn")
            logging.error(e)
          

obj = q8_calculator()

obj.addition([1,2,3,4])
obj.subtraction(45, 5)
obj.multipy([1,2,3,4])
obj.division(45, 5)
obj.log(100.12)




import time
import tracemalloc

class Complexity:
    def __init__(self):
        pass
    
    @staticmethod
    def time_complexity(fn, *args):
        start_time = time.time()
        fn(*args)
        end_time = time.time()
        return end_time - start_time
    
    
    def space_complexity(self , fn , *args):
        tracemalloc.start()
        fn(*args)
        current, peak =  tracemalloc.get_traced_memory()
        tracemalloc.stop()
        
        return current, peak
        
        
        
        
        
        
        
        
        
        
        
        
        
 import logging
import mysql.connector as conn

import csv

logging.basicConfig(filename="sql_bulk_upload.log", level=logging.DEBUG, filemode='w', format = "%(asctime)s %(levelname)s %(message)s")

class MySQL_Bulk_Upload():
    
    def __init__(self, host, user, password,database):
        self.host = host
        self.user = user
        self.password = password
        self.database = database
        
    def create_connection(self):
        try:
            mydb = conn.connect(host = self.host, user = self.user, passwd = self.password, database = self.database)
            cursor = mydb.cursor()
            self.mydb = mydb
            self.cursor = cursor
            logging.info("Connection to DB successful")
            print("Connection to DB successful")
        except Exception as e:
            logging.error("Exception occurred", e)
        
        
    def create_table(self, table_name, columns):
        try:
            self.table_name = table_name
            self.columns = columns
            self.cursor.execute(f"CREATE TABLE if not exists {self.table_name}({self.columns})")
            self.mydb.commit()
            logging.info("table has created")
            print("Table has created")
        except Exception as e:
            logging.error("Exception occurred", e)
        
    def insert_data(self,csv_file):
        try:
            with open(csv_file, "r") as f:
                data  = csv.reader(f, delimiter = '\n')
                next(data)
                for i in data:
                    self.cursor.execute(f'insert into {self.database}.{self.table_name} values({str(i[0])})')
            self.mydb.commit()
            logging.info("Bulk Upload is successful")
        
        except Exception as e:
            print(e)
            logging.error("Exception occurred",e)
                   
        
    def show_data(self):
        try:
            self.cursor.execute(f"SELECT * from {self.table_name}")
            logging.info("Showing Data from table is successful")
            print(self.cursor.fetchall())
        except Exception as e:
            logging.error("Exception occurred", e)


obj = MySQL_Bulk_Upload("localhost", "abc", "password", "ineuron")

obj.create_connection()

obj.create_table("glassdata2", "col1 INT(10), col2 float(30,10), col3 float(30,10), col4 float(30,10), col5 float(30,10), col6 float(30,10), col7 float(30,10), col8 float(30,10), col9 float(30,10), col10 float(30,10), col11 INT(10)")


obj.insert_data("glass.data")


obj.show_data()




def test() -> int : 
    
    return "sudh" 
