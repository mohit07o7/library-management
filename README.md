# library-management in c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

#define MAX_BOOKS 100
#define MAX_PATRONS 100
#define MAX_TRANSACTIONS 100

// Data Structures
typedef struct {
    int book_id;
    char title[100];
    char author[100];
    int available_copies;
} Book;

typedef struct {
    int patron_id;
    char name[100];
} Patron;

typedef struct {
    int transaction_id;
    int book_id;
    int patron_id;
} Transaction;

// Arrays to store data
Book books[MAX_BOOKS];
Patron patrons[MAX_PATRONS];
Transaction transactions[MAX_TRANSACTIONS];
int bookCount = 0;
int patronCount = 0;
int transactionCount = 0;

// Function to add a book
void addBook() {
    if (bookCount < MAX_BOOKS) {
        Book newBook;
        printf("Enter book title: ");
        scanf("%s", newBook.title);
        printf("Enter book author: ");
        scanf("%s", newBook.author);
        newBook.book_id = bookCount + 1;
        newBook.available_copies = 1; // Assuming one copy by default

        books[bookCount++] = newBook;
        printf("Book added successfully!\n");
    } else {
        printf("Max book limit reached!\n");
    }
}

// Function to list all books
void listBooks() {
    printf("List of Books:\n");
    for (int i = 0; i < bookCount; i++) {
        printf("Book ID: %d\n", books[i].book_id);
        printf("Title: %s\n", books[i].title);
        printf("Author: %s\n", books[i].author);
        printf("Available Copies: %d\n", books[i].available_copies);
        printf("------------\n");
    }
}

// Function to add a patron
void addPatron() {
    if (patronCount < MAX_PATRONS) {
        Patron newPatron;
        printf("Enter patron name: ");
        scanf("%s", newPatron.name);
        newPatron.patron_id = patronCount + 1;

      patrons[patronCount++] = newPatron;
        printf("Patron added successfully!\n");
    } else {
        printf("Max patron limit reached!\n");
    }
}




int main() {
    int choice;

    do {
        printf("Library Management System\n");
        printf("1. Add Book\n");
        printf("2. List Books\n");
        printf("3. Add Patron\n");

    
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addBook();
                break;
            case 2:
                listBooks();
                break;
            case 3:
                addPatron();
                break;
          
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 0);

    return 0;
}
