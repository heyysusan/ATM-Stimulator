# 🏦 ATM Simulation Program

Project from Data Technician bootcamp at JustIT.

### Part 1: ATM Simulation Program 🏦

This Python program simulates the behavior of an Automated Teller Machine (ATM). It allows users to check their balance, withdraw money, deposit money, and exit. The user must enter a correct PIN to access the ATM functionalities.

#### Features ✨
- **🔒 PIN Protection**: Users must enter a correct PIN to access the ATM menu.
- **💰 Balance Inquiry**: Users can check their current account balance.
- **💸 Money Withdrawal**: Users can withdraw preset amounts or enter a custom amount (multiples of £10).
- **📥 Money Deposit**: Users can deposit money into their account.
- **🚪 Exit Option**: Users can exit the ATM application.

#### Requirements 📋
- Python 3.x

#### Usage 🚀
1. Run the `atm.py` script.
2. Enter the correct PIN (default PIN is `1234`).
3. Select from the main menu options to perform various operations:
    - Press `1` to check balance.
    - Press `2` to withdraw money.
    - Press `3` to deposit money.
    - Press `4` to exit the application.

#### Example 💡
```bash
$ python atm.py
Please enter your PIN: 1234

ATM Main Menu:
1. Display Balance
2. Withdraw Money
3. Deposit Money
4. Exit
Please select an option: 1
Your current balance is: £1000

ATM Main Menu:
1. Display Balance
2. Withdraw Money
3. Deposit Money
4. Exit
Please select an option: 2

Withdrawal Menu:
1. £20
2. £50
3. £100
4. Other Amount
Select an option: 2
£50 has been withdrawn from your account.
Your new balance is: £950
```

#### Source Code 📂
```python
class ATM:
    def __init__(self, balance=0, pin="1234"):
        self.balance = balance
        self.pin = pin

    def check_pin(self):
        while True:
            entered_pin = input("Please enter your PIN: ")
            if entered_pin == self.pin:
                return True
            else:
                print("Incorrect PIN. Please try again.")

    def main_menu(self):
        print("\nATM Main Menu:")
        print("1. Display Balance")
        print("2. Withdraw Money")
        print("3. Deposit Money")
        print("4. Exit")
        
    def display_balance(self):
        print(f"Your current balance is: £{self.balance}")

    def withdraw_money(self):
        print("\nWithdrawal Menu:")
        print("1. £20")
        print("2. £50")
        print("3. £100")
        print("4. Other Amount")
        option = input("Select an option: ")
        
        if option == '1':
            self.withdraw_amount(20)
        elif option == '2':
            self.withdraw_amount(50)
        elif option == '3':
            self.withdraw_amount(100)
        elif option == '4':
            amount = int(input("Enter the amount you wish to withdraw: "))
            if amount % 10 == 0:
                self.withdraw_amount(amount)
            else:
                print("The amount must be a multiple of 10.")
        else:
            print("Invalid option selected. Please try again.")
        
    def withdraw_amount(self, amount):
        if amount > self.balance:
            print("Insufficient funds.")
        else:
            self.balance -= amount
            print(f"£{amount} has been withdrawn from your account.")
            print(f"Your new balance is: £{self.balance}")

    def deposit_money(self):
        amount = int(input("Enter the amount you wish to deposit: "))
        self.balance += amount
        print(f"£{amount} has been deposited into your account.")
        print(f"Your new balance is: £{self.balance}")

    def run(self):
        if self.check_pin():
            while True:
                self.main_menu()
                choice = input("Please select an option: ")
                
                if choice == '1':
                    self.display_balance()
                elif choice == '2':
                    self.withdraw_money()
                elif choice == '3':
                    self.deposit_money()
                elif choice == '4':
                    print("Thank you for using the ATM. Goodbye!")
                    break
                else:
                    print("Invalid choice. Please try again.")

# Create an instance of the ATM class and run the program
atm = ATM(balance=1000)  # You can set an initial balance
atm.run()
```

### Part 2: Adding a Graphic Interface with Tkinter 🖥️

Extend the ATM simulation program with a graphical user interface (GUI) using the Tkinter library.

#### Features ✨
- **🔒 PIN Protection**: Users must enter a correct PIN to access the ATM menu.
- **💰 Balance Inquiry**: Users can check their current account balance.
- **💸 Money Withdrawal**: Users can withdraw preset amounts or enter a custom amount (multiples of £10).
- **📥 Money Deposit**: Users can deposit money into their account.
- **🚪 Exit Option**: Users can exit the ATM application.

