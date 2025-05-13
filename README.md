import java.util.Scanner;

public class ATM {
    private double balance;
    private final String correctPIN = "1234";

    public void start() {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your PIN: ");
        String enteredPIN = scanner.nextLine();

        if (!enteredPIN.equals(correctPIN)) {
            System.out.println("Invalid PIN. Access denied.");
            return;
        }

        int choice;
        do {
            System.out.println("\n=== ATM MENU ===");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    checkBalance();
                    break;
                case 2:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    withdraw(withdrawAmount);
                    break;
                case 4:
                    System.out.println("Thank you for using our ATM!");
                    break;
                default:
                    System.out.println("Invalid choice. Try again.");
            }

        } while (choice != 4);
        scanner.close();
    }

    private void checkBalance() {
        System.out.printf("Your balance is: ₹%.2f%n", balance);
    }

    private void deposit(double amount) {
        if (amount <= 0) {
            System.out.println("Deposit amount must be positive.");
        } else {
            balance += amount;
            System.out.printf("Successfully deposited ₹%.2f%n", amount);
        }
    }

    private void withdraw(double amount) {
        if (amount <= 0) {
            System.out.println("Withdrawal amount must be positive.");
        } else if (amount > balance) {
            System.out.println("Insufficient balance.");
        } else {
            balance -= amount;
            System.out.printf("Successfully withdrew ₹%.2f%n", amount);
        }
    }
}
