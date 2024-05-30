# 🏦 ATM Simulation Program

This project simulates the behavior of an ATM using Python and the Tkinter library. The program allows users to:

- 📋 Display their bank account balance
- 💵 Deposit money into their account
- 💸 Withdraw money from their account
- 🚪 Exit the ATM

## How to Run the Program

1. **Ensure Python is Installed**:
    - You need to have Python 3.x installed on your system. You can download it from [python.org](https://www.python.org/). 🐍

2. **Install Tkinter**:
    - Tkinter is usually included with Python, but if you don't have it, you can install it using the following command:
      ```bash
      pip install tk
      ```

3. **Download the Script**:
    - Download the `atm_simulation.py` script from this repository. 📥

4. **Run the Script**:
    - Navigate to the directory where you downloaded the script and run it using:
      ```bash
      python atm_simulation.py
      ```

## Usage

1. **Access ATM**:
    - When you run the script, a window will appear with a button labeled "Access ATM". Click this button to start using the ATM. 🔓

2. **PIN Verification**:
    - The program will prompt you to enter a PIN. The default PIN is `1234`. You have three attempts to enter the correct PIN. If the correct PIN is not entered within three attempts, the program will exit. 🔒

3. **Main Menu**:
    - After entering the correct PIN, the main menu will be displayed. You will have the following options:
        - `1`: Display Balance 🧾
        - `2`: Deposit Money 💵
        - `3`: Withdraw Money 💸
        - `4`: Exit 🚪

### Options Detail

- **Display Balance**:
    - Select option `1` to display your current account balance. A message box will show the balance. 🧾

- **Deposit Money**:
    - Select option `2` to deposit money into your account. You will be prompted to enter the amount to deposit. If the entered amount is positive, it will be added to your balance, and a confirmation message will be displayed. 💵

- **Withdraw Money**:
    - Select option `3` to withdraw money. A sub-menu will appear with predefined amounts (£10, £20, £50, £100, £200) and an option for "Other Amount".
        - If you choose a predefined amount, the withdrawal will be processed if the amount is a multiple of 10 and does not exceed the current balance. 💸
        - If you choose "Other Amount", you will be prompted to enter a custom amount. The custom amount must be a multiple of 10 and within the available balance to be processed. 🔢

- **Exit**:
    - Select option `4` to exit the program. A goodbye message will be displayed, and the program will close. 👋

### Important Notes

- **Initial Balance**:
    - The initial balance is set to £1000. 💰

- **Withdrawal Conditions**:
    - Withdrawals must be in multiples of £10.
    - The withdrawal amount must not exceed the current balance.

## Dependencies

- **Python 3.x**: Ensure you have Python 3.x installed. 🐍
- **Tkinter**: The Tkinter library is used for the graphical interface. 🖼️

## Troubleshooting

- **Incorrect PIN**:
    - If you enter an incorrect PIN three times, the program will exit. Restart the program to try again. 🔐

- **Invalid Amounts**:
    - When depositing or withdrawing, ensure the amounts are valid (positive integers for deposits and multiples of 10 for withdrawals). ❌

## License

This project is open-source and available under the MIT License. 📜

## Contributing
![Screenshot 2024-05-30 154410](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/fabeefd6-bd94-41e9-a8a3-29191a8b1662)

![Screenshot 2024-05-30 154442](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/49a4042d-0f62-4ada-b87a-6a04863dca9a)

![Screenshot 2024-05-30 154458](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/b4825b73-fa74-4eaa-b3e8-8eb762daa9fc)

![Screenshot 2024-05-30 154513](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/f3d186a6-9d01-4ecc-aead-b715d46245a7)

![Screenshot 2024-05-30 154525](https://github.com/heyysusan/ATM-Stimulator/assets/168830084/4b1b8f7f-a4e5-451c-ad01-48ded05b3a32)

Contributions are welcome! If you have suggestions for improvements or new features, feel free to open an issue or submit a pull request. 🤝
