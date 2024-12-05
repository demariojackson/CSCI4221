# CSCI4221
hello, my name is demario jackson
 

# Group 1 Work Description

My responsibility is to be over the mentall wellness section of the app. Making a tab where students could go and be directed to someone that they could talk to about any issues or problems that they are having. Someone like a counselor.

# Project 3 code: Mental Wellness Helper
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Random;

public class MentalWellnessHelper {

    private static ArrayList<String> mindfulnessActivities = new ArrayList<>();
    private static Random random = new Random();

    public static void main(String[] args) {
        initializeMindfulnessActivities();
        Scanner scanner = new Scanner(System.in);

        System.out.println("Welcome to the Mental Wellness Helper!");
        System.out.println("1. Track Your Mood");
        System.out.println("2. Get a Mindfulness Activity");
        System.out.println("3. Guided Breathing Exercise");
        System.out.println("4. Exit");

        while (true) {
            System.out.print("\nSelect an option (1-4): ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    trackMood(scanner);
                    break;
                case 2:
                    suggestMindfulnessActivity();
                    break;
                case 3:
                    guidedBreathing();
                    break;
                case 4:
                    System.out.println("Take care of yourself! Goodbye.");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please select again.");
            }
        }
    }

    // Mood Tracker
    private static void trackMood(Scanner scanner) {
        System.out.println("\nHow are you feeling today? (1-5)");
        System.out.println("1: Very Sad  2: Sad  3: Neutral  4: Happy  5: Very Happy");
        System.out.print("Your mood: ");
        int mood = scanner.nextInt();

        if (mood < 1 || mood > 5) {
            System.out.println("Invalid input. Please enter a number between 1 and 5.");
        } else {
            String[] moodResponses = {
                "It's okay to feel sad. Take it easy today.",
                "You're feeling down. Consider talking to a friend.",
                "A neutral mood. Maybe try something uplifting?",
                "You're feeling happy! Keep up the positivity!",
                "You're very happy! Spread the joy around!"
            };
            System.out.println(moodResponses[mood - 1]);
        }
    }

    // Suggest a Mindfulness Activity
    private static void suggestMindfulnessActivity() {
        int index = random.nextInt(mindfulnessActivities.size());
        System.out.println("\nHere’s a mindfulness activity for you: " + mindfulnessActivities.get(index));
    }

    // Guided Breathing Exercise
    private static void guidedBreathing() {
        System.out.println("\nGuided Breathing Exercise: ");
        System.out.println("1. Inhale for 4 seconds.");
        pause(4000);
        System.out.println("2. Hold your breath for 4 seconds.");
        pause(4000);
        System.out.println("3. Exhale for 6 seconds.");
        pause(6000);
        System.out.println("Repeat this cycle a few times to relax.");
    }

    // Initialize mindfulness activity suggestions
    private static void initializeMindfulnessActivities() {
        mindfulnessActivities.add("Take a 5-minute walk outside and notice the surroundings.");
        mindfulnessActivities.add("Write down three things you're grateful for.");
        mindfulnessActivities.add("Try a 10-minute guided meditation.");
        mindfulnessActivities.add("Drink a glass of water slowly and mindfully.");
        mindfulnessActivities.add("Stretch your body for 5 minutes.");
    }

    // Pause utility
    private static void pause(int milliseconds) {
        try {
            Thread.sleep(milliseconds);
        } catch (InterruptedException e) {
            System.out.println("An error occurred during the pause.");
        }
    }
}
