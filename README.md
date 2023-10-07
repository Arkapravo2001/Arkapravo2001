- 👋 Hi, I’m @Arkapravo2001
EmployeeController 

using Day36WebAPI.Model;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;
using System.Linq;

namespace Day36WebAPI.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class EmployeeController : ControllerBase
    {
        // Get all employees
        [HttpGet("GetEmps")]
        public ActionResult<IEnumerable<Employee>> GetEmps()
        {
            return Ok(EmpList.Employees);
        }

        // Get an employee by ID
        [HttpGet("GetEmp/{eid}")]
        public ActionResult<Employee> GetEmp(int eid)
        {
            var employee = EmpList.Employees.FirstOrDefault(e => e.Eid == eid);

            if (employee == null)
            {
                return NotFound();
            }

            return Ok(employee);
        }

        // Add a new employee
        [HttpPost("AddEmp")]
        public IActionResult AddEmp(Employee employee)
        {
            EmpList.Employees.Add(employee);
            return CreatedAtAction(nameof(GetEmp), new { eid = employee.Eid }, employee);
        }

        // Delete an employee by ID
        [HttpDelete("DelEmp/{eid}")]
        public IActionResult DelEmp(int eid)
        {
            var employee = EmpList.Employees.FirstOrDefault(e => e.Eid == eid);

            if (employee == null)
            {
                return NotFound();
            }

            EmpList.Employees.Remove(employee);
            return NoContent();
        }
    }
}




Emplist.cs
using System.Collections.Generic;

namespace Day36WebAPI.Model
{
    public class EmpList
    {
       


   
        public static List<Employee> Employees = new List<Employee>
    {
        new Employee { Eid = 1, Ename = "John", Esal = 50000, Eaddress = "123 Main St", Ephone = "555-1234" },
        new Employee { Eid = 2, Ename = "Jane", Esal = 60000, Eaddress = "456 Elm St", Ephone = "555-5678" },
        new Employee { Eid = 3, Ename = "Bob", Esal = 55000, Eaddress = "789 Oak St", Ephone = "555-9012" },
        new Employee { Eid = 4, Ename = "Alice", Esal = 70000, Eaddress = "101 Pine St", Ephone = "555-3456" },
        new Employee { Eid = 5, Ename = "Eva", Esal = 75000, Eaddress = "202 Cedar St", Ephone = "555-7890" }
    };
   

}
}

Employee.cs


public class Employee
{
    public int Eid { get; set; }
    public string Ename { get; set; }
    public decimal Esal { get; set; }
    public string Eaddress { get; set; }
    public string Ephone { get; set; }
}
- 
using System.Collections.Generic;
using System;
using System.Linq;

namespace Day33MVC.Models
{

    public class QuestionList
    {
        private List<Question> Questions { get; set; }

        public QuestionList()
        {
            // Initialize your list of questions (default 10 questions)
         
            Questions = new List<Question>
        {

                new Question()

            {
                QID = 1,
                Ques = "Which planet is known as the Red Planet?",
                Option1 = "Mars",
                Option2 = "Venus",
                Option3 = "Jupiter",
                Option4 = "Saturn",
                Ans = "Mars"
            },

            new Question() 

            {
                QID = 2,
                Ques = "Which planet is known as the Red Planet?",
                Option1 = "Mars",
                Option2 = "Venus",
                Option3 = "Jupiter",
                Option4 = "Saturn",
                Ans = "Mars"
            },
            new Question()
            {
                QID = 3,
                Ques = "Which planet is known as the Red Planet?",
                Option1 = "Mars",
                Option2 = "Venus",
                Option3 = "Jupiter",
                Option4 = "Saturn",
                Ans = "Mars"
            },
         
            // Add more default questions here as needed
        };
        }
        

        public List<Question> Get3Questions()
            {
                Random random = new Random();
                // Get random 3 questions from the Questions list
                var randomQuestions = Questions.OrderBy(q => random.Next()).Take(3).ToList();
                return randomQuestions;
            }

