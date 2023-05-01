Download Link: https://assignmentchef.com/product/solved-b561-assignment-1-the-postgresql-system-relational-database-and-simple-sql
<br>
The goal of this assignment is to become familiar with the PostgreSQL system, to create a relational database, and to write and evaluate some simple SQL statements and queries in that system.

You need to upload a single file with name assignment1.sql file to Canvas which contains the necessary SQL statements that solve the problems in this assignment. The assignment1.sql file must be so that the AI’s can run it in their PostgreSQL shell. (We will post a sample .sql file that gives the template for your ssignment1.sql file.)

Before you can solve this assignment, you will need download PostgreSQL (version 10) and install it on your computer.

Consider the following relation schemas for a database that maintains sailors, boats, and reservations of boats by sailors.

Sailor(<u>sid </u>integer, sname text, rating integer)

Boat(<u>bid </u>integer, bname text, color text)

Reserves(<u>sid </u>integer, <u>bid </u>integer, day text)

You should assume that sid in Reserves is a foreign key that references the primary key sid in Sailor, and that bid in Reserves is a foreign key that references the primary key bid in Boat.

Note the files sailor.sql, boat.sql, and reserves.sql that contain the relation instances for the Sailor, Boat, and Reserves relations that are supplied with this assignment.

<strong>1 Database creation and impact of constraints on INSERT and DELETE statements.</strong>

<ol>

 <li>Create a database with name assignment1 in PostgreSQL that stores these relations. Make sure to specify primary and foreign keys. Then write SQL queries that return each of the relation instances Sailor, Boat, and Reserves.</li>

 <li>Provide 6 examples that illustrate how the presence or absence of primaryand foreign keys affects insert and deletes in these relations. To solve this problem, you will need to experiment with the Sailor, Boat, and Reserves relation schemas and instances. For example, you should consider altering primary keys and foreign key constraints and then consider various sequences of insert and delete operations. You may also need to change some of the relation instances. Certain inserts and deletes should succeed but other should create error conditions. (Consider the lecture notes about keys, foreign keys, and inserts and deletes as a guide to solve this problem.)</li>

</ol>

<h1>2           Formulating queries in SQL</h1>

Write SQL statements for the following queries. For this assignment, make sure to always use tuple variables in your SQL statements. For example, in formulating the query “Find the name of each boat” you should write the query

SELECT b.bname FROM Boat b

instead of

SELECT bname FROM Boat

Make sure that each of your queries returns a set but not a bag. In other words, make appropriate use of the DISTINCT clause where necessary.

<ol>

 <li>Find the sid and rating of each sailor.</li>

 <li>Find the sid, name, and rating of each sailor whose rating is in the range [2<em>,</em>11] but not in the range [8<em>,</em>10].</li>

 <li>Find the bid, name, and color of each non-red boat that was reserved by some sailor whose rating is more than 7.</li>

 <li>Find the bid and name of each boat that was reserved by a sailor on a weekend day but that was not reserved by a sailor on a Tuesday.</li>

 <li>Find the sid of each sailor who reserved both a red boat and a green boat.</li>

 <li>Find the sid and name of each each sailor who reserved at least two different boats. (You should write this query without using the COUNT aggregate function.)</li>

 <li>Find the pairs of sids (<em>s</em><sub>1</sub><em>,s</em><sub>2</sub>) of different sailors who both reserved a same boat.</li>

 <li>Find the sid of each sailor who did not reserve any boats on a Monday or on a Tuesday.</li>

 <li>Find the pairs (<em>s,b</em>) such that the sailor with sid <em>s </em>reserved the boat with bid <em>b</em>, provided that the sailor <em>s </em>has a rating greater than 6 and the color of boat <em>b </em>is not red.</li>

 <li>Find the bid of each boat that where reserved by just one sailor. (You should write this query without using the COUNT aggregate function.)</li>

 <li>Find the sid of each sailor who reserved fewer than 3 boats. (You should write this query without using the COUNT aggregate function.)</li>

</ol>

<h1>3           Formulating queries in Predicate Logic</h1>

For each query in Section <strong>??</strong>, specify an expression in the Predicate Logic (also called Relational Calculus). This will illustrate how closely this logic is associated with SQL.

To learn more about this logic, you can consult the book <em>Database Management Systems </em>by Ramakrishnan and Gehrke which you can find online.

You should upload your answers for these problems in a separate pdf file named Assignment1.pdf.

Assume that associated with each of the relation Sailor, Boat, and Reserves, there is a predicate as follows:

Relation      Predicate

Sailor Sailor(<em>x,y,z</em>) Boat Boat(<em>x,y,z</em>)

Sailor             Sailor(<em>x,y,z</em>)

As an example consider the query “Find the bid and name of each boat that was reserved by fewer than 2 sailors.” This query can be formulated in the Predicate Logic with <em>domain variables </em>as follows<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>:

{(<em>b,n</em>)|∃<em>c</em>Boat(<em>b,n,c</em>)∧¬(∃<em>s</em><sub>1</sub>∃<em>d</em><sub>1</sub>∃<em>s</em><sub>2</sub>∃<em>d</em><sub>2</sub>(Reserves(<em>s</em><sub>1</sub><em>,b,d</em><sub>1</sub>)∧Reserves(<em>s</em><sub>2</sub><em>,b,d</em><sub>2</sub>)∧<em>s</em><sub>1 </sub>6= <em>s</em><sub>2</sub>)}<em>.</em>

And alternative formulation using a Predicate Logic with <em>tuple variables </em>is as follows and is more inline with the SQL formulation:<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>:

{(<strong>b</strong><em>.</em>bid<em>,</em><strong>b</strong><em>.</em>bname)|Boat(<strong>b</strong>)∧

¬(∃<strong>r</strong><sub>1</sub>∃<strong>r</strong><sub>2</sub>(Reserves(<strong>r</strong><sub>1</sub>) ∧ Reserves(<strong>r</strong><sub>2</sub>) ∧ <strong>r</strong><sub>1</sub><em>.</em>bid = <strong>b</strong><em>.</em>bid ∧ r<sub>2</sub><em>.</em>bid = <strong>b</strong><em>.</em>bid ∧ r<sub>1</sub><em>.</em>sid 6= <strong>r</strong><sub>2</sub><em>.</em>sid)}<em>.</em>

<a href="#_ftnref1" name="_ftn1">[1]</a> This logic is also called the Domain Relational Calculus.

<a href="#_ftnref2" name="_ftn2">[2]</a> This logic is also called the Tuple Relational Calculus.