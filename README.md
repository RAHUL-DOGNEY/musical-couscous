# musical-couscous
This sql Query's help us to Practice 

Show all employees who have managers with a salary higher than $15,000. Show the following data: employee name, manager name, manager salary, and salary grade of the manager.
                SELECT First_Name as Manager, Manager_Id, Salary as Grade_Salary
               FROM Employees 
                WHERE SALARY > 15000 AND Managee_Id IS NOT NULL;

Show the names, salaries, and the number of dollars (in thousands) that all employees earn.
                  SELECTFirts_Name as Name, Salary,TRUNC(salary/1000)
                  FROM Employees;

Show the names and locations for all departments, and the number of employees working in each department. Make sure that departments without employees are included as well.    
           SELECT d.DEPARTMENT_ID,d.DEPARTMENT_NAME,d.LOCATION_ID,COUNT
(e.EMPLOYEE_ID) 
           FROM departments d,employees e where d.DEPARTMENT_ID =e.DEPARTMENT_ID  
           GROUP  By d.DEPARTMENT_NAME
Which jobs are found in the Administration and Executive departments, and how many employees do these jobs? Show the job with the highest frequency first.
             SELECT j.JOB_ID,COUNT(e.EMPLOYEE_ID) AS FREQUENCY
             FROM jobs j,employees e,departments d
             WHERE e.JOB_ID=j.JOB_ID AND e.DEPARTMENT_ID=d.DEPARTMENT_ID AND d.DEPARTMENT_NAME IN("Administration","Executive") 
            GROUP BY j.JOB_ID ORDER BY FREQUENCY DESC,JOB_ID ASC;

Show the employees that have no commission with a 10% raise in their salary (round off the salaries).
      SELECT First_Name, Salary*1.1 AS "New salary"
      FROM employees
