#include <stdio.h>
#include <string.h>

#define MAX_BOOKS 100

// Structure to represent a book
struct Book {
    int id;
    char title[50];
    char author[50];
    float price;
};

// Global array to store books and a counter for the number of books
struct Book books[MAX_BOOKS];
int numBooks = 0;

// Function to add a book
void addBook() {
    if (numBooks < MAX_BOOKS) {
        printf("Enter Book ID: ");
        scanf("%d", &books[numBooks].id);
        printf("Enter Book Title: ");
        scanf(" %[^\n]", books[numBooks].title); // Read string with spaces
        printf("Enter Book Author: ");
        scanf(" %[^\n]", books[numBooks].author);
        printf("Enter Book Price: ");
        scanf("%f", &books[numBooks].price);
        numBooks++;
        printf("Book added successfully!\n");
    } else {
        printf("Maximum number of books reached.\n");
    }
}

// Function to search for a book by ID
void searchBook() {
    int searchId;
    printf("Enter Book ID to search: ");
    scanf("%d", &searchId);
    int found = 0;
    for (int i = 0; i < numBooks; i++) {
        if (books[i].id == searchId) {
            printf("\nBook Found:\n");
            printf("ID: %d\n", books[i].id);
            printf("Title: %s\n", books[i].title);
            printf("Author: %s\n", books[i].author);
            printf("Price: %.2f\n", books[i].price);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Book with ID %d not found.\n", searchId);
    }
}

// Function to update a book's details
void updateBook() {
    int updateId;
    printf("Enter Book ID to update: ");
    scanf("%d", &updateId);
    int found = 0;
    for (int i = 0; i < numBooks; i++) {
        if (books[i].id == updateId) {
            printf("Enter New Title: ");
            scanf(" %[^\n]", books[i].title);
            printf("Enter New Author: ");
            scanf(" %[^\n]", books[i].author);
            printf("Enter New Price: ");
            scanf("%f", &books[i].price);
            printf("Book updated successfully!\n");
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Book with ID %d not found.\n", updateId);
    }
}

// Function to delete a book by ID
void deleteBook() {
    int deleteId;
    printf("Enter Book ID to delete: ");
    scanf("%d", &deleteId);
    int found = 0;
    for (int i = 0; i < numBooks; i++) {
        if (books[i].id == deleteId) {
            // Shift elements to the left to fill the gap
            for (int j = i; j < numBooks - 1; j++) {
                books[j] = books[j + 1];
            }
            numBooks--;
            printf("Book deleted successfully!\n");
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Book with ID %d not found.\n", deleteId);
    }
}

// Function to display all books
void displayAllBooks() {
    if (numBooks == 0) {
        printf("No books to display.\n");
        return;
    }
    printf("\n--- All Books ---\n");
    for (int i = 0; i < numBooks; i++) {
        printf("ID: %d, Title: %s, Author: %s, Price: %.2f\n",
               books[i].id, books[i].title, books[i].author, books[i].price);
    }
    printf("-------------------\n");
}

int main() {
    int choice;
    do {
        printf("\nBook Management System (No File Handling)\n");
        printf("1. Add Book\n");
        printf("2. Search Book\n");
        printf("3. Update Book\n");
        printf("4. Delete Book\n");
        printf("5. Display All Books\n");
        printf("0. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addBook();
                break;
            case 2:
                searchBook();
                break;
            case 3:
                updateBook();
                break;
            case 4:
                deleteBook();
                break;
            case 5:
                displayAllBooks();
                break;
            case 0:
                printf("Exiting program.\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 0);

    return 0;
}