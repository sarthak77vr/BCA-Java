1.	Encapsulation is the bundling of data and methods that operate on the data into a single unit, called a class. It hides the internal state of an object from the outside world and only exposes the necessary functionality through well-defined interfaces. 
Create an Employee class having data members' Name, Eid, and Basic_Salary, to calculate the HRA is 20% of Basic Salary and DA is 25% of Basic salary and MA is 300 rupee. implement the following queries:
  a) Display the name and gross salary of an employee whose name starts With 'n'
  b).Display the Eid and gross salary whose Eid is equal to 107.
  c)  Count the total number of employees whose salary more than 20000/-



ans:-
import java.util.ArrayList;

class assignment {
    private String name;
    private int eid;
    private double basicSalary;

    public assignment(String name, int eid, double basicSalary) {
        this.name = name;
        this.eid = eid;
        this.basicSalary = basicSalary;
    }

    public String getName() {
        return name;
    }

    public int getEid() {
        return eid;
    }

    public double calculateGrossSalary() {
        double hra = 0.20 * basicSalary;
        double da = 0.25 * basicSalary;
        double ma = 300;
        return basicSalary + hra + da + ma;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Eid: " + eid + ", Gross Salary: " + calculateGrossSalary();
    }

    public static void displayEmployeeWithStartingLetter(ArrayList<assignment> employees, char startingLetter) {
        for (assignment emp : employees) {
            if (emp.getName().charAt(0) == startingLetter) {
                System.out.println(emp.getName() + ": " + emp.calculateGrossSalary());
            }
        }
    }

    public static void displayEmployeeWithEid(ArrayList<assignment> employees, int eid) {
        for (assignment emp : employees) {
            if (emp.getEid() == eid) {
                System.out.println("Eid: " + emp.getEid() + ", Gross Salary: " + emp.calculateGrossSalary());
            }
        }
    }

    public static int countEmployeesWithSalaryAbove(ArrayList<assignment> employees, double threshold) {
        int count = 0;
        for (assignment emp : employees) {
            if (emp.calculateGrossSalary() > threshold) {
                count++;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        ArrayList<assignment> employees = new ArrayList<>();
        employees.add(new assignment("Piyush", 101, 25000));
        employees.add(new assignment("RIYA", 102, 20000));
        employees.add(new assignment("nandini", 103, 30000));
        employees.add(new assignment("Sweta", 104, 22000));
        employees.add(new assignment("kartik", 105, 28000));
        employees.add(new assignment("sahil", 106, 35000));
        employees.add(new assignment("Nisha", 107, 21000));

        System.out.println("Employees whose name starts with 'N':");
        displayEmployeeWithStartingLetter(employees, 'N');

        System.out.println("\nEmployee with Eid 107:");
        displayEmployeeWithEid(employees, 107);

        System.out.println("\nTotal number of employees with salary more than 20000: " +
                countEmployeesWithSalaryAbove(employees, 20000));
    }
