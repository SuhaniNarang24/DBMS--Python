# DBMS--Python
This Project was later improvised to a RDBMS

studentData = {
    #GR # [ Name     Roll, Fees                    Marks      ]
    #(Key)[           #    Paid Std Physics, Chem, Bio, Math, Eng, computer]
    100 : ['t',       99, False,11,[100,       100,  99,  100,  100,    100]],
    110 : ['b',       98, True ,11,[91,        59,   56,  77,   59,   75]],
    200 : ['t',       80, False,11,[70,       97,  86,   100,  69,    79]],
    600 : ['ahana', 100, False,6, [78,       87,  98,  100,  89,    90]],
    500 : ['ashi', 101, False,8, [78,       87,  98,  100,  89,    90], "Award 1"]
    }
#____________________________________________________________________________
   
def addNewStudent():
    newGRNum=max(studentData.keys())+5
    print("New GR NUMBER IS",newGRNum)
    name=input("Enter the name of the new student:")
    rollNo=int(input("enter the new roll number of the student:"))
    feespaid=False
    std=int(input("Enter the class in which the student is studying in:"))
    listofmarks=[]
    w=1
    for w in range (w,7):
        marks=int(input("Marks of student in subject"))
        listofmarks.append(marks)
    dictValue = [name, rollNo,feespaid,std,listofmarks]
    studentData[newGRNum]=dictValue
   
#_______________________________________________________________________________

def feePayment():
    GRNum = int(input("enter GR number:"))
    print (studentData[GRNum])
    if (studentData[GRNum][2] == False):
        print("not paid")
        classofstudent=studentData[GRNum][3]
        if  classofstudent in range(1,5):
            print("50,000 rupees is to be deposited")

        elif classofstudent in range (5,9):
            print("1 lakh rupees is to be deposited")

        elif classofstudent in range(9,13):
            print("1 lakh and 50,000 is to be deposited")
        studentData[GRNum][2] = True
        #here we are assuming that each time we ask for the details of payment
        #and it is false ,then it gets updated that payment is done.
        print (studentData[GRNum])
    else:
        print("paid")
#_______________________________________________________________________________

def deleteStudent():
    GRNum = int(input("enter GR number:"))
    print (studentData[GRNum])
    del studentData[GRNum]
    #print (studentData[GRNum])
#_______________________________________________________________________________

def aStudentRecord():
    GRNum=int(input("Whose record do you want(GRnumber)? "))
    if (GRNum in studentData):

        aStudentDataList = studentData[GRNum]
        print("name of the student:",aStudentDataList[0])
        print("rollno",aStudentDataList[1])
        i = 1
        sum_marks=0
        for aMark in aStudentDataList [4]:
            print ("marks in subject:", i, aMark)
            i = i + 1
            sum_marks=aMark+sum_marks  
        print("total marks in all subjects is:",sum_marks,"average",
              sum_marks/6)
    else:
        print ("No such student in the data", GRNum)

#_______________________________________________________________________________

def rankStudents():
   
    classofStudent=int(input("Enter the class of the student:"))
    listofselectedstudents=[]
    for student in studentData:
        if classofStudent==studentData[student][3]:
            listofselectedstudents.append([student,sum(studentData[student][4])])
    print(listofselectedstudents)
    lenOfList = len(listofselectedstudents)
   

    for i in range(lenOfList):
        minima = listofselectedstudents[i][1]
        for j in range(i, lenOfList):
          if (minima > listofselectedstudents[j][1]):
                minima = listofselectedstudents[j][1]

                # Swapping
                t=listofselectedstudents[j]
                listofselectedstudents[j] = listofselectedstudents[i]
                listofselectedstudents[i] = t

    print ('The sorted list is:', listofselectedstudents)
    k=0
    for k in range(k+1,lenOfList+1):
        print("The",k,"ranker is:", listofselectedstudents[lenOfList-k],'GRnumber:',listofselectedstudents[lenOfList-k][0],\
              'Aggregated Marks:',listofselectedstudents[lenOfList-k][1])
   
        #print('the", i ,"ranker is:",listofselectedstudents[lenOfList-1],'GRnumber:',listofselectedstudents[lenOfList-1][0],\
          #'Aggregated Marks:',listofselectedstudents[lenOfList-1][1])

   
#_______________________________________________________________________________
def awardingStudents():
    GRnumber=int(input("Enter the GR number of the student:"))
    Award=input("Enter the award that the student has received:")
    studentData[GRnumber].append(Award)
    print(studentData)


#__________________________________________________
   
# Main program
# ===========
while(True):
    print ("1. Add new student")
    print ("2. Pay fees")
    print ("3. Deleting the student data")
    print ("4. Recall a student's data")
    print ("5. Ranking of students")
    print ("6. Awarding of students")
    print ("7. Exit")

    inpChoice = int(input('Enter your choice: '))

    if (inpChoice == 1):
        print (studentData)
        addNewStudent()
        print (studentData)
    elif (inpChoice == 2):
        feePayment()
    elif (inpChoice == 3):
        deleteStudent()
    elif (inpChoice == 4):
        aStudentRecord()
    elif (inpChoice == 5):
        rankStudents()
    elif (inpChoice == 6):
        awardingStudents()
    elif (inpChoice == 7):
        break
    else:
        print ('Invalid choice')