            public string GetAns(int QID)
            {
                // Find the question by QID and return the answer
                var question = Questions.FirstOrDefault(q => q.QID == QID);
                if (question != null)
                {
                    return question.Ans;
                }
                else
                {
                    return null; // Handle the case where the question with given QID is not found
                }
            }
        }
    }






public class QuestionList
{
    private List<Question> Questions { get; set; }

    public QuestionList()
    {
        // Initialize your list of questions (default 10 questions)
        Questions = new List<Question>
        {
            new Question
            {
                QID = 1,
                Ques = "What is the capital of France?",
                Option1 = "London",
                Option2 = "Paris",
                Option3 = "Berlin",
                Option4 = "Madrid",
                Ans = "Paris"
            },
            new Question
            {
                QID = 2,
                Ques = "Which planet is known as the Red Planet?",
                Option1 = "Mars",
                Option2 = "Venus",
                Option3 = "Jupiter",
                Option4 = "Saturn",
                Ans = "Mars"
            },
            // Add more default questions here as needed
        };
    }

    // Rest of your methods (Get3Questions, GetAns) go here
}

public class QuestionList
{
    private List<Question> Questions { get; set; }

    public QuestionList()
    {
        // Initialize your list of questions (default 10 questions)
        Questions = new List<Question>
        {
            // Add your default 10 questions here
        };
    }

    public List<Question> Get3Questions()
    {
        Random random = new Random();
        // Get random 3 questions from the Questions list
        var randomQuestions = Questions.OrderBy(q => random.Next()).Take(3).ToList();
        return randomQuestions;
    }

    public string GetAns(int QID)
    {
        // Find the question by QID and return the answer
        var question = Questions.FirstOrDefault(q => q.QID == QID);
        if (question != null)
        {
            return question.Ans;
        }
        else
        {
            return null; // Handle the case where the question with given QID is not found
        }
    }
}

public class Question
{
    public int QID { get; set; }
    public string Ques { get; set; }
    public string Option1 { get; set; }
    public string Option2 { get; set; }
    public string Option3 { get; set; }
    public string Option4 { get; set; }
    public string Ans { get; set; }
}


Exercise: 
Model:
Question class (QID, Ques, Option1, Option2, Option3, Option4, Ans )
QuestionList : 
Questions: by default has a list of 10 Questions
List<Question> Get3Questions(){ returns random 3 questions from Questions}
String getAns(Qid) -> returns the ans from Questions
  
package pkg4;

public class Permission {
	public int  permission_id;
	public int  permission_role_id;
	public String permission_title;
	public String permission_module;
	public String permission_description;
	
	public void addPermision() {
		System.out.println("Permission Granted");
	}
	public void editPermision() {
		System.out.println("Permission Edited");
	}
	public void deletePermision() {
		System.out.println("Permission Deleted");
	}
	public void searchpermision() {
		System.out.println("Search Permission");
	}
}
package pkg4;

public class Role {
	public int  role_id;
	public String role_title;
	public String role_description;
	
	public void addRole() {
		System.out.println("Add Role");
	}
	public void editRole() {
		System.out.println("Edit Role");
	}
	public void deleteRole() {
		System.out.println("Delete Role");
	}
	public void searchRole() {
		System.out.println("Search Role");
	}
	public void assignRole() {
		System.out.println("Assign Role");
}
}
package pkg4;

import java.util.Date;

interface Per{
	public void addPermision();
	public void editPermision();
	public void deletePermision();
	public void searchpermision();
}
interface Rol{
	public void addRole();
	public void editRole();
	public void deleteRole();
	public void searchRole();
	public void assignRole();
}
public class User implements Per,Rol{
	public int userid;
	public int userroleid;
	public String username;
	public String useremail;
	public Date userdob;
	public String address;
	
	

