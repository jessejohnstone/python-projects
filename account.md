import os

FILENAME = "bank_data.txt"


# Create file if not exists
def initialize_file():
    if not os.path.exists(FILENAME):
        open(FILENAME, "w").close()


# Read all accounts
def read_accounts():
    accounts = {}

    with open(FILENAME, "r") as file:
        for line in file:
            line = line.strip()

            if line:
                acc_no, name, balance = line.split("|")
                accounts[acc_no] = {
                    "name": name,
                    "balance": float(balance)
                }

    return accounts


# Save accounts to file
def save_accounts(accounts):
    with open(FILENAME, "w") as file:
        for acc_no, data in accounts.items():
            line = f"{acc_no}|{data['name']}|{data['balance']}\n"
            file.write(line)


# Create account
def create_account(accounts):
    acc_no = input("Enter new account number: ")

    if acc_no in accounts:
        print("Account already exists!")
        return

    name = input("Enter account holder name: ")
    balance = float(input("Enter initial deposit: "))

    accounts[acc_no] = {
        "name": name,
        "balance": balance
    }

    save_accounts(accounts)
    print("Account created successfully!")


# Deposit money
def deposit(accounts):
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("Account not found!")
        return

    amount = float(input("Enter amount to deposit: "))

    accounts[acc_no]["balance"] += amount

    save_accounts(accounts)
    print("Deposit successful!")


# Withdraw money
def withdraw(accounts):
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("Account not found!")
        return

    amount = float(input("Enter amount to withdraw: "))

    if amount > accounts[acc_no]["balance"]:
        print("Insufficient balance!")
        return

    accounts[acc_no]["balance"] -= amount

    save_accounts(accounts)
    print("Withdrawal successful!")


# Check balance
def check_balance(accounts):
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("Account not found!")
        return

    acc = accounts[acc_no]

    print("\n--- Account Details ---")
    print("Name:", acc["name"])
    print("Balance: KES", acc["balance"])
    print("-------------------------")


# Main menu
def main():
    initialize_file()
    accounts = read_accounts()

    while True:
        print("\n===== BANKING SYSTEM =====")
        print("1. Create Account")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Check Balance")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            create_account(accounts)

        elif choice == "2":
            deposit(accounts)

        elif choice == "3":
            withdraw(accounts)

        elif choice == "4":
            check_balance(accounts)

        elif choice == "5":
            print("Thank you for using our bank system!")
            break

        else:
            print("Invalid choice! Try again.")


# Run program
if __name__ == "__main__":
    main()
