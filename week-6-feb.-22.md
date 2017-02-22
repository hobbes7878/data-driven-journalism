# Advanced SQL

---

## Before class


![](/assets/pencil.png)

#### Exercise 1: Practice SQL

For this exercise you may use either your own data from last week's homework _or_ the data from TEA we used in class last week.


- Use SQL to answer **three questions** about your data. If you're using your own data, these may be the same three questions you answered last week. If using TEA data from class, you need to ask three new questions.
- Use [Markdown code blocks and syntax highlighting](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#code-and-syntax-highlighting) to record your SQL queries in your data diary. (HINT: The syntax highlighting code for SQL is `sql`.)
- Make sure you write and answer your questions **in English**.

#### Exercise 2:
Draft pitches for **three** open records requests for electronic data you'd like to file with Texas public agencies as part of your midterm project.
- Describe the data you hope to get for each request.
- Research the agency you will be requesting the data from. What data do they make available online now, if any?
- Reach out to someone at the agency by telephone or email and ask them about the data you're requesting. What do they say about it?
- Each open records request should be pitched as a paragraph that tells me everything you know about the data you're requesting, including how big the dataset is, what's in it, and most importantly the story you think you could write after analyzing it.

Feel free to workshop your requests in Slack with each other and with me throughout the week.

Be prepared to talk through your favorite of your three requests in class.
    

##### What if I don't know what data to request?

Then you need to do all the more research. Cruise the websites of Texas state agencies. Look at research done by academics by topic on J-Store. Google for what stories other reporters have done in other states.

##### Remember

We're trying to tell a story that will be publishable in your school newspaper. Consider agencies that will deal with data appropriate for that publication like public universities or other educational institutions.

**NOTE: You should spend _far more time_ on Exercise 2 than 1 this week. Points lost if it's not obvious from your pitches that was the case.**



---

## In class 

- Learn SQL Joins
- Workshop data requests

### More SQL

Up to now, we've been querying data in a single table. Often, though data will be kept across multiple tables or be more interesting when combined with a completely separate data source.

The most obvious example is combining a dataset with demographic info from the U.S. Census, which we'll do later. 

Being able to query across tables is an essential and powerful part of SQL. We call this **joining** tables.

SQL joins always involve just two tables. The act of joining them creates a new table composed of some combination of the other two.w

So how do we combine tables? By using the table's fields!

### Primary keys

The simplest way to combine tables by fields is to use a field explicitly designed for it: a **primary key.**

A primary key is a column that has data that can identify a single row in the table.

Say we had a table of students. The field containing your student ID number would be our primary key because it contains unique identifying information for each student that can be used to find one and only one row in the table.

Primary keys _must be unique_ so they only indicate a single row. In the same table of students, your name would not make a good primary key value because perhaps another student shares your name. Then when we query the table we have no single field that we can use to get just your row in the table.

Primary keys are often just called _IDs_, for obvious reasons.

A great use of primary keys is to associate data between tables.

Take a look at this diagram:

![](http://rdbms.opengrass.net/2_Database%20Design/2.1_TermsOfReference/r/keyForeign.gif)

We have a table of classes and a table of students taking classes. Notice both tables have a `courseid` field. This field associates records from the students table with those in the courses table. Joining the data from both tables using this field tells us which students are taking which courses.

The `courseid` field on the courses table is our primary key. Notice all the values are unique, indicating a single class in the table.

The `courseid` field on the students table is _not unique_. This should make intuitive sense. Several students take each class. We call this field a **foreign key** because it refers to the primary key on another table.

Which field is the primary key on the student table?

### Joins

SQL allows you to do several kinds of joins using primary and foreign keys. Each type is designed to include a specific subset of data that either matches or doesn't on the key used to join the table.

But before we get into each type, let's think about a practical example from our store database from last week.

Remember we had tables for products, orders and customers.

What if we wanted to get a table of all our products that had been ordered by customers?

What if we wanted to get table of all the products that _hadn't_ been ordered by customers?

These are questions that require information from two tables, namely products and orders. That means we want to join information from those two tables. 

Our products table should have a **primary key**, call it `product_id`. Our orders table will have a **foreign key** to products. We can call that `product_fk`.

Now think about our two questions.


### Types of table joins

![](http://www.dofactory.com/Images/sql-joins.png)

#### Inner join

Selects only those records common in both tables.

#### Full join

Selects all records in both tables.

#### Left join

Selects all records from the first/left table and those matched in the last/right table.

#### Right join

Selects all records in the last/right table and those matched in the first/left table.