	@Override
	public void addRole() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void editRole() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void deleteRole() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void searchRole() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void assignRole() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void addPermision() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void editPermision() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void deletePermision() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void searchpermision() {
		// TODO Auto-generated method stub
		
	}
	public void addUser() {
		System.out.println("User added");
	}
	public void editUser() {
		System.out.println("User edited");
	}
	public void deleteUser() {
		System.out.println("User Deleted");
	}
	public void searchUser() {
		System.out.println("Search User");
	}
}
package pkg4;

import java.util.Date;

public class Holidays {
	public int holidayid;
	public int holidayempid;
    public String holidaydur;
    public String holidaydesc;
    public Date holidaydate;
    Permission Per;
    public void addHolidays() {
		System.out.println("Add Holidays");
	}
	public void editHolidays() {
		System.out.println("Edit Holidays");
	}
	public void deleteHolidays() {
		System.out.println("Delete Holidays");
	}
	public void searchHolidays() {
		System.out.println("Search Holidays");
	}
	

}
package pkg4;



public class Attendance {
	
		public int attendanceid;
		public int attendanceempid;
	    public int attendancestudentid;
	    public String attendancetype;
	    public String attendancedesc;
	    Permission Per;
	    public void addAttendance() {
			System.out.println("Add Attendance");
		}
		public void editAttendance() {
			System.out.println("Edit Attendance");
		}
		public void deleteAttendance() {
			System.out.println("Delete Attendance");
		}
		public void searchAttendance() {
			System.out.println("Search Attendance");
		}
}
package pkg4;


public class Salary {

	public int salaryid;
	public int salaryempid;
    public String salarytype;
    public String salarytotal;
    public String salaryamt;
    public String salarydesc;
    Permission Per;
    public void addSalary() {
		System.out.println("Add Salary");
	}
	public void editSalary() {
		System.out.println("Edit Salary");
	}
	public void deleteSalary() {
		System.out.println("Delete Salary");
	}
	public void searchSalary() {
		System.out.println("Search Salary");
	}

}
package pkg4;



public class Employees {
	public int employeeid;
	public String employeeaddress;
    public String employeename;
    public String employeemob;
    public String employeeemail;
    public String employeeusername;
    public String employeepassword;
    Permission Per;
    public void addEmployee() {
		System.out.println("Add Employee");
	}
	public void editEmployee() {
		System.out.println("Edit Employee");
	}
	public void deleteEmployee() {
		System.out.println("Delete Employee");
	}
	public void searchEmployee() {
		System.out.println("Search Employee");
	}
	
}
package pkg4;

public class Leave {
	public int leaveid;
	public int leaveempid;
    public String leavetype;
    public String leavestatus;
    public String leaveto;
    public String leavefrom;
    public String leavedesc;
    Permission Per;
    public void addLeave() {
		System.out.println("Add Leave");
	}
	public void editLeave() {
		System.out.println("Edit Leave");
	}
	public void deleteLeave() {
		System.out.println("Delete Leave");
	}
	public void searchLeave() {
		System.out.println("Search Leave");
	}

}


<!DOCTYPE html>
<html lang = "en">
<head>
<title>JavaScript Calculator</title>
<style>
    h1{
        text-align:center;
        padding:23px;
        background: color #ecf0ec;
        color:red;
    }
    #clear{
        width:500 px;
        color:white;
        border:3px solid red;
        border-radius:3px;
        padding:20px;
        background-color:black;
    }
    .formstyle
    {
        width:300px;
        height:530px;
        margin:auto;
        border:3px solid red
    }
    
    input
    {
     width:20px;
     background-color:black;
     color:white;
     border:3px solid red;
     border-radius:5 px;
     padding:26px;
     margin:5px;
     font-size:15px;
    }

    #calc{
        width:250px;
        border:5px solid red;
        border-radius:3px;
        padding:20px;
        margin:auto;
    }
