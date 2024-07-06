import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int secretNumber = random.nextInt(100) + 1; // Generate random number between 1 and 100
        int guess;
        int attempts = 0;
        boolean correct = false;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("I have selected a number between 1 and 100. Try to guess it!");

        while (!correct) {
            System.out.print("Enter your guess: ");
            try {
                guess = scanner.nextInt();
            } catch (Exception e) {
                System.out.println("Invalid input. Please enter a valid integer.");
                scanner.next(); // Consume invalid input
                continue;
            }
            attempts++;

            if (guess < secretNumber) {
                System.out.println("Too low. The number is between " + (guess + 1) + " and 100. Try again.");
            } else if (guess > secretNumber) {
                System.out.println("Too high. The number is between 1 and " + (guess - 1) + ". Try again.");
            } else {
                correct = true;
                System.out.println("Congratulations! You've guessed the number " + secretNumber + " correctly in " + attempts + " attempts.");
            }
        }

        scanner.close(); // Closing the scanner to release resources
    }
}
