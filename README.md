import java.util.Scanner;

class Student {
    private String name;
    private int rollNumber;
    private double[] marks;
    private static final int SUBJECT_COUNT = 5;

    public Student(String name, int rollNumber, double[] marks) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.marks = marks;
    }

    public double calculateAverage() {
        double total = 0;
        for (double mark : marks) {
            total += mark;
        }
        return total / SUBJECT_COUNT;
    }

    public String calculateGrade() {
        double average = calculateAverage();
        if (average >= 90) {
            return "A";
        } else if (average >= 75) {
            return "B";
        } else if (average >= 50) {
            return "C";
        } else {
            return "F";
        }
    }

    public void displayDetails() {
        System.out.println("\nStudent Details:");
        System.out.println("Name: " + name);
        System.out.println("Roll Number: " + rollNumber);
        System.out.println("Marks: ");
        for (int i = 0; i < marks.length; i++) {
            System.out.println("Subject " + (i + 1) + ": " + marks[i]);
        }
        System.out.println("Average Marks: " + calculateAverage());
        System.out.println("Grade: " + calculateGrade());
    }
}

public class GradeCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter student name: ");
        String name = scanner.nextLine();

        System.out.print("Enter roll number: ");
        int rollNumber = scanner.nextInt();

        double[] marks = new double[5];
        System.out.println("Enter marks for 5 subjects:");
        for (int i = 0; i < 5; i++) {
            System.out.print("Subject " + (i + 1) + ": ");
            marks[i] = scanner.nextDouble();
        }

        Student student = new Student(name, rollNumber, marks);

        student.displayDetails();

        scanner.close();
    }
}