</style>
    </head>
    <body>
        <h1>Calculator In JavaScript</h1>
        <div class="formstyle">
        <form name="form9">
        <input id="calc" type="text" name="answer"><br><br>
        <input type="button" value="DEl" onclick="form9.answer.value=form9.answer.value.slice(0,-1)">
        <input type="button" value="7" onclick="form9.answer.value+='7'">
        <input type="button" value="8" onclick="form9.answer.value+='8'">
        <input type="button" value="9" onclick="form9.answer.value+='9'">
        <input type="button" value="+" onclick="form9.answer.value+='+'">
        <input type="button" value="4" onclick="form9.answer.value+='4'">
        <input type="button" value="5" onclick="form9.answer.value+='5'">
        <input type="button" value="6" onclick="form9.answer.value+='6'">
        <input type="button" value="-" onclick="form9.answer.value+='-'">
        <input type="button" value="1" onclick="form9.answer.value+='1'">
        <input type="button" value="2" onclick="form9.answer.value+='2'">
        <input type="button" value="3" onclick="form9.answer.value+='3'">
        <input type="button" value="*" onclick="form9.answer.value+='*'">
        <input type="button" value="/" onclick="form9.answer.value+='/'">
        <input type="button" value="0" onclick="form9.answer.value+='0'">
        <input type="button" value="." onclick="form9.answer.value+='.'">
        <input type="button" value="=" onclick="form9.answer.value=eval(form9.answer.value)">
        
        <input type="button" value="Clr" onclick="form9.answer.value=''"id="clear">
        <br>

        </form>
        </div>
    </body>
</html>


using System;
namespace Prj1Day1Con
{
    public interface ImyIterator
    {
        int next();
        bool hasNext();
        void begin();
    }
    public class myCollection
    {
        private int[] arr = new int[10000];
        private int tos = -1;
        private int nav = -1;
        public void add(int i)
        {
            tos = tos + 1;
            arr[tos] = i;
        }
        public class myIterator : ImyIterator
        {
            private myCollection collection;
            public myIterator(myCollection collection)
            {
                this.collection = collection;
            }
           
            public void begin()
            {
                if (collection.tos > 0)
                    collection.nav = 0;
            }
            public bool hasNext()
            {
                return collection.nav <= collection.tos;
            }
            public int next()
            {
                if (collection.nav <= collection.tos && collection.tos != -1)
                {
                    int value = collection.arr[collection.nav];
                    collection.nav++;
                    return value;
                }
                return -1;
            }
        }
        public myIterator GetIterator()
        {
            return new myIterator(this);
        }
    }
    internal class AbstractEx
    {
        static void Main(string[] args)
        {
            myCollection c1 = new myCollection();
            
            c1.add(10);
            c1.add(203);
            c1.add(9);
            c1.add(49);
            c1.add(100);
            ImyIterator it = c1.GetIterator();
            it.begin();
            while (it.hasNext())
            {
                int val = it.next();
                if (val != -1)
                {
                    Console.WriteLine("Current Element is "+val);
                }
                else Console.WriteLine("No more elements to iterate");
            }
        }
    }
}

using System;
using System.IO;

