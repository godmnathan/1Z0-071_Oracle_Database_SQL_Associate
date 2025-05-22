# Oracle SQL Learning Path

This learning path is designed to guide you through the Oracle Database SQL Associate (1Z0-071) certification material in a structured and logical sequence. Follow this path to build your knowledge progressively from foundational concepts to advanced topics.

## 🏁 Getting Started

Before diving into specific SQL topics, complete these initial steps:

1. **Set up your environment**
   - Follow the [Setup Guide](setup/README.md) to install Oracle Database or set up a cloud instance
   - Configure the sample database using the provided scripts
   - Test your connection and ensure everything is working properly

2. **Understand the certification requirements**
   - Review the [exam objectives](https://education.oracle.com/oracle-database-sql/pexam_1Z0-071)
   - Familiarize yourself with the exam format and passing score
   - Create a study schedule based on your available time and target exam date

## 📚 Core Learning Path

### Phase 1: Database Fundamentals (Weeks 1-2)

1. **Relational Database Concepts**
   - [Introduction to Relational Databases](topics/001-relational-database-concepts/concepts.md)
   - [Entity-Relationship Diagrams](topics/001-relational-database-concepts/erd-guide.md)
   - [Database Architecture](topics/001-relational-database-concepts/architecture.md)
   - Complete the [Database Concepts Quiz](quizzes/001-database-concepts.md)

2. **Basic SQL Queries**
   - [SQL SELECT Statement Fundamentals](topics/002-retrieving-data/select-basics.md)
   - [Column Aliases and Expressions](topics/002-retrieving-data/aliases-expressions.md)
   - [Working with NULL Values](topics/002-retrieving-data/null-values.md)
   - Practice with [Basic Query Exercises](exercises/beginner/basic-queries.md)

### Phase 2: Data Filtering and Manipulation (Weeks 3-4)

3. **Restricting and Sorting Data**
   - [WHERE Clause and Conditions](topics/003-restricting-sorting/where-clause.md)
   - [Comparison and Logical Operators](topics/003-restricting-sorting/operators.md)
   - [ORDER BY and Sorting Options](topics/003-restricting-sorting/sorting.md)
   - Complete the [Data Filtering Quiz](quizzes/003-filtering-sorting.md)

4. **Single-Row Functions**
   - [Character Functions](topics/004-single-row-functions/character-functions.md)
   - [Number Functions](topics/004-single-row-functions/number-functions.md)
   - [Date Functions](topics/004-single-row-functions/date-functions.md)
   - Practice with [Function Exercises](exercises/intermediate/functions.md)

5. **Conversion Functions and Conditional Logic**
   - [Data Type Conversion](topics/005-conversion-functions/type-conversion.md)
   - [Conditional Expressions](topics/005-conversion-functions/conditional-expressions.md)
   - [CASE and DECODE](topics/005-conversion-functions/case-decode.md)
   - Complete the [Conversion Functions Quiz](quizzes/005-conversion-functions.md)

### Phase 3: Data Aggregation and Multi-Table Queries (Weeks 5-6)

6. **Group Functions**
   - [Aggregate Functions](topics/006-group-functions/aggregate-functions.md)
   - [GROUP BY Clause](topics/006-group-functions/group-by.md)
   - [HAVING Clause](topics/006-group-functions/having.md)
   - Practice with [Aggregation Exercises](exercises/intermediate/aggregation.md)

7. **Joining Multiple Tables**
   - [Inner Joins](topics/007-multiple-tables/inner-joins.md)
   - [Outer Joins](topics/007-multiple-tables/outer-joins.md)
   - [Self Joins and Non-Equijoins](topics/007-multiple-tables/self-joins.md)
   - Complete the [Joins Quiz](quizzes/007-joins.md)

### Phase 4: Advanced Queries (Weeks 7-8)

8. **Subqueries**
   - [Single-Row Subqueries](topics/008-subqueries/single-row.md)
   - [Multiple-Row Subqueries](topics/008-subqueries/multiple-row.md)
   - [Correlated Subqueries](topics/008-subqueries/correlated.md)
   - Practice with [Subquery Exercises](exercises/advanced/subqueries.md)

9. **SET Operators**
   - [UNION and UNION ALL](topics/009-set-operators/union.md)
   - [INTERSECT and MINUS](topics/009-set-operators/intersect-minus.md)
   - [Sorting Combined Results](topics/009-set-operators/sorting.md)
   - Complete the [SET Operators Quiz](quizzes/009-set-operators.md)

### Phase 5: Data Manipulation and Management (Weeks 9-10)

10. **DML Operations**
    - [INSERT Statements](topics/010-dml-statements/insert.md)
    - [UPDATE Statements](topics/010-dml-statements/update.md)
    - [DELETE Statements](topics/010-dml-statements/delete.md)
    - [MERGE Statement](topics/010-dml-statements/merge.md)
    - [Transaction Control](topics/010-dml-statements/transactions.md)
    - Practice with [DML Exercises](exercises/advanced/dml-operations.md)

11. **Database Objects Management**
    - [Tables and Constraints](topics/011-database-objects/tables-constraints.md)
    - [Indexes and Performance](topics/011-database-objects/indexes.md)
    - [Sequences and Synonyms](topics/011-database-objects/sequences-synonyms.md)
    - Complete the [Database Objects Quiz](quizzes/011-database-objects.md)

12. **DDL and Schema Management**
    - [Creating and Modifying Tables](topics/012-ddl/create-alter-tables.md)
    - [Managing Constraints](topics/012-ddl/constraints.md)
    - [Temporary and External Tables](topics/012-ddl/special-tables.md)
    - Practice with [DDL Exercises](exercises/advanced/ddl-operations.md)

### Phase 6: Advanced Topics and Exam Preparation (Weeks 11-12)

13. **Data Dictionary and System Views**
    - [Understanding the Data Dictionary](topics/013-data-dictionary/overview.md)
    - [Querying System Views](topics/013-data-dictionary/system-views.md)
    - Complete the [Data Dictionary Quiz](quizzes/013-data-dictionary.md)

14. **Time Zone Management**
    - [Date/Time Functions](topics/014-time-zones/datetime-functions.md)
    - [INTERVAL Data Types](topics/014-time-zones/interval-types.md)
    - Practice with [Time Zone Exercises](exercises/advanced/time-zones.md)

15. **Final Exam Preparation**
    - Review the [Comprehensive Cheat Sheet](cheat_sheets/comprehensive.md)
    - Take [Practice Exam 1](practice_exams/exam1.md)
    - Take [Practice Exam 2](practice_exams/exam2.md)
    - Review incorrect answers and weak areas
    - Take [Final Practice Exam](practice_exams/final.md)

## 📈 Progress Tracking

Track your progress through this learning path:

- ✅ Mark topics as complete when you finish them
- 📝 Take notes on challenging concepts
- 🔄 Revisit difficult topics as needed
- 📊 Monitor your quiz and practice exam scores

## 🎓 Beyond Certification

After completing your certification:

- Explore advanced Oracle features not covered in the exam
- Work on real-world projects to apply your knowledge
- Consider pursuing higher-level Oracle certifications
- Contribute back to this repository to help others learn

Remember that consistent practice is key to mastering SQL. Try to write queries daily and challenge yourself with increasingly complex problems.

---

<p align="center">
  <b>Good luck with your Oracle SQL journey!</b>
</p>
