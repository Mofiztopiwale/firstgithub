# firstgithub
# class Person:
#  def __init__(self, first_name, last_name, email_address):
#     self.first_name = first_name
#     self.last_name = last_name
#     self.email_address = email_address
#  def get_fullname(self):
#     return f"{self.first_name} {self.last_name}"

# class Customer(Person):
#  def __init__(self, first_name, last_name, email_address, customer_number):
#     super().__init__(first_name, last_name, email_address)
#     self.customer_number = customer_number

# class Employee(Person):
#  def __init__(self, first_name, last_name, email_address, pan_number):
#     super().__init__(first_name, last_name, email_address)
#     self.pan_number = pan_number
  
# def main():
#  people = [] # List to store created objects
#  while True:
#     print("Menu:")
#     print("1. Add Customer")
#     print("2. Add Employee")
#     print("3. Display All")
#     print("4. Exit")
#     choice = int(input("Enter your choice: "))
#     if choice == 1:
#         first_name = input("Enter customer's first name: ")
#         last_name = input("Enter customer's last name: ")
#         email_address = input("Enter customer's email address: ")
#         customer_number = input("Enter customer number: ")
#         customer = Customer(first_name, last_name, email_address, customer_number)
#         people.append(customer) # Add the object to the list
#         print("Customer added successfully.")
#     elif choice == 2:
#         first_name = input("Enter employee's first name: ")
#         last_name = input("Enter employee's last name: ")
#         email_address = input("Enter employee's email address: ")
#         pan_number = input("Enter PAN number: ")
#         employee = Employee(first_name, last_name, email_address, pan_number)
#         people.append(employee) # Add the object to the list
#         print("Employee added successfully.")
#     elif choice == 3:
#         print("\nAll Created Objects:")
#         for person in people:
#             print(type(person).__name__) # Display the class name (Customer or Employee)
#             print(f"Full Name: {person.get_fullname()}")
#             print(f"Email Address: {person.email_address}")
#             if isinstance(person, Customer):
#               print(f"Customer Number: {person.customer_number}")
#             elif isinstance(person, Employee):
#               print(f"PAN Number: {person.pan_number}")
#               print("-" * 20)
#     elif choice == 4:
#         break
#     else:
#         print("Invalid choice. Please select a valid option.")
# if __name__ == "__main__":
#  main()


import csv
# fields=['bookNo','title','author','price']
with open("books.csv",'w',newline="") as file:
 writer = csv.writer(file)
 count=int(input("Enter the number of books: "))
 # writer.writerow(fields)
 data=[]
 for i in range(count):
      li=[]
    print("enter details for item ",i+1)
    li.append(i+1)
    li.append(input("Enter book title: "))
    li.append(input("author name: "))
    li.append(int(input("Enter Price: ")))
    data.append(li)
 print(data)
 writer.writerows(data)
def search_by_author(value):
 with open("books.csv", "r") as file:
    reader = csv.reader(file)
    for a in reader:
        if a[2].lower() == value.lower():
            return a
    return []
def search_by_price(value):
 if value<=0:
    raise Exception("Value of price can't be less than or equal to 0")
 with open("books.csv", "r") as file:
    reader = csv.reader(file)
    li=[]
    for a in reader:
        if int(a[3]) < value:
            li.append(a)
    return li
def search_by_word(value):
 with open("books.csv", "r") as file:
    reader = csv.reader(file)
    li=[]
    for a in reader:
        if value in a[1].split():
            li.append(a)
    return li
print("1:Search Book by author\n2:Search Books below specified price (Rise an exception if price entered is <=0)\n3:Search Books where tilte contains the specified word\n4:Exit")
while True:
 val=int(input("enter choice: "))
 if val == 1:
    value = input("Enter books author: ")
    print("book is: ",search_by_author(value))
 elif val==2:
    value=int(input("enter price: "))
    print("books are: \n",search_by_price(value))
 elif val==3:
    value = input("enter word: ")
    print("books are: \n",search_by_word(value))
 else:
      print("Bye!!")
 exit(0)








# li=[]
# val=1
# print("1->.Add an item to the queue\n2->.Delete an item from queue\n3->.Display the queue\n4->exit")
# while val!=4:
#  val=int(input("Select one option: "))
#  if val==1:
#     a=input("enter a value to add: ")
#     li.append(a)
#  elif val==2:
#     print("the value ",li.pop(0)," is removed")
#  elif val==3:
#     print("Queue: ",*li)


def find_highest(detail):
 li=[[detail[a][2], detail[a][0]] for a in detail]
 val=li[0]
 for a in li[1:]:
    if val[0]<a[0]:
        val=a
        return val[1]

def find_course(details,course):
 val=details.get(course,0)
 if val==0:
    return "NO such course Found"
 return val

course_details={"MAT134":["Math","Jayesh",13],"DSA138":["DSA","Thapa",15],"PYT34":["Python","Abhishek",30],"SED32":["SED","Maggie",86]}
print("Available courses are: ",course_details)
print("Highest registered courese is: ",find_highest(course_details))
course=input("enter course code: ")
print(find_course(course_details,course))
