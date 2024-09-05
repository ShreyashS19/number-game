
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {

    public static int playRound() {
        Random rand = new Random();
        int no = rand.nextInt(100) + 1;  
        int attempts = 0;
        int maxAttempts = 5;
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Enter a number between 1 and 100. You have 5 attempts to guess it.");

        while (attempts < maxAttempts) {
            System.out.print("Enter your guess: ");
            int guess = sc.nextInt();
            attempts++;

          


            if (guess < no) {
                System.out.println("Too low!");
            } else if (guess > no) {
                System.out.println("Too high!");
            } else {
                System.out.println("Congratulations! You've guessed the number " + no + " in " + attempts + " attempts.");
                return attempts;
            }

         
            System.out.println("You have " + (maxAttempts - attempts) + " attempts left.");
        }

        System.out.println("Sorry, you've used all " + maxAttempts + " attempts. The correct number was " + no + ".");
        return maxAttempts + 1;  
    }

    public static void playGame() {
        Scanner sc = new Scanner(System.in);
        int roundsPlayed = 0;
        int totalAttempts = 0;
        boolean keepPlaying = true;

        while (keepPlaying) {
            roundsPlayed++;
            System.out.println("\n Round " + roundsPlayed );

            int attemptsTaken = playRound();
            totalAttempts += attemptsTaken;

            System.out.print("Do you want to play another round? (yes/no): ");
            String response = sc.next().toLowerCase();
            if (!response.equals("yes")) {
                keepPlaying = false;
            }
        }

        System.out.println("\nGame over! You played " + roundsPlayed + " rounds with a total score of " + totalAttempts + ".");
        System.out.println("Average attempts per round: " + (double) totalAttempts / roundsPlayed);
    }

    public static void main(String[] args) {
        playGame();
        
    }
}