class Program
{
    static void Main(string[] args)
    {
        while (true)
        {
            Console.WriteLine("\nMain Menu:");
            Console.WriteLine("1. Using File");
            Console.WriteLine("2. Using FileStream");
            Console.WriteLine("3. Using StreamReader and StreamWriter");
            Console.WriteLine("4. Exit");

            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    FileMenu();
                    break;
                case "2":
                    FileStreamMenu();
                    break;
                case "3":
                    StreamReaderStreamWriterMenu();
                    break;
                case "4":
                    return;
                default:
                    Console.WriteLine("Invalid choice. Please select a valid option.");
                    break;
            }
        }
    }

    static void FileMenu()
    {
        string filePath = "file.txt";
        string[] fileContent = new string[0];

        while (true)
        {
            Console.WriteLine("\nFile Menu:");
            Console.WriteLine("1. Write to File");
            Console.WriteLine("2. Read from File");
            Console.WriteLine("3. Go to Main Menu");

            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    Console.WriteLine("Enter text to write to the file (type 'done' to stop):");
                    string input = Console.ReadLine();
                    while (!input.ToLower().Equals("done"))
                    {
                        Array.Resize(ref fileContent, fileContent.Length + 1);
                        fileContent[fileContent.Length - 1] = input;
                        input = Console.ReadLine();
                    }

                    File.WriteAllLines(filePath, fileContent);
                    Console.WriteLine("Text written to file.");
                    break;
                case "2":
                    try
                    {
                        string[] lines = File.ReadAllLines(filePath);
                        Console.WriteLine("Number of words: " + CountWords(lines));
                        Console.WriteLine("File Content:");
                        foreach (string line in lines)
                        {
                            Console.WriteLine(line);
                        }
                    }
                    catch (FileNotFoundException)
                    {
                        Console.WriteLine("File not found. Please write to the file first.");
                    }
                    break;
                case "3":
                    return;
                default:
                    Console.WriteLine("Invalid choice. Please select a valid option.");
                    break;
            }
        }
    }

    static int CountWords(string[] lines)
    {
        int wordCount = 0;
        foreach (string line in lines)
        {
            string[] words = line.Split(new char[] { ' ' }, StringSplitOptions.RemoveEmptyEntries);
            wordCount += words.Length;
        }
        return wordCount;
    }

    static void FileStreamMenu()
    {
        // Implement FileStream functionality here
    }

    static void StreamReaderStreamWriterMenu()
    {
        // Implement StreamReader and StreamWriter functionality here
    }
}
using System;
using System.IO;

class Program
{
    static void Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: program.exe <filename.cs>");
            return;
        }

        string fileName = args[0];

        if (!File.Exists(fileName))
        {
            Console.WriteLine("File not found.");
            return;
        }

        if (Path.GetExtension(fileName).ToLower() != ".cs")
        {
            Console.WriteLine("Invalid file extension. Only .cs files are supported.");
            return;
        }

        string fileContents = File.ReadAllText(fileName);

        if (fileContents.Contains("Main(string[] args)") || fileContents.Contains("Main()"))
        {
            string newFileName = Path.GetFileNameWithoutExtension(fileName);
            string newFileExtension = ".myexe";
            
            if (!fileContents.Contains("Main(string[] args)"))
            {
                newFileExtension = ".mydll";
            }

            string newFilePath = newFileName + newFileExtension;
            
            File.WriteAllText(newFilePath, fileContents);

            Console.WriteLine("Compiled successfully. Output file: " + newFilePath);
        }
        else
        {
            Console.WriteLine("Main function not found. Compilation aborted.");
        }
    }
}

using System;
using System.IO;

class Program
{
    static void Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: program.exe <filename.cs>");
            return;
        }

        string fileName = args[0];

        if (!File.Exists(fileName))
        {
            Console.WriteLine("File not found.");
            return;
        }

        if (Path.GetExtension(fileName).ToLower() != ".cs")
        {
            Console.WriteLine("Invalid file extension. Only .cs files are supported.");
            return;
        }

        string fileContents = File.ReadAllText(fileName);

        if (fileContents.Contains("Main(string[] args)") || fileContents.Contains("Main()"))
        {
            string newFileName = Path.GetFileNameWithoutExtension(fileName);
            string newFileExtension = ".myexe";
            
            if (!fileContents.Contains("Main(string[] args)"))
            {
                newFileExtension = ".mydll";
            }

            string newFilePath = newFileName + newFileExtension;
            
            File.WriteAllText(newFilePath, fileContents);

            Console.WriteLine("Compiled successfully. Output file: " + newFilePath);
        }
        else
        {
            Console.WriteLine("Main function not found. Compilation aborted.");
        }
    }
}

