# tables
Students Table:
course table


## Write a query to retrieve the names of students who are enrolled in the 'Math' course.

## Write a query to find the names of students who are not enrolled in any course.

## Write a query to retrieve the names of students who are enrolled in both 'Math' and 'English' courses.

## Write a query to find the names of students who are not enrolled in any course using the NOT IN clause.

## Write a query to retrieve the names of students who are enrolled in at least one course using the EXISTS clause.

## Write a query to find the names of students who are not enrolled in any course using the NOT EXISTS clause.




CREATE TABLE student (StudentID INT PRIMARY KEY, StudentName VARCHAR(50));

CREATE TABLE Course (CourseID INT PRIMARY KEY, CourseName VARCHAR(50));

INSERT INTO student VALUES (1, 'Alice'), (2, 'Bob'), (3, 'Charlie'), (4, 'David');

SELECT * FROM student;

INSERT INTO Course VALUES (101, 'Math'), (102, 'English'), (103, 'Science'), (104, 'History');

SELECT * FROM Course;

CREATE TABLE enrolements (StudentID INT, CourseID INT);

INSERT INTO enrolements VALUES (1, 101), (1, 102), (2, 101), (3, 102), (4, 103);

SELECT * FROM enrolements;

SELECT s.StudentName FROM student s
JOIN enrolements e ON s.StudentID = e.StudentID
WHERE e.CourseID = 101;

SELECT s.StudentName FROM student s
JOIN enrolements e ON s.StudentID = e.StudentID
WHERE e.StudentID IS NULL;

SELECT s.StudentName FROM student s
JOIN enrolements e ON s.StudentID = e.StudentID
WHERE e.CourseID = 101 OR e.CourseID = 102;

SELECT s.StudentName FROM student s
WHERE s.StudentID NOT IN(SELECT e.StudentID FROM enrolements e);

SELECT s.StudentName FROM student s
WHERE EXISTS(SELECT 1 FROM enrolements e WHERE e.StudentID = s.StudentID);

SELECT s.StudentName FROM student s
WHERE NOT EXISTS(SELECT 1 FROM enrolements e WHERE e.StudentID = s.StudentID);
