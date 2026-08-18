# Library-Management-System-CLI-
A console-based system to add, issue, return, and track books in a small library
books = {}

def add_book(title, qty):
    books[title] = books.get(title, 0) + qty

def issue_book(title):
    if books.get(title, 0) > 0:
        books[title] -= 1
        print(f"'{title}' issued successfully.")
    else:
        print(f"'{title}' not available.")

def return_book(title):
    books[title] = books.get(title, 0) + 1
    print(f"'{title}' returned.")

def show_books():
    for title, qty in books.items():
        print(f"{title}: {qty} copies")

while True:
    cmd = input("\nadd/issue/return/list/quit: ").strip().lower()
    if cmd == "add":
        t = input("Title: "); q = int(input("Quantity: "))
        add_book(t, q)
    elif cmd == "issue":
        issue_book(input("Title: "))
    elif cmd == "return":
        return_book(input("Title: "))
    elif cmd == "list":
        show_books()
    elif cmd == "quit":
        break
