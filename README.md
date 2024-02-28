# Simple-Task-List

import java.util.ArrayList;
import java.util.Scanner;

public class TaskListApp {
    private static ArrayList<String> tasks = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        boolean running = true;
        while (running) {
            System.out.println("\nTask List Menu:");
            System.out.println("1. Add Task");
            System.out.println("2. Remove Task");
            System.out.println("3. List Tasks");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    addTask();
                    break;
                case 2:
                    removeTask();
                    break;
                case 3:
                    listTasks();
                    break;
                case 4:
                    running = false;
                    System.out.println("Exiting... Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
        scanner.close();
    }

    private static void addTask() {
        System.out.print("Enter the task to add: ");
        String task = scanner.nextLine();
        tasks.add(task);
        System.out.println("Task added: " + task);
    }

    private static void removeTask() {
        if (tasks.isEmpty()) {
            System.out.println("Task list is empty. No task to remove.");
            return;
        }
        System.out.print("Enter the index of the task to remove: ");
        int index = scanner.nextInt();
        scanner.nextLine(); // Consume newline character

        if (index < 0 || index >= tasks.size()) {
            System.out.println("Invalid index. No task removed.");
        } else {
            String removedTask = tasks.remove(index);
            System.out.println("Task removed: " + removedTask);
        }
    }

    private static void listTasks() {
        if (tasks.isEmpty()) {
            System.out.println("Task list is empty.");
        } else {
            System.out.println("Task List:");
            for (int i = 0; i < tasks.size(); i++) {
                System.out.println((i + 1) + ". " + tasks.get(i));
            }
        }
    }
}
