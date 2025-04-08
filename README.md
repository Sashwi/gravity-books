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
  🗝️🔗 book_id (PK, FK)   : ID of the book
  🗝️🔗 author_id (PK, FK) : ID of the author
  
Function:
Allows multiple authors for a book, and an author to write multiple books.

✅book_language
A reference table that stores supported languages.

Key columns:
🗝️language_id (PK): Unique language code.
language_code: Short code of language (Example:EN,FR)
language_name: Full name (Example:English, French)

Relationship:
Referenced taken from book table

✅publisher
Stores information about book publishers.

Key columns:
🗝️publisher_id (PK): Unique publisher ID.
publisher_name: Name of the publishing company.

Relationship:
Referenced taken from book

✅customer
Holds information about the customers who purchase books.

Key columns:
🗝️customer_id (PK): Unique ID
first_name, last_name: Full name
email: Contact email

Relationship:
Linked to cust_order.
Linked to addresses via customer_address

✅customer_address
A bridge table between customers and addresses with address status tracking.

Key columns:
🗝️🔗customer_id (PK, FK): Links to customer.
🗝️🔗address_id (PK, FK): Links to address.
🔗status_id (FK): Links to address_status.

Function:Allows customers to have multiple addresses (current, previous, etc)

✅address
Stores the physical address details.

Key columns:
🗝️address_id (PK): Unique ID.
street_number, street_name: Address lines.
city: City name.
🔗country_id (FK): Links to country.

Relationship:Referenced in customer_address and cust_order as destination.

✅country
Lookup table for countries.

Key columns:
🗝️country_id (PK): Unique ID.
country_name: Name of the country.

Used in:address table

✅address_status
Describes the status of a customer’s address.

Key columns:
🗝️status_id (PK): Unique ID.

address_status: Status description (e.g., current, previous).

Used in:customer_address to define if the address is active or not.

✅cust_order
Represents a single order placed by a customer.

Key columns:
🗝️order_id (PK): Unique ID.
order_date: Date and time the order was placed.
🔗customer_id (FK): Who placed the order.
shipping_method_id (FK): Delivery method.
dest_address_id (FK): Where it's going.

Relationships:Links to order_line, order_history tables

✅order_line
Represents the books included in a specific order.

Key columns:
🗝️line_id (PK): Unique line item ID.
🔗order_id (FK): Which order this line belongs to.
🔗book_id (FK): Which book was ordered.
price: Price of the book at the time of order.

Function:Enables orders with multiple books.

✅shipping_method
Stores shipping options.

Key columns:
method_id (PK): Unique ID.
method_name: Shipping type (e.g., Express, Standard).
cost: Cost of that method.

Used in:cust_order table

✅order_status
Lookup table for possible order stages.

Key columns:
🗝️status_id (PK): Unique ID.
status_value: Description (e.g., Placed, Shipped, Delivered).

Used in:order_history

✅order_history
Tracks how the order progresses over time.

Key columns:
🗝️history_id (PK): Unique ID.
🔗order_id (FK): Which order this is about.
🔗status_id (FK): Current status.
status_date: When the status changed.

Function:Gives a timeline view of order processing.











  