[16/09, 14:20] Arkapravo Ganguly: using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        Console.WriteLine("Start of Main");

        // Start two asynchronous tasks
        Task task1 = PrintNumbersAsync("Task 1", 5);
        Task task2 = PrintNumbersAsync("Task 2", 5);

        // Wait for both tasks to complete
        await Task.WhenAll(task1, task2);

        Console.WriteLine("End of Main");
    }

    static async Task PrintNumbersAsync(string taskName, int count)
    {
        for (int i = 1; i <= count; i++)
        {
            Console.WriteLine($"{taskName}: {i}");
            await Task.Delay(100); // Simulate some asynchronous work
        }
    }
}
[16/09, 14:20] Arkapravo Ganguly: using System;
using System.Threading;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Start of Main");

        // Create and start two threads
        Thread thread1 = new Thread(() => PrintNumbers("Thread 1", 5));
        Thread thread2 = new Thread(() => PrintNumbers("Thread 2", 5));

        thread1.Start();
        thread2.Start();

        // Wait for both threads to complete
        thread1.Join();
        thread2.Join();

        Console.WriteLine("End of Main");
    }

    static void PrintNumbers(string threadName, int count)
    {
        for (int i = 1; i <= count; i++)
        {
            Console.WriteLine($"{threadName}: {i}");
            Thread.Sleep(100); // Simulate some work
        }
    }
}
using System;
using System.Collections.Generic;
using System.Threading.Tasks;

class Program
{
    static void Main()
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

        // Use TLP to calculate the square of each number concurrently
        Parallel.ForEach(numbers, num =>
        {
            int square = num * num;
            Console.WriteLine($"The square of {num} is {square}");
        });

        Console.ReadLine();
    }
}
CREATE FUNCTION ChkPrime (@num INT)
RETURNS NVARCHAR(50)
AS
BEGIN
    DECLARE @result NVARCHAR(50)
    DECLARE @is_prime INT
    SET @is_prime = 1
    
    IF @num < 2
    BEGIN
        SET @result = 'Not Prime'
    END
    ELSE
    BEGIN
        DECLARE @i INT
        SET @i = 2
        WHILE @i <= SQRT(@num)
        BEGIN
            IF @num % @i = 0
            BEGIN
                SET @is_prime = 0
                BREAK
            END
            SET @i = @i + 1
        END
        
        IF @is_prime = 1
        BEGIN
            IF @num % 2 = 0
                SET @result = 'Even Prime'
            ELSE
                SET @result = 'Odd Prime'
        END
        ELSE
        BEGIN
            IF @num % 2 = 0
                SET @result = 'Even'
            ELSE
                SET @result = 'Odd'
        END
    END
    
    RETURN @result
END

CREATE PROCEDURE PrintNumbersDescending
(
    @startNumber INT
)
AS
BEGIN
    IF @startNumber <= 0
    BEGIN
        PRINT 'Input number must be greater than 0.';
        RETURN;
    END
    
    DECLARE @currentNumber INT = @startNumber;
    
    WHILE @currentNumber >= 1
    BEGIN
        PRINT @currentNumber;
        SET @currentNumber = @currentNumber - 1;
    END
END;
using System;
using System.Data.SqlClient;

namespace LoginApp
{
    class Program
    {
        static void Main(string[] args)
        {
            string connectionString = "Your_Connection_String_here"; // Replace with your SQL Server connection string

            Console.Write("Enter username: ");
            string username = Console.ReadLine();

            Console.Write("Enter password: ");
            string password = Console.ReadLine();

            bool loginSuccessful = CheckLogin(connectionString, username, password);

            if (loginSuccessful)
            {
                Console.WriteLine("Login successful");
            }
            else
            {
                Console.WriteLine("Login NOT successful");
            }
        }

