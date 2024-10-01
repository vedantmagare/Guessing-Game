# Guessing-Game

	package InternshipProject;
	
	import java.util.Random;
	import java.util.Scanner;
	
	public class GuessTheNumber {
	
		public static void main(String[] args) {
			Scanner scanner = new Scanner(System.in);
			Random random = new Random();
	
			int rounds = 3; // Total number of rounds
			int maxAttempts = 5; // Maximum attempts allowed per round
			int score = 0; // Initialize score
	
			System.out.println("Welcome to the Guess the Number Game!");
	
			// Loop for the number of rounds
			for (int round = 1; round <= rounds; round++) {
				int numberToGuess = random.nextInt(100) + 1; // Generate a random number between 1 and 100
				int attempts = 0;
				boolean guessedCorrectly = false;
	
				System.out.println("\nRound " + round + " begins!");
				System.out.println("I have selected a number between 1 and 100. Try to guess it!");
	
				// Loop for each attempt within the allowed number of attempts
				while (attempts < maxAttempts && !guessedCorrectly) {
					System.out.print("Enter your guess: ");
					int userGuess = scanner.nextInt();
					attempts++;
	
					if (userGuess == numberToGuess) {
						System.out.println("Congratulations! You guessed the number in " + attempts + " attempts.");
						guessedCorrectly = true;
						// Points are calculated based on attempts
						score += (maxAttempts - attempts + 1) * 10;
					} else if (userGuess < numberToGuess) {
						System.out.println("Too low! Try a higher number.");
					} else {
						System.out.println("Too high! Try a lower number.");
					}
				}
	
				// If the user didn't guess the number within the allowed attempts
				if (!guessedCorrectly) {
					System.out.println("Sorry, you've used all your attempts. The number was: " + numberToGuess);
				}
	
				System.out.println("Your current score: " + score);
			}
	
			System.out.println("\nGame Over! Your final score is: " + score);
			scanner.close();
		}
	}
