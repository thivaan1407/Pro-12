CREATE TABLE Department (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50) NOT NULL
);

CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(50) NOT NULL,
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);

CREATE TABLE Faculty (
    FacultyID INT PRIMARY KEY,
    FacultyName VARCHAR(50) NOT NULL,
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);

CREATE TABLE Course (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50) NOT NULL,
    DepartmentID INT,
    FacultyID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID),
    FOREIGN KEY (FacultyID) REFERENCES Faculty(FacultyID)
);

CREATE TABLE Enrollment (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Course(CourseID)
);

INSERT INTO Department VALUES
(1, 'Computer Science'),
(2, 'Commerce'),
(3, 'Mathematics');

INSERT INTO Student VALUES
(1, 'Arun', 1),
(2, 'Bala', 1),
(3, 'Cathy', 2),
(4, 'Divya', 3);

INSERT INTO Faculty VALUES
(1, 'Ravi', 1),
(2, 'Kumar', 2),
(3, 'Priya', 3);

INSERT INTO Course VALUES
(1, 'Database Management System', 1, 1),
(2, 'Computer Networks', 1, 1),
(3, 'Accounting', 2, 2),
(4, 'Statistics', 3, 3);

INSERT INTO Enrollment VALUES
(1, 1, 1, '2026-01-10'),
(2, 1, 2, '2026-01-11'),
(3, 2, 1, '2026-01-12'),
(4, 3, 3, '2026-01-13'),
(5, 4, 4, '2026-01-14');
