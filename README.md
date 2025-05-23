import java.util.Scanner;

public class MainApp {
    public static void main(String[] args) {
        try (Scanner scanner = new Scanner(System.in)) {

        System.out.print("Create a username: "); // inbuilt: System.out.print
        String correctUsername = scanner.nextLine(); // inbuilt: scanner.nextLine

        String correctPassword;
        while (true) {
            System.out.print("Create a password (at least 8 characters, contain a number, and a symbol): "); // inbuilt: System.out.print
            correctPassword = scanner.nextLine(); // inbuilt: scanner.nextLine
            if (validatePassword(correctPassword)) {
                break;
            } else {
                System.out.println("Password does not meet the criteria. Try again."); // inbuilt: System.out.println
            }
        }

        System.out.println("Account created successfully!"); // inbuilt: System.out.println

        System.out.print("Enter username: "); // inbuilt: System.out.print
        String username = scanner.nextLine(); // inbuilt: scanner.nextLine

        System.out.print("Enter password: "); // inbuilt: System.out.print
        String password = scanner.nextLine(); // inbuilt: scanner.nextLine

        if (username.equals(correctUsername) && password.equals(correctPassword)) { // inbuilt: String.equals
            System.out.println("Login successful!"); // inbuilt: System.out.println
        } else {
            System.out.println("Invalid username or password."); // inbuilt: System.out.println
        }

        } // try-with-resources automatically closes the scanner
    }

    private static boolean validatePassword(String password) {
        if (password.length() < 8) { // inbuilt: String.length
            return false;
        }
        boolean hasNumber = false;
        boolean hasSymbol = false;

        for (char c : password.toCharArray()) { // inbuilt: String.toCharArray
            if (Character.isDigit(c)) { // inbuilt: Character.isDigit
                hasNumber = true;
            } else if (!Character.isLetterOrDigit(c)) { // inbuilt: Character.isLetterOrDigit
                hasSymbol = true;
            }
        }

        return hasNumber && hasSymbol;
    }
}
