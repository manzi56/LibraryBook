class LibraryBook:
    def __init__(self, title, author, year, isbn):
        self.title = title
        self.author = author
        self.year = year
        self.isbn = isbn
        self.checked_out = False
    
    def __str__(self):
        return f"{self.title} by {self.author} ({self.year}), ISBN: {self.isbn}"
    
    def check_out(self):
        if self.checked_out:
            return False
        self.checked_out = True
        return True
    
    def check_in(self):
        if not self.checked_out:
            return False
        self.checked_out = False
        return True
class Library:
    def __init__(self):
        self.books = []
    
    def add_book(self, book):
        self.books.append(book)
    
    def remove_book(self, book):
        self.books.remove(book)
    
    def search_books(self, term):
        return [book for book in self.books if term.lower() in book.title.lower() or term.lower() in book.author.lower()]
    
    def check_out_book(self, book):
        return book.check_out()
    
    def check_in_book(self, book):
        return book.check_in()
    
    def get_all_books(self):
        return self.books
    
    def get_total_books(self):
        return len(self.books)
    
    def get_available_books(self):
        return len([book for book in self.books if not book.checked_out])
from library import Library, LibraryBook

# Create a new library object
library = Library()

# Add three new books to the library
book1 = LibraryBook("Python for Beginners", "John Smith", 2021, "978-1234567890")
book2 = LibraryBook("Python for Data Science", "
book3 = LibraryBook("Python Web Development", "Tom Lee", 2020, "978-0123456789")
# Search for books with the search term "Python" and print the results
search_results = library.search_books("Python")
for book in search_results:
print(book)
# Check out one of the books
library.check_out_book(book2)
# List all of the books in the library
all_books = library.get_all_books()
for book in all_books:
print(book)
# Check in the book that was checked out
library.check_in_book(book2)
# List all of the books in the library again to verify that the book was checked in successfully
all_books = library.get_all_books()
for book in all_books:
print(book)
