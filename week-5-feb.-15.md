# Structured data, Part 2: Databases

---

## Before class

![](/assets/book.png)

#### Required reading:

* [Big Data tipsheet](https://docs.google.com/file/d/0BzQD-tsALvmHSFBiUWNHV3ZCNkU/edit?pli=1) Elizabeth Lucas


![](/assets/pencil.png)

#### Exercise:

- Install [Atom](https://atom.io/) and the [markdown-preview-plus](https://atom.io/packages/markdown-preview-plus) package (See instructions in Slack)
- Complete this [Markdown tutorial](http://www.markdowntutorial.com/).
- Convert the data diary you wrote last week into Markdown format (re-save it as `diary.md`). Use this [Markdown syntax cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), if you need to.
- Add to your new Markdown data diary.
    - Ask at least 3 questions of your dataset. (Think critically! Points lost for shallow, I'm-just-trying-to-complete-the-assignment questions.)
    - Use your basic Excel skills to answer them.
    - Record your questions, answers and the steps you took in your diary.
    - Be sure you write the answers to your question in English prose, as though you were intending to publish your findings in a story.

#### For example:

If you have a dataset of college salaries, you might ask:
- How much better are tenured professors paid than adjuncts?
- Which school has the most clerical staff earning below $40K per year?
- In which school are men's and women's salaries most different?

You would answer those questions in **publishable English** like so:

> The average salary for men and women is most different in the business school, where men earn $25,000 more on average than their female colleagues.

You would document each step you took to arrive at that conclusion in your diary, maybe like this:

> #### Steps
- Sorted data by school (A) and gender columns (B)
- Calculated average salary by range of cells for each school by gender with formula `=AVERAGE(C2:C200)`, etc.
- Subtracted the average for women for the average for men
- Found the highest difference in the averages

---

## In class
- Install [DB Browser for SQLite](http://sqlitebrowser.org/) and setup a database
- Learn basic SQL verbs and practice making your own queries

---

# Databases

Up till now you've been viewing and manipulating data stored in spreadsheets using Microsoft Excel. Excel is a great, human-friendly tool for designing and manipulating data, but it's limited to a certain scale. Once you need data to be entered electronically rather than by hand or be easily accessible by other components, like automatic reports or features on a website, you need something designed more with a machine in mind.

You need a database.

Databases are simply collections of data stored in tables. Understanding how databases are constructed and queried is essential to being able to query large and complex datasets, which is how you [get your scoop](http://www.niemanlab.org/2013/12/scooped-by-code/).

### Database structure

A database is simply a collection of data stored in tables. A database can have multiple related tables. A table can have multiple fields, including fields related to other tables.

We'll look at an example next, but to preface the discussion, think about the Tidy Data concept we looked at last week. Data stored in tidy tables is exactly the basic organizational structure of databases. You can think of a single data table as a tidy table. We only use slightly different terminology: Instead of talking about _columns_ and _rows_, we describe data tables in _fields_ and _records_. They are almost exactly equivalent. Fields, like columns, should represent variables. Records, like rows, represent observations.

Let's look at that example:


![](/assets/database_structure.png)

Let's assume this database represents a store. Our store database consists of three separate tables: `Customers`, `Orders` and `Products`.

Each of those tables has its own collection of fields related to the particular information that table stores.

The `Orders` table has two special fields that relate records in the `Orders` table to records in the two other tables. Those fields join records across tables to create the complete information about any one sale at our store.

Think this table through using practical example. Say Sally is a customer in our store. Her personal information would be stored in the `Customers` table. In that table Sally has at most one record. But Sally is a frequent customer of our store, so she has placed multiple orders, each of which would be an individual record in the `Orders` table. But say we are a specialty shop, and Sally is really only buying the same product each time she makes an order. That product would have just one record in the `Products` table.

Multiply that structure by thousands or millions of individual sales, customers and products and you start to see the problem. We need a way to easily relate records across these three tables in order to answer even basic questions within our database.

# Enter the SQL

SQL stands for _Structured Query Language_. _Query_ in this case means asking questions, and _structured language_ just means we have an established way -- a code -- for asking those questions. 

SQL is a code for querying a database to get only specific records we care about. It has very few parts, but in combination they 


```SQL
SELECT
last_name,
first_name
FROM "Customers";
```