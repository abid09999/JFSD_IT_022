import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// Interface defining employee operations
interface EmployeeOperations {
    void addEmployee(Employee employee);
    void updateSalary(int employeeID, double newSalary);
    Employee viewEmployeeDetails(int employeeID);
    List<Employee> listEmployees();
}

// Abstract class representing an Employee
abstract class Employee {
    protected int employeeID;
    protected String name;
    protected String designation;
    protected double salary;

    public Employee(int employeeID, String name, String designation, double salary) {
        this.employeeID = employeeID;
        this.name = name;
        this.designation = designation;
        this.salary = salary;
    }

    public int getEmployeeID() {
        return employeeID;
    }

    public String getName() {
        return name;
    }

    public String getDesignation() {
        return designation;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }

    public void displayDetails() {
        System.out.println("Employee ID: " + employeeID);
        System.out.println("Name: " + name);
        System.out.println("Designation: " + designation);
        System.out.println("Salary: $" + salary);
        System.out.println("-------------------------");
    }
}

// Concrete class implementing EmployeeOperations
class EmployeeManager implements EmployeeOperations {
    private List<Employee> employees = new ArrayList<>();

    @Override
    public void addEmployee(Employee employee) {
        employees.add(employee);
        System.out.println("Employee added successfully.");
    }

    @Override
    public void updateSalary(int employeeID, double newSalary) {
        for (Employee emp : employees) {
            if (emp.getEmployeeID() == employeeID) {
                emp.setSalary(newSalary);
                System.out.println("Salary updated successfully.");
                return;
            }
        }
        System.out.println("Employee not found.");
    }

    @Override
    public Employee viewEmployeeDetails(int employeeID) {
        for (Employee emp : employees) {
            if (emp.getEmployeeID() == employeeID) {
                return emp;
            }
        }
        return null;
    }

    @Override
    public List<Employee> listEmployees() {
        return employees;
    }
}

// Main class for user interaction
public class EmployeeManagementSystem {
    public static void main(String[] args) {
        EmployeeManager manager = new EmployeeManager();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Employee Management System");
            System.out.println("1. Add Employee");
            System.out.println("2. Update Salary");
            System.out.println("3. View Employee Details");
            System.out.println("4. List Employees");
            System.out.println("5. Exit");
            System.out.print("Choose an option: ");

            int choice = scanner.nextInt();
            switch (choice) {
                case 1:
                    System.out.print("Enter Employee ID: ");
                    int id = scanner.nextInt();
                    scanner.nextLine(); // Consume newline
                    System.out.print("Enter Name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter Designation: ");
                    String designation = scanner.nextLine();
                    System.out.print("Enter Salary: ");
                    double salary = scanner.nextDouble();
                    
                    Employee employee = new Employee(id, name, designation, salary) {}; // Anonymous class for abstract Employee
                    manager.addEmployee(employee);
                    break;
                case 2:
                    System.out.print("Enter Employee ID to update salary: ");
                    int empID = scanner.nextInt();
                    System.out.print("Enter new Salary: ");
                    double newSalary = scanner.nextDouble();
                    manager.updateSalary(empID, newSalary);
                    break;
                case 3:
                    System.out.print("Enter Employee ID to view details: ");
                    int viewID = scanner.nextInt();
                    Employee emp = manager.viewEmployeeDetails(viewID);
                    if (emp != null) {
                        emp.displayDetails();
                    } else {
                        System.out.println("Employee not found.");
                    }
                    break;
                case 4:
                    List<Employee> employees = manager.listEmployees();
                    if (employees.isEmpty()) {
                        System.out.println("No employees found.");
                    } else {
                        for (Employee e : employees) {
                            e.displayDetails();
                        }
                    }
                    break;
                case 5:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice, please try again.");
            }
        }
    }
}
