# pdbc_learners_examples_program
pdbc for beginners, practice program.



import pymysql as a
db = a.connect("127.0.0.1","root","rootroot","abhishek")

cursor = db.cursor()

while True:

    ch = int(input("Select Choice\n 1.Insert data\n 2.Update data\n 3.delete data\n 4.Show data\n 5.exit\n"))

    if ch == 1:
        marks = int(input("enter marks"))
        name = input("enter name")
        rollno = int(input("enter roll no"))


        cursor.execute("insert into students values({},'{}',{})".format(marks,name,rollno))
        db.commit()


    

    elif ch == 2:
        up = int(input("select to update by:\n 1.Update marks\n 2.Update name\n 3.update rollno"))
        if up == 1:
            marks = int(input("enter marks to be updated"))
            name = input("enter the name of student ")
            cursor.execute("update students set marks = {} where name='{}'".format(marks,name))
            db.commit()
            
            
        elif up == 2:
            name = input("enter the name of student ")
            marks = int(input("enter marks"))
            
            cursor.execute("update students set name = '{}' where marks={}".format(marks,name))
            db.commit()
           

        elif up == 3:

            roll = int(input("enter roll no to be updated"))
            name = input("enter the name of student ")
            cursor.execute("update students set rollno = {} where name='{}'".format(roll,name))
            db.commit()
            

    elif  ch == 3:
         name = input("enter name")
         cursor.execute("delete from students where name = '{}'".format(name))
         db.commit()
         

    elif ch == 4:

        cursor.execute("select * from students")
        for data in cursor:
            print(data[0],data[1],data[2])
            db.commit()
        
    elif ch == 5:
        break


db.close()
         
        
     
             
         


        
            
