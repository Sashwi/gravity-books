# Book store_ Data understanding project
This project helps to undersand the backend data system of an online bookstore.

# ER diagram
The database schema is visualized in the following ER diagram:
ERD illustrating all major entities, attributes, and relationships

erd_gravity (1).png

The Relational Entity(ER) Diagram shows how an online bookstore would manage books, authors, customers, and orders behind the scenes.

# Understanding of the Schema

Totally we have 15 tables in this book store database system, in which we have a interconnection among the tables to perform the requirement.

1.book             -  Stores book details
2.author	         -  Stores author information
3.book_author      -	Connects books and authors (many-to-many connection)
4.book_language    -  Language information of books
5.publisher        -	Book Publishing company information
6.customer	       -  Customer details
7.customer_address -	Maps customers to their respective addresses
8.address	         -  Detailed address information 
9.country	         -  List of countries
10.address_status	 -  Status of each address whether active or not
11.cust_order	     -  Orders placed by customers
12.order_line	     -  What are all the books are in each order
13.shipping_method -  Delivery options available
14.order_status	   -  Order lifecycle stages
15.order_history	 -  Timeline of status changes for an order

Almost all the functions involved in the bookstore has been included in the schema,So we can perform any of the requirement from customer and for the analysis.

# Table-by-Table Explanation of the Bookstore ER Diagram

✅Book table
This is the central table in the schema. It stores data for each book which is the main aspect of all functiions in store.

Key columns:
🗝️book_id (PK)    : Unique ID for each book
   title           : Title of the book
   isbn13          : Standard book identification number
🔗language_id(FK)  : Links to book_language 
   num_pages       : Total number of pages.
   publication_date: Date of publication.
🔗publisher_id(FK) : Links to publisher

📎 Relationships:
Connected to publisher, book_language, book_author, and order_line

✅author
Key columns:
🗝️author_id (PK): Unique identifier.
  author_name  : Full name of the author.
   
📎Relationships:
 Linked to book through the junction table book_author

✅book_author
A junction table for the many-to-many relationship between book and author.
Key columns:
  🗝️🔗 book_id (PK, FK)   : ID of the book.
  🗝️🔗 author_id (PK, FK) : ID of the author.
  
Function:
Allows multiple authors for a book, and an author to write multiple books.








  
