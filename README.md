# Library-Management
import java.util.ArrayList; import java.util.List; import java.util.Scanner;

class Book { private String title; private String author;
public Book(String title, String author) {
    this.title = title;
    this.author = author;
}

public String getTitle() {
    return title;
}

public String getAuthor() {
    return author;
}

@Override
public String toString() {
    return "Title: " + title + ", Author: " + author;
}
public class LibraryManagementSystem { private List library;

public LibraryManagementSystem() {
    library = new ArrayList<>();
}

public void addBook(String title, String author) {
    Book book = new Book(title, author);
    library.add(book);
    System.out.println("Book added to the library: " + book);
}

public void searchBook(String query) {
    System.out.println("Searching for books containing: " + query);
    for (Book book : library) {
        if (book.getTitle().toLowerCase().contains(query.toLowerCase()) ||
            book.getAuthor().toLowerCase().contains(query.toLowerCase())) {
            System.out.println(book);
        }
    }
}

public void displayLibrary() {
    System.out.println("Library Contents:");
    for (Book book : library) {
        System.out.println(book);
    }
}

public static void main(String[] args) {
    LibraryManagementSystem librarySystem = new LibraryManagementSystem();
    Scanner scanner = new Scanner(System.in);

    while (true) {
        System.out.println("\nLibrary Management System Menu:");
        System.out.println("1. Add Book");
        System.out.println("2. Search Book");
        System.out.println("3. Display Library");
        System.out.println("4. Exit");
        System.out.print("Please select an option: ");

        int choice = scanner.nextInt();
        scanner.nextLine(); // Consume the newline character

        switch (choice) {
            case 1:
                System.out.print("Enter book title: ");
                String title = scanner.nextLine();
                System.out.print("Enter author name: ");
                String author = scanner.nextLine();
                librarySystem.addBook(title, author);
                break;
            case 2:
                System.out.print("Enter search query: ");
                String query = scanner.nextLine();
                librarySystem.searchBook(query);
                break;
            case 3:
                librarySystem.displayLibrary();
                break;
            case 4:
                System.out.println("Thank you for using the Library Management System.");
                System.exit(0);
            default:
                System.out.println("Invalid option. Please select a valid option.");
        }
    }
}
}
