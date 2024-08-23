# SQL-PROJECT-
# LIBRARY MANAGEMENT SYSTEM
CREATE TABLE Book (
    Book_ID INT PRIMARY KEY,
    Title VARCHAR(255),
    Author VARCHAR(255),
    PublishedYear INT
);
CREATE TABLE Employee (
    Employee_ID INT PRIMARY KEY,
    Employee_Name VARCHAR(100),
    Mobile_Number VARCHAR(100),
    Email VARCHAR(255)
    );
    CREATE TABLE Customers(
    Customer_ID INT PRIMARY KEY,
    Book_ID INT,
    Customer_name varchar(100),
    Due_Date DATE,
    foreign key (Book_ID) references book (Book_ID)
    );
    CREATE TABLE Purchases(
    Purchase_id int primary key ,
    Customer_id int,
    Purchse_date date,
    Email VARCHAR(255),
    foreign key ( Customer_id) references customers (Customer_ID)
    );

    INSERT INTO book (Book_ID,Title,Author,PublishedYear) VALUES
    (1001, 'The Great Gatsby', 'F. Scott Fitzgerald', 1925),
    (1002, 'To Kill a Mockingbird', 'Harper Lee', 1960),
    (1003, '1984', 'George Orwell', 1949),
    (1004, 'Pride and Prejudice', 'Jane Austen', 1813),
    (1005, 'The Catcher in the Rye', 'J.D. Salinger', 1951),
    (1006, 'Moby-Dick', 'Herman Melville', 1851),
    (1007, 'War and Peace', 'Leo Tolstoy', 1869),
    (1008, 'The Lord of the Rings', 'J.R.R. Tolkien', 1954),
    (1009, 'Jane Eyre', 'Charlotte Brontë', 1847),
    (1010, 'The Hobbit', 'J.R.R. Tolkien', 1937);

    INSERT INTO Employee (Employee_ID, Employee_Name, Mobile_Number, Email) VALUES
    (1, 'Alice Smith', '123-456-7890', 'alice.smith@example.com'),
    (2, 'Bob Johnson', '234-567-8901', 'bob.johnson@example.com'),
    (3, 'Charlie Brown', '345-678-9012', 'charlie.brown@example.com'),
    (4, 'Diana Prince', '456-789-0123', 'diana.prince@example.com'),
    (5, 'Eve Adams', '567-890-1234', 'eve.adams@example.com'),
    (6, 'Frank Castle', '678-901-2345', 'frank.castle@example.com'),
    (7, 'Grace Lee', '789-012-3456', 'grace.lee@example.com'),
    (8, 'Hank Pym', '890-123-4567', 'hank.pym@example.com'),
    (9, 'Ivy Walker', '901-234-5678', 'ivy.walker@example.com'),
    (10, 'John Doe', '012-345-6789', 'john.doe@example.com');

    INSERT INTO Customers (Customer_ID, Book_ID, Customer_Name, Due_Date) VALUES
    (1, 1001, 'Alice Smith', '2024-09-01'),
    (2, 1002, 'Bob Johnson', '2024-09-05'),
    (3, 1003, 'Charlie Brown', '2024-09-10'),
    (4, 1004, 'Diana Prince', '2024-09-15'),
    (5, 1005, 'Eve Adams', '2024-09-20'),
    (6, 1006, 'Frank Castle', '2024-09-25'),
    (7, 1007, 'Grace Lee', '2024-09-30'),
    (8, 1008, 'Hank Pym', '2024-10-05'),
    (9, 1009, 'Ivy Walker', '2024-10-10'),
    (10, 1010, 'John Doe', '2024-10-15');

    INSERT INTO Purchases (Purchase_ID, Customer_ID, Purchase_Date, Email) VALUES
    (1, 1, '2024-08-01', 'alice.smith@example.com'),
    (2, 2, '2024-08-02', 'bob.johnson@example.com'),
    (3, 3, '2024-08-03', 'charlie.brown@example.com'),
    (4, 4, '2024-08-04', 'diana.prince@example.com'),
    (5, 5, '2024-08-05', 'eve.adams@example.com'),
    (6, 6, '2024-08-06', 'frank.castle@example.com'),
    (7, 7, '2024-08-07', 'grace.lee@example.com'),
    (8, 8, '2024-08-08', 'hank.pym@example.com'),
    (9, 9, '2024-08-09', 'ivy.walker@example.com'),
    (10, 10, '2024-08-10', 'john.doe@example.com');

    
     Update a Book's Information

