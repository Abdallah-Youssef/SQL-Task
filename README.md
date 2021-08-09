1)


	SELECT * from employees;


-------------------------
2)

	SELECT * from employees e
	WHERE e.dept_id = 1;


-----------------
3)

	SELECT * from employees e
	INNER JOIN departments d ON (d.dept_id = e.dept_id)
	WHERE d.description LIKE 'Sales';

------------------
4)

	SELECT * from employees e
	WHERE e.name LIKE 'J%';

-------------------
5)

	SELECT d.description, MAX(e.salary) from employees e
	INNER JOIN departments d ON (d.dept_id = e.dept_id)
	GROUP BY d.description;

---------------------
6)

	SELECT *, salary
	FROM employees
	WHERE salary < (
			SELECT MAX(salary) FROM employees
	) AND dept_id = 1

	ORDER BY salary DESC
	LIMIT 1;

-----------
7)

	SELECT *, RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) from employees e

-----------
8)

	SELECT *

	FROM departments d

	LEFT OUTER JOIN employees e ON e.dept_id = d.dept_id

	WHERE e.emp_id IS NULL

