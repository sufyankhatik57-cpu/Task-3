# Task-3
[29/08, 4:41 pm] Sufiyan Khatik: import json
import os

# File to store contacts
FILE_NAME = 'contacts.json'

# Load contacts from file
def load_contacts():
    if os.path.exists(FILE_NAME):
        with open(FILE_NAME, 'r') as f:
            return json.load(f)
    return []

# Save contacts to file
def save_contacts(contacts):
    with open(FILE_NAME, 'w') as f:
        json.dump(contacts, f, indent=4)

# Display all contacts
def view_contacts(contacts):
    if not contacts:
        print("\nNo contacts found.")
        return
    print("\n--- Contact List ---")
    for i, contact in enumerate(contacts, start=1):
        print(f"{i}. Name: {contact['name']}, Phone: {contact['phone']}, Email: {contact['email']}")

# Add a new contact
def add_contact(contacts):
    name = input("Enter name: ")
    phone = input("Enter phone number: ")
    email = input("Enter email address: ")
    contacts.append({'name': name, 'phone': phone, 'email': email})
    save_contacts(contacts)
    print("Contact added successfully!")

# Edit an existing contact
def edit_contact(contacts):
    view_contacts(contacts)
    try:
        index = int(input("Enter the contact number to edit: ")) - 1
        if 0 <= index < len(contacts):
            contacts[index]['name'] = input("Enter new name: ")
            contacts[index]['phone'] = input("Enter new phone number: ")
            contacts[index]['email'] = input("Enter new email: ")
            save_contacts(contacts)
            print("Contact updated successfully!")
        else:
            print("Invalid contact number.")
    except ValueError:
        print("Please enter a valid number.")

# Delete a contact
def delete_contact(contacts):
    view_contacts(contacts)
    try:
        index = int(input("Enter the contact number to delete: ")) - 1
        if 0 <= index < len(contacts):
            deleted = contacts.pop(index)
            save_contacts(contacts)
            print(f"Deleted contact: {deleted['name']}")
        else:
            print("Invalid contact number.")
    except ValueError:
        print("Please enter a valid number.")

# Main menu
def main():
    contacts = load_contacts()
    while True:
        print("\n--- Contact Management System ---")
        print("1. View Contacts")
        print("2. Add Contact")
        print("3. Edit Contact")
        print("4. Delete Contact")
        print("5. Exit")
        choice = input("Enter your choice (1-5): ")

        if choice == '1':
            view_contacts(contacts)
        elif choice == '2':
            add_contact(contacts)
        elif choice == '3':
            edit_contact(contacts)
        elif choice == '4':
            delete_contact(contacts)
        elif choice == '5':
            print("Exiting Contact Management System. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
[29/08, 4:41 pm] Sufiyan Khatik: --- Contact Management System ---
1. View Contacts
2. Add Contact
3. Edit Contact
4. Delete Contact
5. Exit
Enter your choice (1-5): 2
Enter name: Alice
Enter phone number: 1234567890
Enter email address: alice@example.com
Contact added successfully!

--- Contact Management System ---
1. View Contacts
2. Add Contact
3. Edit Contact
4. Delete Contact
5. Exit
Enter your choice (1-5): 1

--- Contact List ---
1. Name: Alice, Phone: 1234567890, Email: alice@example.com
2.
[29/08, 4:41 pm] Sufiyan Khatik: [
    {
        "name": "Alice",
        "phone": "1234567890",
        "email": "alice@example.com"
    }
]