# Retrieve All Books

   # 1.Question: How do you retrieve all the records from the Book table?

     Answer: SELECT * FROM Book;

 #  2. Question: How do you update the PublishedYear of the book with Book_ID = 1 to 1925

      Answer: UPDATE Book
              SET PublishedYear = 1925
              WHERE Book_ID = 1;

# Delete a Book Record

  #  3. Question: How do you delete the book with Book_ID = 1 from the Book table?

      Answer: DELETE FROM Book
              WHERE Book_ID = 1;

#  Retrieve Books Published After a Specific Year

#    4. Question: How do you find all books published after the year 1937?

       Answer: SELECT * FROM Book
               WHERE PublishedYear > 1937;
#  5.Question: How do you find the email addresses of employees with a specific Employee_ID of 1?

        Answer: SELECT Email FROM Employee
                WHERE Employee_ID = 1;

#  6.Question:  Write an SQL query to update the mobile number of the employee with Employee_ID 2 to '234-567-8901'.

       Answer: UPDATE Employee
               SET Mobile_Number = '234-567-8901'
               WHERE Employee_ID = 2;
               
 # 7.Question: What is the SQL query to find all employees whose names contain the substring 'John Doe'?

       Answer: SELECT Employee_Name, Mobile_Number, Email FROM Employee
               WHERE Employee_Name LIKE '%John Doe%';

# 8.Question :How do you find the due date of the customer with Customer_ID 2?

       Answer: Due_Date FROM Customers
                WHERE Customer_ID = 2;
 
  # 9.Question: How do you find the average Due_Date (as the midpoint) of all checked-out books?

     Answer: SELECT AVG(Due_Date) AS Average_Due_Date
             FROM Customers;

 #  10.Question: How do you rename the column Customer_name to Name in the Customers table?

     Answer: ALTER TABLE Customers
             RENAME COLUMN Customer_name TO Name;



  #  11.Question:How do you update the Email for a customer with Customer_id 2 to 'alice.smith@example.com'?

       Answer: SET Email = 'alice.smith@example.com'
               WHERE Customer_id = 123;
  #  12.Question :How would you list all unique Customer_id values from the Purchases table?

       Answer: SELECT DISTINCT Customer_id
               FROM Purchases;


  #  13.Question : What are the details of customers and their associated purchases?
       
       Answer   :  select * from customers join purchases
                   ON
                   customers.customer_id=purchases.customer_id;


   #  14.Question : How can you retrieve a list of all books and include any associated customer details if available?
        
        Answer   : select * from Book  left join customers
                   ON
                   Book.book_id=customers.book_id;

   
# Stored Procedure

      DELIMITER $$

      CREATE PROCEDURE add_customer (
      IN p_Customer_ID INT,
      IN p_Book_ID INT,
      IN p_Customer_name VARCHAR(100),
      IN p_Due_Date DATE
)
BEGIN
      INSERT INTO customers (Customer_ID, Book_ID, Customer_name, Due_Date)
      VALUES (p_Customer_ID, p_Book_ID, p_Customer_name, p_Due_Date);
END $$

DELIMITER ;

     CALL add_customer(11, 1010, 'John Doe', '2024-10-15');
     SELECT * FROM customers 
     WHERE Customer_ID = 10;
 
# joins query

       select * from customers join purchases
       ON
       customers.customer_id=purchases.customer_id;


       select * from Book  left join customers
       ON
       Book.book_id=customers.book_id;
  
# view
       CREATE VIEW vicky AS
       SELECT purchase_id,purchase_Date from purchases;
       select * from vicky;


   