#### Requirements 📋
- Python 3.x
- Tkinter (usually included with Python installations)

#### Usage 🚀
1. Run the `atm_gui.py` script.
2. Enter the correct PIN in the GUI (default PIN is `1234`).
3. Use the buttons and input fields in the GUI to perform various operations.

#### Example GUI 💡
A sample screenshot or description of how the GUI looks and works.

#### Source Code 📂
```python
import tkinter as tk
from tkinter import messagebox

class ATMGUI:
    def __init__(self, root):
        self.root = root
        self.root.title("ATM Machine")
        self.balance = 1000
        self.pin = "1234"
        self.create_widgets()
        
    def create_widgets(self):
        self.pin_label = tk.Label(self.root, text="Enter PIN:")
        self.pin_label.pack()
        
        self.pin_entry = tk.Entry(self.root, show="*")
        self.pin_entry.pack()
        
        self.pin_button = tk.Button(self.root, text="Submit", command=self.check_pin)
        self.pin_button.pack()
        
        self.menu_frame = tk.Frame(self.root)
        
        self.balance_button = tk.Button(self.menu_frame, text="Display Balance", command=self.display_balance)
        self.balance_button.pack(fill='x')
        
        self.withdraw_button = tk.Button(self.menu_frame, text="Withdraw Money", command=self.withdraw_money)
        self.withdraw_button.pack(fill='x')
        
        self.deposit_button = tk.Button(self.menu_frame, text="Deposit Money", command=self.deposit_money)
        self.deposit_button.pack(fill='x')
        
        self.exit_button = tk.Button(self.menu_frame, text="Exit", command=self.root.quit)
        self.exit_button.pack(fill='x')
        
    def check_pin(self):
        if self.pin_entry.get() == self.pin:
            self.pin_label.pack_forget()
            self.pin_entry.pack_forget()
            self.pin_button.pack_forget()
            self.menu_frame.pack()
        else:
            messagebox.showerror("Error", "Incorrect PIN. Please try again.")
    
    def display_balance(self):
        messagebox.showinfo("Balance", f"Your current balance is: £{self.balance}")
    
    def withdraw_money(self):
        amount = tk.simpledialog.askinteger("Withdraw", "Enter amount to withdraw")
        if amount:
            if amount % 10 != 0:
                messagebox.showerror("Error", "Amount must be a multiple of 10.")
            elif amount > self.balance:
                messagebox.showerror("Error", "Insufficient funds.")
            else:
                self.balance -= amount
                messagebox.showinfo("Withdraw", f"£{amount} has been withdrawn from your account.")
    
    def deposit_money(self):
        amount = tk.simpledialog.askinteger("Deposit", "Enter amount to deposit")
        if amount:
            self.balance += amount
            messagebox.showinfo("Deposit", f"£{amount} has been deposited into your account.")

if __name__ == "__main__":
    root = tk.Tk()
    app = ATMGUI(root)
    root.mainloop()
```

### Installation 💻
1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Run the `atm.py` script for the command-line version or the `atm_gui.py` script for the graphical version.

```bash
# Clone the repository
git clone https://github.com/your-username/atm-simulation.git

# Navigate to the project directory
cd atm-simulation

# Run the command-line ATM simulation
python atm.py

# OR

# Run the graphical ATM simulation
python atm_gui.py
```

## Contributing
![Screenshot 2024-05-30 154410](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/fabeefd6-bd94-41e9-a8a3-29191a8b1662)

![Screenshot 2024-05-30 154442](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/49a4042d-0f62-4ada-b87a-6a04863dca9a)

![Screenshot 2024-05-30 154458](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/b4825b73-fa74-4eaa-b3e8-8eb762daa9fc)

![Screenshot 2024-05-26 162409](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/2c8ff5c6-aaf1-4f0a-844c-fc39925e8880)

![Screenshot 2024-05-26 162439](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/e7a0d479-2073-4d72-8167-bf306a1aa672)

![Screenshot 2024-05-30 154513](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/f3d186a6-9d01-4ecc-aead-b715d46245a7)

![Screenshot 2024-05-30 154525](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/4b1b8f7f-a4e5-451c-ad01-48ded05b3a32)

Contributions are welcome! If you have suggestions for improvements or new features, feel free to open an issue or submit a pull request. 🤝
