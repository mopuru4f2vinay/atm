class User:
    def __init__(self, user_id, pin):
        self.user_id = user_id
        self.pin = pin
        self.balance = 0
        self.transaction_history = []

class ATM:
    def __init__(self):
        self.users = {} 
    def add_user(self, user_id, pin):
        self.users[user_id] =User( user_id,pin)

    def authenticate_user(self, user_id, pin):
        if user_id in self.users:
            if self.users[user_id].pin == pin:
                return True
        return False

    def deposit(self, user_id, amount):
        if user_id in self.users:
            self.users[user_id].balance += amount
            self.users[user_id].transaction_history.append(f"Deposit: +${amount}")

    def withdraw(self, user_id, amount):
        if user_id in self.users:
            if self.users[user_id].balance >= amount:
                self.users[user_id].balance -= amount
                self.users[user_id].transaction_history.append(f"Withdrawal: -${amount}")
            else:
                print("Insufficient funds.")

    def transfer(self, user_id, recipient_id, amount):
        if user_id in self.users and recipient_id in self.users:
            if self.users[user_id].balance >= amount:
                self.users[user_id].balance -= amount
                self.users[user_id].transaction_history.append(f"Transfer to {recipient_id}: -${amount}")
                self.users[recipient_id].balance += amount
                self.users[recipient_id].transaction_history.append(f"Transfer from {user_id}: +${amount}")
            else:
                print("Insufficient funds.")

    def show_transaction_history(self, user_id):
        if user_id in self.users:
            print("Transaction History:")
            for transaction in self.users[user_id].transaction_history:
                print(transaction)

def main():
    atm = ATM()

    
    atm.add_user("123456", "1234")

    while True:
        user_id = input("Enter User ID: ")
        pin = input("Enter PIN: ")

        if atm.authenticate_user(user_id, pin):
            print("Authentication successful.")
            break
        else:
            print("Authentication failed. Please try again.")

    while True:
        print("\nOptions:")
        print("1. Transactions History")
        print("2. Withdraw")
        print("3. Deposit")
        print("4. Transfer")
        print("5. Quit")

        choice = input("Enter your choice: ")

        if choice == "1":
            atm.show_transaction_history(user_id)
        elif choice == "2":
            amount = float(input("Enter amount to withdraw: "))
            atm.withdraw(user_id, amount)
        elif choice == "3":
            amount = float(input("Enter amount to deposit: "))
            atm.deposit(user_id, amount)
        elif choice == "4":
            recipient_id = input("Enter recipient's User ID: ")
            amount = float(input("Enter amount to transfer: "))
            atm.transfer(user_id, recipient_id, amount)
        elif choice == "5":
            print("Exiting. Thank you!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
