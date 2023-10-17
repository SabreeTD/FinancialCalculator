package com.pluralsight;
import java.util.Scanner;

public class Calculations {

        public static void main(String[] args) {
                Scanner scanner = new Scanner(System.in);

                while (true) {
                        System.out.println("Select an option:");
                        System.out.println("1. Mortgage Calculator");
                        System.out.println("2. Future Value Calculator");
                        System.out.println("3. Exit");

                        System.out.print("Enter your choice: ");
                        int choice = scanner.nextInt();

                        switch (choice) {
                                case 1:
                                        mortgageCalculator();
                                        break;
                                case 2:
                                        futureValueCalculator();
                                        break;
                                case 3:
                                        System.out.println("Goodbye!");
                                        System.exit(0);
                                default:
                                        System.out.println("Invalid choice. Please try again.");
                        }

                        System.out.println();
                }
        }

        public static void mortgageCalculator() {
                Scanner scanner = new Scanner(System.in);
// Retrieve loan Amount
                System.out.print("Enter the loan amount: ");
                double principal = scanner.nextDouble();
//Retrieve interest rate
                System.out.print("Enter the annual interest rate (%): ");
                double interestRate = scanner.nextDouble() / 100;
// Retrieve loan term
                System.out.print("Enter the loan term (in years): ");
                int loanTerm = scanner.nextInt();

                double monthlyInterestRate = interestRate / 12;
                int numPayments = loanTerm * 12;

                double mortgagePayment = principal * monthlyInterestRate * Math.pow(1 + monthlyInterestRate, numPayments);
                mortgagePayment /= Math.pow(1 + monthlyInterestRate, numPayments) - 1;

                System.out.printf("Monthly Mortgage Payment: %.2f\n", mortgagePayment);
        }

        public static void futureValueCalculator() {
                Scanner scanner = new Scanner(System.in);
// Retrieve Principal amount
                System.out.print("Enter the principal amount: ");
                double principal = scanner.nextDouble();
// Retrieve Interest Rate
                System.out.print("Enter the annual interest rate (%): ");
                double interestRate = scanner.nextDouble() / 100;

                System.out.print("Enter the number of compounding periods per year: ");
                int compoundingPeriods = scanner.nextInt();
// Retrieve years
                System.out.print("Enter the number of years: ");
                int numYears = scanner.nextInt();

                double futureValue = principal * Math.pow(1 + interestRate / compoundingPeriods, compoundingPeriods * numYears);

                System.out.printf("Future Value: %.2f\n", futureValue);
        }
}
