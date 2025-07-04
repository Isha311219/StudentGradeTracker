# StudentGradeTracker
       Build a Java program to input and manage student grades.
● Calculate average, highest, and lowest scores.
● Used arrays or ArrayLists to store and manage data.
● Display a summary report of all students.
● The interface is console-based or GUI-based as desired.


Student.java

public class Student {
    private String name;
    private int score;

    public Student(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public int getScore() {
        return score;
    }
}


GradeTracker.java

import java.util.ArrayList;
import java.util.Scanner;

public class GradeTracker {
    public static void main(String[] args) {
        System.out.println("Hello from GradeTracker!");
        Scanner scanner = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        System.out.println("=== Student Grade Tracker ===");

        while (true) {
            System.out.print("Enter student name (or type 'done'): ");
            String name = scanner.nextLine();
            if (name.equalsIgnoreCase("done")) break;

            System.out.print("Enter score for " + name + ": ");
            int score = Integer.parseInt(scanner.nextLine());

            students.add(new Student(name, score));
        }

        if (students.isEmpty()) {
            System.out.println("No student data entered.");
            return;
        }

        int total = 0;
        int highest = Integer.MIN_VALUE;
        int lowest = Integer.MAX_VALUE;
        Student topStudent = null;
        Student lowStudent = null;

        System.out.println("\n--- Student Report ---");
        for (Student s : students) {
            int score = s.getScore();
            total += score;

            if (score > highest) {
                highest = score;
                topStudent = s;
            }

            if (score < lowest) {
                lowest = score;
                lowStudent = s;
            }

            System.out.println(s.getName() + ": " + s.getScore());
        }

        double average = (double) total / students.size();
        System.out.println("\nAverage Score: " + average);
        System.out.println("Highest Score: " + topStudent.getName() + " (" + highest + ")");
        System.out.println("Lowest Score: " + lowStudent.getName() + " (" + lowest + ")");
    }
}

