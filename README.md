- 👋 Hi, I’m @Arkapravo2001
  
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