        static bool CheckLogin(string connectionString, string username, string password)
        {
            using (SqlConnection connection = new SqlConnection(connectionString))
            {
                connection.Open();

                string query = "SELECT COUNT(*) FROM Login WHERE uname = @uname AND passwd = @passwd";
                using (SqlCommand command = new SqlCommand(query, connection))
                {
                    command.Parameters.AddWithValue("@uname", username);
                    command.Parameters.AddWithValue("@passwd", password);

                    int count = (int)command.ExecuteScalar();

                    return count > 0;
                }
            }
        }
    }
}

using System.Collections.Generic;
using System;

namespace Day30MVC.Models
{
    public class EmployeeList
    {
        public List<Employee> emps = new List<Employee>();
        public EmployeeList(List<Employee> emps) { this.emps = emps; }
        public EmployeeList(Employee emp) { this.emps.Add(emp); }
        public EmployeeList()
        {
            this.AddEmp(new Employee("abc", 101));
            this.AddEmp(new Employee("xyz", 102));
            this.AddEmp(new Employee("abcxyz", 103));
        }
        public void AddEmp(Employee emp) { this.emps.Add(emp); }
        public void DispEmp()
        {
            foreach (Employee e in emps)
            {
                Console.WriteLine(e);
            }
        }
        public Employee getEmp(string name)
        {
            Employee e = new Employee("default", 100);
            foreach (Employee ee in emps)
            {
                if (ee.name.Equals(name))
                {
                    e = ee;
                }
            }
            
            Employee e2 = emps.Find(ee => ee.name.Equals(name));
            return e;
        }
    }
}

Provide a Menu with buttons for : Add a new Student, Update an existing student, delete an existing Student, display the list of students, search a student according to Id, Search the group of students according to criteria as mentioned below.

Prepare an MVC project for Student class and StdList class
Add Views which submits a new Student data to the controller of Student which adds student data to the list of stds and returns the fresh list in JSON format.
Provide link to each page in each view
Student{id, name, course, duration in years, year of enrollment, fees}
Provide search according to ID, course, name, duration, year, fees range.

@model List<Employee>

<h2>Search Results</h2>

@if (Model.Count == 0)
{
    <p>No results found.</p>
}
else
{
    <table class="table">
        <thead>
            <tr>
                <th>Name</th>
                <th>ID</th>
            </tr>
        </thead>
        <tbody>
            @foreach (var employee in Model)
            {
                <tr>
                    <td>@employee.name</td>
                    <td>@employee.ID</td>
                </tr>
            }
        </tbody>
    </table>
}

Login Id and password : pair of data (login form)
Being maintained for all the logged in pages.
Page 1: Login Page  : Next button take us to Inbox
Hidden step/action: Saves the cookies: either the data given by client or empty string(none of the cookies are null), redirects to Inbox page
Page 2: Inbox Page: 
If the cookies are present :
Just a table full of scratch messages
A link to Inbox page, Draft page, Sent page, Compose page
A link to logout
Else Inbox page should be empty with link to login page
Page 3-5: Compose Page / Draft page / Sent page:
If the cookies are present :
Just a table full of scratch data
A link to Inbox page, Draft page, Sent page, Compose page
A link to logout 
Else the pages should be empty with link to login page
Page 6 : Logout page:
Refresh the cookie for login credentials and delete the username and password
Provide a link to login page


public class User
{
    public string Username { get; set; }
    public string Password { get; set; }
}

public static class UserRepository
{
    private static List<User> users = new List<User>
    {
        new User { Username = "user1", Password = "password1" }
    };

    public static User GetUser(string username)
    {
        return users.FirstOrDefault(u => u.Username == username);
    }
}


using System.Collections.Generic;
using System;

