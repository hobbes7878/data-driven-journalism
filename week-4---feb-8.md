# Data structures

---

## Before class

![](/assets/book.png)

#### Required reading:

* [Data journalists are the new punks](https://www.youtube.com/watch?v=h2zbvmXskSE) Simon Rogers - 10 mins.
* [The Quartz guide to bad data](https://github.com/Quartz/bad-data-guide) Quartz. Skim it. - 10 mins.

##### Excel skills

If you are unfamiliar with the following operations in Microsoft Excel, go through these free tutorials. (Watch the 5 min. videos!)

* [Creating Simple Formulas](http://www.gcflearnfree.org/excel2010/creating-simple-formulas/1/)
* [Creating Complex Formulas](http://www.gcflearnfree.org/excel2010/creating-complex-formulas/1/)
* [Working with Basic Functions](http://www.gcflearnfree.org/excel2010/working-with-basic-functions/1/)


![](/assets/pencil.png)

#### Exercise:

Pick a publicly available dataset from a Texas municipal or state agency website. (Preferably one that actually interests you.) Download it and open it in Excel. Begin a **"data diary"** about your dataset. You should answer as many of the following questions in your data diary as apply to your data.

- Who collected this data?
- What does the agency use this data for, i.e., why do they collect it?
- When is the data collected?
- What time span does the data cover?
- How many records are in the dataset?
- What does a single record represent in the data?
- Describe each column of the dataset, individually:
    - What data is in this column?
    - What _kind_ of data does it contain, e.g., character strings, numbers, dates, etc.?
    - If the column contains numeric data, what is the maximum and minimum value in the column? What's the average?
    - What if any codes are used in this column and what do they mean?
- Using Quartz's guide, what elements of "bad data" do you see in this dataset, if any?

    
### Important: 
Data diaries are due by **noon Tuesday**. Please send them to me via Slack in the #assignments channel.

---

## In class
- Learn data terms, taxonomy and structures
- Practice some basic data manipulation in Excel

**Install party** 
- [DB Browser for SQLite](http://sqlitebrowser.org/)
- [SublimeText package manager](https://packagecontrol.io/installation)
- [SublimeText Markdown Preview package](https://packagecontrol.io/packages/Markdown%20Preview)

---

### Kinds of Data

#### Qualitative
Qualitative data represent categorical values like the color of people's eyes or the make and model of automobiles.

#### Quantitative
Quantitative data represent numeric data like the temperature yesterday or your annual salary.

#### Discrete

Discrete data represent a limited set of possible values that data can take.

- **All** qualitative data is discrete. Your eyes are either blue or green or brown.
- **Some** quantitative data is discrete. Your car engine has either 4 cylinders or 6 or 8.

#### Continuous

Continuous data represent an infinite (or practically infinite) set of possible values that data can take.

- **No** qualitative data is continuous.
- **Some** quantitative data is continuous. The temperature is 55 degrees, or it can be 55.5 or 55.55 or 55.555...

---
### Data types

| Type  | Description  |
|---|---|
|String   | A "string" or characters. Your name is a string.|
| Integer  | A whole number like 4 and 5.  |
| Float / Decimal  | A decimal number like 4.3 or 5.2.  |
|  Date / Datetime | A numeric representation of a date or a date and a time.  |
|Boolean   | A true or false value.  |
|Null |A value that represents no value |

---
### Data structures

#### Structured data
Highly organized data. Basically data than can be constructed into a table. Think of an Excel table like the one below where every row shares the same columns of data.

| Breed     | Hair  | Lifespan |
|-----------|-------|----------|
| Poodle    | Long  | 12       |
| Chihuahua | Short | 17       |

#### Unstructured data
Disorganized data that can not be immediately constructed into a table. Think of a cache of documents, each has its own pieces of data unique to each document that aren't shared between documents.

---

### "Tidy" data

[Tidy data](ftp://cran.r-project.org/pub/R/web/packages/tidyr/vignettes/tidy-data.html) represents structured data formatted in a specific way. As an example, take a look at our dog table again.

We can separate that data into three structural components: **observations**, **variables** and **values**.

**Variables** represent each _kind_ of data the dataset has values for. The columns of the dog table are our variables: breed, hair and lifespan. (They're called variables because the values they represent _vary_.)

**Observations** represent each particular example we have data for. The rows of our dogs table are our observations. Each row is a separate dog for which we have several data attributes recorded in our table. (You can imagine a biologist observing each dog to collect its data.)

**Values** represent the actual categorical or numeric data recorded for each dog. Short hair for Chihuahua. 12-year lifespan for a Poodle.

**Rule:** Tidy data is any data where the variables are always structured as columns, the observations are always structured as rows and values are always at the intersection of the two, just like our dog table.

| Breed     | Hair  | Lifespan |
|-----------|-------|----------|
| Poodle    | Long  | 12       |
| Chihuahua | Short | 17       |



### "Untidy" data

Untidy data is any tabular data that is not "tidy" according to our rule above. For example, here's table of health statistics for the average American man and woman:

|        | Men  | Women |
|--------|------|-------|
| Height | 5'9" | 5'4"  |
| Weight | 196  | 166.2 |

In this case, our table shows the variables Height and Weight, which are rows. But it doesn't show a third variable, Gender. Men and Women are actually **values** of Gender, which are structured as columns in the table.

Values as columns, variables as rows? This data is **untidy**.

Fortunately, most untidy data can be tidied up by manipulating the data a little. This is the same health data as above, only transposed into a tidy format:

| Gender | Height | Weight |
|--------|--------|--------|
| Men    | 5'9"   | 196    |
| Women  | 5'4"   | 166.2  |

#### How to spot untidy data
Watch out for data tables that aren't "square" or that you can't read left-to-right.

#### Why is tidy data so important?

Tidy data is "machine-readable," meaning it's a format computers understand. That's important because we use code to manipulate our data to answer the questions we ask of it. Tidy data is a language we can share.


---

## Data storage



#### Common file types

| File type                  | Extension    |
|----------------------------|--------------|
| Excel                      | .xls / .xlsx |
| Text file                  | .txt         |
| Comma-separated value file | .csv         |
| Tab-separated value file   | .tsv         |

- #### Which is best?
CSV is the "gold standard" of data. When you can get your data this way, you should.



### "Delimiting" data

- #### Fixed-width

Data separated by white space, limited at horizontal character positions.

![](http://blog.scribesoft.com/wp-content/uploads/2013/11/Fixed.png)



- #### Character-separated

Data separated by specific characters, often a comma or a pipe.

![](http://www.howtogeek.com/wp-content/uploads/2010/07/507x277ximage126.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.6KErtxFUf7.png)

### Encoding

Computers have different ways to represent letters, numbers, punctuation and other symbols. We call these encodings because they are a way of mapping codes a computer understands to a specific character that we understand.

Why do you need to know this? Sometimes characters don't translate well between encodings and you end up [garbled text](https://github.com/Quartz/bad-data-guide#text-is-garbled) in your data like this: ���.



## The dread data file

![](https://cdn4.iconfinder.com/data/icons/CS5/128/ACP_PDF%202_file_document.png)


PDF's are **the worst** and among the most popular formats you'll see structured data in.

They were designed to create image perfect versions of documents, but that also means machines don't understand them. Excel can't read them, you can't load the data they contain into a database.

### PDF Extraction

Tools like [Tabula](http://tabula.technology/) or services like [CometDocs](http://www.cometdocs.com/) are generally what's required to extract data from a PDF into something more structured like an Excel file or CSV.

---

![](https://lh3.ggpht.com/GkNfqm17WFuzaIR87_oz690ErF63hL08Ngj73QtDxyWlCOF80d2gWd2GHrPLJJ-YmHYS=w300)


# Excel Basics
