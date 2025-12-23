using System;
using System.Collections.Generic;

// Employee class
class Employee
{
    public int Id { get; set; }
    public string Name { get; set; }
    public double Salary { get; set; }

    public Employee(int id, string name, double salary)
    {
        Id = id;
        Name = name;
        Salary = salary;
    }
}

class Program
{
    static void Main()
    {
        List<Employee> employees = new List<Employee>();
        int choice;

        do
        {
            Console.WriteLine("\n===== EMPLOYEE MENU =====");
            Console.WriteLine("1. Add Employee");
            Console.WriteLine("2. Update Employee Salary");
            Console.WriteLine("3. Delete Employee");
            Console.WriteLine("4. Display All Employees");
            Console.WriteLine("5. Exit");
            Console.Write("Enter choice: ");

            choice = Convert.ToInt32(Console.ReadLine());

            switch (choice)
            {
                case 1: // Add
                    Console.Write("Enter ID: ");
                    int id = Convert.ToInt32(Console.ReadLine());

                    Console.Write("Enter Name: ");
                    string name = Console.ReadLine();

                    Console.Write("Enter Salary: ");
                    double salary = Convert.ToDouble(Console.ReadLine());

                    employees.Add(new Employee(id, name, salary));
                    Console.WriteLine("Employee added successfully.");
                    break;

                case 2: // Update salary
                    Console.Write("Enter Employee ID to update salary: ");
                    int updateId = Convert.ToInt32(Console.ReadLine());

                    bool updated = false;
                    foreach (Employee emp in employees)
                    {
                        if (emp.Id == updateId)
                        {
                            Console.Write("Enter new salary: ");
                            emp.Salary = Convert.ToDouble(Console.ReadLine());
                            Console.WriteLine("Salary updated successfully.");
                            updated = true;
                            break;
                        }
                    }
                    if (!updated)
                        Console.WriteLine("Employee not found.");
                    break;

                case 3: // Delete
                    Console.Write("Enter Employee ID to delete: ");
                    int deleteId = Convert.ToInt32(Console.ReadLine());

                    Employee empToRemove = null;
                    foreach (Employee emp in employees)
                    {
                        if (emp.Id == deleteId)
                        {
                            empToRemove = emp;
                            break;
                        }
                    }

                    if (empToRemove != null)
                    {
                        employees.Remove(empToRemove);
                        Console.WriteLine("Employee deleted successfully.");
                    }
                    else
                    {
                        Console.WriteLine("Employee not found.");
                    }
                    break;

                case 4: // Display
                    Console.WriteLine("\n--- Employee List ---");
                    if (employees.Count == 0)
                    {
                        Console.WriteLine("No employees available.");
                    }
                    else
                    {
                        foreach (Employee emp in employees)
                        {
                            Console.WriteLine($"ID: {emp.Id}, Name: {emp.Name}, Salary: {emp.Salary}");
                        }
                    }
                    break;

                case 5:
                    Console.WriteLine("Exiting program...");
                    break;

                default:
                    Console.WriteLine("Invalid choice!");
                    break;
            }

        } while (choice != 5);
    }
}