namespace Day30MVC.Models
{
    public class EmployeeList
    {
        public List<Employee> emps = new List<Employee>();
        public EmployeeList(List<Employee> emps) { this.emps = emps; }
        public EmployeeList(Employee emp) { this.emps.Add(emp); }
        public EmployeeList()
        {
            this.AddEmp(new Employee("abc", 101));
            this.AddEmp(new Employee("xyz", 102));
            this.AddEmp(new Employee("abcxyz", 103));
        }
        public void AddEmp(Employee emp) { this.emps.Add(emp); }
        public void DispEmp()
        {
            foreach (Employee e in emps)
            {
                Console.WriteLine(e);
            }
        }
        public Employee getEmp(string name)
        {
            Employee e = new Employee("default", 100);
            foreach (Employee ee in emps)
            {
                if (ee.name.Equals(name))
                {
                    e = ee;
                }
            }

            Employee e2 = emps.Find(ee => ee.name.Equals(name));
            return e;
        }
    }
}
namespace Day30MVC.Models
{
    public class Employee
    {
        public string name { get; set; }
        public int id { get; set; }

        public Employee(string name, int id)
        {
            this.name = name;
            this.id = id;
        }

        public Employee() { }

        public override string ToString()
        {
            return "\nEmp: " + name + " with id: " + id;
        }
    }
}
using Day30MVC.Models;
using Microsoft.AspNetCore.Mvc;

namespace Day30MVC.Controllers
{
    public class EmployeeController : Controller
    {
        EmployeeList emps = new EmployeeList();
        public IActionResult Index()
        {
            return View();
        }
        public IActionResult WelcomeEmp(string name)
        {
            TempData["Emp"] = emps.getEmp(name);
            return View();
        }
        public IActionResult WelcomeEmp2(string name)
        {
            TempData["EmpName"] = name;
            return View();
        }
        public IActionResult ListEmp()
        {
            return View(emps.emps);
        }

        public JsonResult ListEmp2()
        {
            return Json(emps.emps);
        }

    }
}

using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;

public class MCQController : Controller
{
    public IActionResult Index()
    {
        return View();
    }

    [HttpPost]
    public IActionResult StartTest(string name)
    {
        // Initialize cookies for questions
        Response.Cookies.Append("01", "0");
        Response.Cookies.Append("02", "0");
        Response.Cookies.Append("03", "0");

        // Redirect to the first question
        return RedirectToAction("MCQ1");
    }

    public IActionResult MCQ1()
    {
        return View();
    }

    [HttpPost]
    public IActionResult MCQ1(string ans)
    {
        if (Request.Cookies["01"] == "0" && ans == "mo")
        {
            Response.Cookies.Append("01", "10");
        }
        return RedirectToAction("MCQ2");
    }

    public IActionResult MCQ2()
    {
        return View();
    }

    [HttpPost]
    public IActionResult MCQ2(string ans)
    {
        if (Request.Cookies["02"] == "0" && ans == "Cool")
        {
            Response.Cookies.Append("02", "10");
        }
        return RedirectToAction("MCQ3");
    }

    public IActionResult MCQ3()
    {
        return View();
    }

    [HttpPost]
    public IActionResult MCQ3(string ans)
    {
        if (Request.Cookies["03"] == "0" && ans == "Yes")
        {
            Response.Cookies.Append("03", "10");
        }
        return RedirectToAction("MCQ4");
    }

    public IActionResult MCQ4()
    {
        return View();
    }

    [HttpPost]
    public IActionResult MCQ4(string ans)
    {
        if (Request.Cookies["04"] == "0" && ans == "No")
        {
            Response.Cookies.Append("04", "10");
        }
        return RedirectToAction("Result");
    }

    public IActionResult Result()
    {
        // Convert cookie values to integers and calculate the result
        int result = int.Parse(Request.Cookies["01"]) + int.Parse(Request.Cookies["02"]) + int.Parse(Request.Cookies["03"]) + int.Parse(Request.Cookies["04"]);
        ViewData["res"] = result;

        return View();
    }
}
