
# Prototype Database Style #

### Things to be consider: ###
1. Folder Structure.
2. Configuration or Convention.
3. Scope of the Data Structure to the any types of system.
4. Security.
5. Time and Space Complexity.
6. Modularity
    - meaning all the module is not tightly coupled you need to analyze carefully the module
    to make it independent.
7. Flowchart Example how to install a module.
8. "Plugin" consider as a abstract layer that will not dependent in the model of the application.

#### Note: #####
1. Hooks.
    - install
    - uninstall
2. Need to present a way of saving a data in a flexible data structure.

#### Question: ####
1. How will the proposed data structure cater the flexibility.

## Drupal
- They're using Entity
- Problem:
    - Joining Tables
    - Distinct

## Wordpress
- They're allowed the developer to build own schema and optional to apply the prefix for each table
that are set in the wp-config.php

##### Proposed Data Structure: #####

Benefits of EAV:
1. Can easily add new column without altering the whole table.
2. Eliminate the null column in each row.

## NEED TO LEARN IN RELATIONAL DB ##
1. Database Schema
2. Database Design Pattern
3. Database Optimization
4. Database Indexing

## NEW UPDATE ##
1. Sample ERD
2. How to Install
3. What are the requirements/required files
4. Depending on the structure.



### How to plan your database relational: ###

Pain Points:

1. You need to correctly design it, meaning one time structure.
    - changes are possible but it's paintful
2. Database is not for creative.
    - meaning we can't do something to find new ways to structure.
    - if you want to use creativity use it on UI.
    - must be METHODICAL not CREATIVE.
3. Questions:
    a. What is the main point of this database?
        - must be careful for this answer.
        - to support mobile, desktop or web.
        * What are the goals of the proposed system? the important question.
    b. What do you have already? 
        * do you have existing database?
            - Don't just import: re-architect
        * do you have existing process?
            - Physical assets 
    c. The two questions are essential for the third question, what table do you need?
        - each entity, object or table.
    d. After figuring out what are the tables needed, now you must zoom in deeper what column/attribute do you need?
        - what exactly data need to store in the table.
        - must be specific as possible defining the column name for the purpose.
        - data type
        - limit size
        - flexibility is nice but not in the database we need to be static to declare what data type should be using for each column.
    e. What relationship do you need for each entity?
        - foreign key
- Reference:
    [ https://www.youtube.com/watch?v=s91pPLx_T3Q ]

Database is an organized collection of data.

Types of Databases
- Relational (Oracle, SQL Server, MySQL, DB2)
- Data Warehouse
    - Star Schema
        - [ https://www.youtube.com/watch?v=Q7KHW2oCOUI ]
    - [ https://en.wikipedia.org/wiki/Dimensional_modeling ]
- [ https://www.lucidchart.com/pages/database-diagram/database-models ]

* 20 Database Design Best Practices
- https://dzone.com/articles/20-database-design-best

* Relational Database
- https://stackoverflow.com/questions/145689/relational-database-design-patterns

## Presentation Structure:
1. Module Management
2. Data Structure
3. Multiple Database Supports
4. Users Data Structure
5. Example create CMS module for Nucleus
    - EAV model.


CMS
    - ACL
        - view
            - index.blade.php
    - Module management
        - view
            - 
    - User management
    - Login
        - view
            - admin
            - frontend
            - login.blade.php