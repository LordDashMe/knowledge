# Form Normalization

## 1NF - First Normal Form

- The most basic of normal forms.

- The table values must be ```atomic```.

- The table must be ```isomorphic```.
  1. There's no top-to-bottom ordering to the rows.
  2. There's no left-to-right ordering to the columns.
  3. There are no duplicate rows.
  4. Every row-and-column intersection contains exactly one value from the applicable domain (and nothing else).
  5. All columns are regular [i.e. rows have no hidden components such as row IDs, object IDs, or hidden timestamps].

- Each cell in the table must contain only one piece of information and there can be no duplicate rows.

### Customer Table

| Customer ID | First Name | Last Name | Telephone Number |
| ----------- | ---------- | --------- | ---------------- |
| 123 | John | Doe | 555-861-2025 |
| 123 | John | Doe | 192-122-1111 |
| 456 | Michael | Sauce | 182-929-2929 |
| 456 | Michael | Sauce | (555) 403-1659 Ext. 53 |
| 789 | Eunice | Calm | 555-808-9633 |

- Note that the "ID" is no longer unique in this solution with duplicated customers. To uniquely identify a row, we need to use a combination of (ID, Telephone Number). The value of the combination is unique although each column separately contains repeated values. Being able to uniquely identify a row (tuple) is a requirement of 1NF.

### Customer Info Table

| Customer ID | First Name | Last Name |
| ----------- | ---------- | --------- |
| 123 | John | Doe |
| 456 | Michael | Sauce |
| 789 | Eunice | Calm |

### Customer Contact Table

| ID | Customer ID | Telephone Number |
| -- | ----------- | ---------------- |
| 1 | 123 | 555-861-2025 |
| 2 | 123 | 192-122-1111 |
| 3 | 456 | 182-929-2929 |
| 4 | 456 | (555) 403-1659 Ext. 53 |
| 5 | 789 | 555-808-9633 |

- Columns do not contain more than one telephone number in this design. Instead, each Customer-to-Telephone Number link appears on its own row. Using Customer ID as key, a one-to-many relationship exists between the name and the number tables. A row in the "parent" table, Customer Name, can be associated with many telephone number rows in the "child" table, Customer Telephone Number, but each telephone number belongs to one, and only one customer. It is worth noting that this design meets the additional requirements for second and third normal form.

- Reference: <https://en.wikipedia.org/wiki/First_normal_form>

## 2NF - Second Normal Form

- A database is said to be in 2NF - Second Normal Form if:
  1. The database meets 1NF requirements.
  2. Each column in a table represents what the primary key is describing.

- A functional dependency on part of any candidate key is a violation of 2NF. In addition to the primary key, the relation may contain other candidate keys; it is necessary to establish that no non-prime attributes have part-key dependencies on any of these candidate keys.

### Manufacturer Table

| Manufacturer | Model | Model Full Name | Manufacturer Country |
| ------------ | ----- | --------------- | -------------------- |
| Forte | X-Prime | Forte X-Prime | Italy |
| Forte | Ultraclean | Forte Ultraclean | Italy |
| Dent-o-Fresh | EZbrush | Dent-o-Fresh | EZbrush USA |
| Kobayashi | ST-60 | Kobayashi ST-60 | Japan |
| Hoch | Toothmaster | Hoch Toothmaster | Germany |
| Hoch | X-Prime | Hoch X-Prime | Germany |

- Even if the designer has specified the primary key as {Model Full Name}, the relation is not in 2NF because of the other candidate keys. {Manufacturer, Model} is also a candidate key, and Manufacturer Country is dependent on a proper subset of it: Manufacturer. To make the design conform to 2NF, it is necessary to have two relations:

### Manufacturer Location Table

| Manufacturer | Manufacturer Country |
| ------------ | -------------------- |
| Forte | Italy |
| Dent-o-Fresh | USA |
| Kobayashi | Japan |
| Hoch | Germany |

### Manufacturer Model Table

| Manufacturer | Model | Model Full Name |
| ------------ | ----- | --------------- |
| Forte | X-Prime | Forte X-Prime |
| Forte | Ultraclean | Forte Ultraclean |
| Dent-o-Fresh | EZbrush | Dent-o-Fresh EZbrush |
| Kobayashi | ST-60 | Kobayashi ST-60 |
| Hoch | Toothmaster | Hoch Toothmaster |
| Hoch | X-Prime | Hoch X-Prime |

- Reference: <https://en.wikipedia.org/wiki/Second_normal_form>

## 3NF - Third Normal Form

- A database is said to be in Third Normal Form if:
  1. The databse meets 2NF requirements.
  2. Any column, that is not the primary key, is not dependent on any other column.

### Courses Table

| Course | Semester | Places | TeacherID | TeacherName |
| ------ | -------- | ------ | --------- | ----------- |
| IT101 | 2009-1 | 100 | 332 | Mr Jones |
| IT101 | 2009-2 | 100 | 332 | Mr Jones |
| IT102 | 2009-1 | 200 | 495 | Mr Bentley |
| IT102 | 2010-1 | 150 | 332 | Mr Jones |
| IT103 | 2009-2 | 120 | 242 | Mrs Smith |

- Now it should be obvious that TeacherName is dependent on TeacherID - so this is not in 3NF. To fix this, we do much the same as we did in 2NF - take TeacherName out of this table, and put it in its own, which has TeacherID as the key.

### Teachers Table

| TeacherID | TeacherName |
| --------- |-------------|
| 332 | Mr Jones |
| 495 | Mr Bentley |
| 242 | Mrs Smith |

## Simplified Definition

- 1NF - must be atomic table and no duplicate in any direction.

- 2NF - must passed the 1NF and if there's any column dependent on the primary key column, create a new table to pass the 2NF.

- 3NF - must passed the 2NF and if there's any column which is not dependent on the primary key column but dependent on any other foreign key column in the same table, create a new table to pass the 3NF.
