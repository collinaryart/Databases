# Databases
Documents:
1. Conceptual model diagram
2. Logical model diagram (Oracle Data Modeler)
3. Schema file of CREATE TABLE statements (Oracle Data Modeler)
4. PDF of full normalisation of 2 ReadMore
Community Library (RCL) documents showing UNF, 1NF, 2NF and 3NF
5. Output from the Oracle spool command showing the tables have been created (Oracle Data Modeler)

# Conceptual Design Assumptions
1. Borrowers can
register immediately without borrowing
any books.
2. A manager must be
appointed to at least 1 branch.
3. Borrowers register
when they borrow their first book.
4. A borrower can start
multiple loans at the same time.

# Logical Design Assumptions

1. The LGA related information is provided by Google and set to 5 characters in length.
2. The amount of the transaction is retained to two decimal places of accuracy.
3. Users may not pay fines on time, so the system should be able to record late fines.
4. Users can borrow up to 10 books at a time and cannot continue to borrow books
beyond this limit.
5. The maximum period of each book borrowing is 6 months, after
which the book has to be returned or renewed.
6. Users must pay all fines before they can continue borrowing books, and the system
should enforce this rule.
7. No 2 report documents in the library may be borrowed at the same time.

# Why add loan_id as a proxy key (SK)?
Reason for adding the Surrogate Key (loan_id):Complex composite key: Since the LOAN entity
has a composite key with several attributes, adding a surrogate key like loan_id simplifies the
entity. This is beneficial because it:
- reduces complexity in queries, especially in joins between
tables.
- improves performance when indexing the table.
- ensures each loan transaction can be uniquely identified by a simple key rather than multiple
attributes.

Expected large data volume in LOAN entity: The LOAN entity is likely to hold a significant amount
of data (many records), so using a simple surrogate key like loan_id can help streamline database
operations and improve scalability.

# Why add fine_id as a proxy key (SK)?
Independence of Fines and Loans: While there is a correlation between Fines (FINE) and Loans
(LOAN), they are of different business logic. Adding fine_id as a proxy key for the FINE entity ensures that each fine record has a separate, unique identifier that does not conflict with the
loan_id in the LOAN entity.

# Acknowledgements
Developed with Frank Zheng.
