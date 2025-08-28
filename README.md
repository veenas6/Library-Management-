# Book Management System (Without File Handling)

## Overview
This is a simple C program that allows you to manage a collection of books using an in-memory array. It supports basic operations such as adding, searching, updating, deleting, and displaying books.

## Features
- **Add Book:** Insert new books with details like ID, title, author, and price.
- **Search Book:** Find a book by its unique ID.
- **Update Book:** Modify the details of an existing book using its ID.
- **Delete Book:** Remove a book from the collection by its ID.
- **Display All Books:** List all books currently stored in the system.

## How It Works
- Books are stored in a global array with a fixed maximum size (`MAX_BOOKS`).
- The program uses a menu-driven interface where users can select options by entering numbers.
- Data is stored temporarily in memory and is lost when the program exits (no file handling).

## Usage

### Compile the program
```bash
gcc -o book_management book_management.c
