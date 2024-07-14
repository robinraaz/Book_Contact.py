# Book_Contact.py
class Contact:
    def __init__(self, name, phone, email, address):
        self.name = name
        self.phone = phone
        self.email = email
        self.address = address
    def __str__(self):
        return f'Name: {self.name}, Phone: {self.phone}, Email: {self.email}, Address: {self.address}'
class ContactBook:
    def __init__(self):
        self.contacts = []
    def add_contact(self, contact):
        self.contacts.append(contact)
        print(f'Contact {contact.name} added.')
    def view_contacts(self):
        if not self.contacts:
            print('No contacts to display.')
        else:
            for contact in self.contacts:
                print(contact)
    def search_contact(self, search_term):
        results = [contact for contact in self.contacts if
                   search_term.lower() in contact.name.lower() or search_term in contact.phone]
        if not results:
            print('No contacts found.')
        else:
            for contact in results:
                print(contact)
    def update_contact(self, name, new_contact):
        for i, contact in enumerate(self.contacts):
            if contact.name == name:
                self.contacts[i] = new_contact
                print(f'Contact {name} updated.')
                return
        print(f'Contact {name} not found.')
    def delete_contact(self, name):
        for i, contact in enumerate(self.contacts):
            if contact.name == name:
                del self.contacts[i]
                print(f'Contact {name} deleted.')
                return
        print(f'Contact {name} not found.')
def main():
    contact_book = ContactBook()
    while True:
        print("\nContact Book Menu")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Enter your choice: ")
        if choice == '1':
            name = input("Enter name: ")
            phone = input("Enter phone number: ")
            email = input("Enter email: ")
            address = input("Enter address: ")
            contact = Contact(name, phone, email, address)
            contact_book.add_contact(contact)
        elif choice == '2':
            contact_book.view_contacts()
        elif choice == '3':
            search_term = input("Enter name or phone number to search: ")
            contact_book.search_contact(search_term)
        elif choice == '4':
            name = input("Enter the name of the contact to update: ")
            print("Enter new details")
            new_name = input("Enter name: ")
            new_phone = input("Enter phone number: ")
            new_email = input("Enter email: ")
            new_address = input("Enter address: ")
            new_contact = Contact(new_name, new_phone, new_email, new_address)
            contact_book.update_contact(name, new_contact)
        elif choice == '5':
            name = input("Enter the name of the contact to delete: ")
            contact_book.delete_contact(name)
        elif choice == '6':
            print("Exiting Contact Book.")
            break
        else:
            print("Invalid choice. Please try again.")
if __name__ == "__main__":
    main()
