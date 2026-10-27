# Grading_System
import java.util.Scanner;

public class StudentGradeCalculator {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.println("==================================");
        System.out.println("      STUDENT GRADE CALCULATOR");
        System.out.println("==================================");

        int numberOfSubjects;

        while (true) {
            System.out.print("Enter the number of subjects: ");

            if (input.hasNextInt()) {
                numberOfSubjects = input.nextInt();

                if (numberOfSubjects > 0) {
                    break;
                }

                System.out.println("Please enter a number greater than zero.");
            } else {
                System.out.println("Invalid input. Please enter a whole number.");
                input.next();
            }
        }

        double totalMarks = 0.0;

        for (int i = 1; i <= numberOfSubjects; i++) {
            double marks;

            while (true) {
                System.out.print("Enter marks for subject " + i + " (0-100): ");

                if (input.hasNextDouble()) {
                    marks = input.nextDouble();

                    if (marks >= 0 && marks <= 100) {
                        break;
                    }

                    System.out.println("Marks must be between 0 and 100.");
                } else {
                    System.out.println("Invalid input. Please enter a number.");
                    input.next();
                }
            }

            totalMarks += marks;
        }

        double maximumMarks = numberOfSubjects * 100.0;
        double averagePercentage = (totalMarks / maximumMarks) * 100.0;

        String grade;

        if (averagePercentage >= 90) {
            grade = "A";
        } else if (averagePercentage >= 80) {
            grade = "B";
        } else if (averagePercentage >= 70) {
            grade = "C";
        } else if (averagePercentage >= 60) {
            grade = "D";
        } else {
            grade = "F";
        }

        System.out.println("\n========== RESULT ==========");
        System.out.println("Number of subjects : " + numberOfSubjects);
        System.out.printf("Total marks        : %.2f / %.2f%n",
                totalMarks, maximumMarks);
        System.out.printf("Average percentage : %.2f%%%n", averagePercentage);
        System.out.println("Grade              : " + grade);
        System.out.println("============================");

        input.close();
    }
}
