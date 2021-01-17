# Demonstration-CRUD-Operations-in-Entity-Framework
20487_MOD02_DEMO_L4

### Demonstration: CRUD Operations in Entity Framework

#### Demonstration Steps

1. Open the Command Prompt window.

2. To change the directory to the starter project, at the command prompt, run the following command:

   ```bash
    cd [Repository Root]\AllFiles\Mod02\DemoFiles\CRUD\Starter
   ```

3. To restore all the dependencies and tools of a project, at the command prompt, run the following command:

   ```base
    dotnet restore
   ```

4. To open the project in VS Code, paste the following command, and then press Enter:

   ```bash
    code .
   ```

5. On the **Explorer** blade, under **STARTER**, double-click **Program.cs**.

6. To retrieve the **ASP** course from the **Courses** table, inside the **using** block under **DBInitializer**, append the following code:

   ```cs
    Course ASPCourse = (from course in context.Courses
    where course.Name == "ASP.NET Core" select course).Single();
   ```

7. To create two new student records named **Thomas Anderson** and **Terry Adams**, append the following code to the **using** block:

   ```cs
    Student firstStudent = new Student() { Name = "Thomas Anderson" };
    Student secondStudent = new Student() { Name = "Terry Adams" };
   ```

8. To add the two newly created student records to the **ASP** course, append the following code to the **using** block:

   ```cs
    ASPCourse.Students.Add(firstStudent);
    ASPCourse.Students.Add(secondStudent);
   ```

9. To give the teacher of the **ASP** course a $1000 salary raise, append the following code to the **using** block:

   ```cs
    ASPCourse.CourseTeacher.Salary += 1000;
   ```

10. To select **Student_1** from the **ASP** course, append the following code to the **using** block:

    ```cs
     Student studentToRemove = ASPCourse.Students.FirstOrDefault((student) => student.Name == "Student_1");
    ```

11. To remove the student record from the **ASP** course, append the following code to the **using** block:

    ```cs
     ASPCourse.Students.Remove(studentToRemove);
    ```

12. Save the changes, print the result, and then append the following code to the **using** block:

    ```cs
     context.SaveChanges();
     Console.WriteLine(ASPCourse);
     Console.ReadLine();
    ```

13. To run the application, in command prompt, run the following command:

    ```bash
    dotnet run
    ```

14. After a few seconds, the list of students appears in the console window. Notice that there are two new student records at the bottom of the list, and Student 1 is missing from the list. Also notice that the salary of the teacher is now **$101,000**.

![20487D_Images](https://github.com/ialcaidef/Demonstration-CRUD-Operations-in-Entity-Framework/blob/master/01.png)

15. Notice the Structured Query Language (SQL) update, and delete and insert statements that correspond to the salary update, student record deletion, and the addition of the two new student records.

16. To stop the application, in the command prompt press Ctrl+C.

17. Close all open windows.
