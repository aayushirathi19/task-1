import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int roundsWon = 0;

        System.out.println("🎮 Welcome to the Number Guessing Game!");

        boolean playAgain = true;
        while (playAgain) {
            int targetNumber = random.nextInt(100) + 1; // Random number from 1 to 100
            int maxAttempts = 7;
            int attempts = 0;
            boolean isCorrect = false;

            System.out.println("\n🎯 I have selected a number between 1 and 100. Can you guess it?");
            System.out.println("💡 You have " + maxAttempts + " attempts.");

            while (attempts < maxAttempts) {
                System.out.print("👉 Enter your guess: ");
                int guess = scanner.nextInt();
                attempts++;

                if (guess == targetNumber) {
                    System.out.println("✅ Correct! You guessed the number in " + attempts + " attempts.");
                    roundsWon++;
                    isCorrect = true;
                    break;
                } else if (guess < targetNumber) {
                    System.out.println("🔼 Too low. Try again.");
                } else {
                    System.out.println("🔽 Too high. Try again.");
                }
            }

            if (!isCorrect) {
                System.out.println("❌ You've used all attempts. The correct number was: " + targetNumber);
            }

            System.out.println("🏆 Rounds won so far: " + roundsWon);
            System.out.print("🔁 Do you want to play another round? (yes/no): ");
            scanner.nextLine(); // Consume newline
            String response = scanner.nextLine();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("🎉 Game Over! You won " + roundsWon + " round(s). Thanks for playing!");
        scanner.close();
    }
}
