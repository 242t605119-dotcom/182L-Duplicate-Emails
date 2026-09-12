# LeetCode 182 - Duplicate Emails

## Problem

Write a SQL query to report all the duplicate emails in the `Person` table.

An email is considered a duplicate if it appears more than once in the table.

The result should contain the duplicate email addresses in a column named `Email`.

## Table Structure

The `Person` table contains:

* `id` - Unique ID of the person
* `email` - Email address of the person

## Approach

This problem can be solved using `GROUP BY` and `HAVING`.

First, we group all rows having the same email address.

Then, we use `COUNT()` to count how many times each email appears.

Finally, the `HAVING` condition keeps only those emails whose count is greater than 1.

## SQL Query

```sql
SELECT email AS Email
FROM Person
GROUP BY email
HAVING COUNT(email) > 1;
```

## Example

### Input

| id | email                     |
| -- | ------------------------- |
| 1  | [a@b.com](mailto:a@b.com) |
| 2  | [c@d.com](mailto:c@d.com) |
| 3  | [a@b.com](mailto:a@b.com) |

### Output

| Email                     |
| ------------------------- |
| [a@b.com](mailto:a@b.com) |

The email `a@b.com` appears twice, so it is considered a duplicate.

## Key Concepts

* `GROUP BY`
* `COUNT()`
* `HAVING`
* Duplicate detection
* SQL aggregation

## Why GROUP BY?

`GROUP BY email` puts identical email addresses into the same group.

For example:

```text
a@b.com
c@d.com
a@b.com
```

After grouping:

```text
a@b.com → 2
c@d.com → 1
```

The query then selects only the group with a count greater than `1`.

## Why HAVING?

`WHERE` is generally used to filter individual rows before grouping.

`HAVING` is used to filter groups after aggregation.

Since we are checking the result of `COUNT(email)`, we use:

```sql
HAVING COUNT(email) > 1
```

## Time Complexity

**O(n)** approximately, depending on the database engine and execution plan.

The database needs to process the rows and group them by email.

## Space Complexity

**O(n)** in the worst case because the database may need to maintain groups for distinct email values.

## Difficulty

**Easy**

## Topic

* SQL
* GROUP BY
* HAVING
* COUNT
* Duplicate values
* Aggregate functions

## What I Learned

This problem helped me understand how to find duplicate values in a database using SQL aggregation.

The main idea is to group the same email addresses together and use `COUNT()` to determine how many times each email appears.

## Author

T.Nandhini
