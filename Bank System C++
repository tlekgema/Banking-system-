#include <iostream>
#include <string>
using namespace std;

// Global arrays for 3 users
string names[3] = {"Thabo", "Valerie", "Cynthia"};
int accountNumbers[3] = {1001, 1002, 1003};
int pins[3] = {2468, 3692,9021};
double balances[3] = {1500,2500,800};

int currentUser = -1; // Index of logged in user

void displayMenu() {
    cout << "===== GCC BANK =====" << endl;
    cout << "Welcome, " << names[currentUser] << endl;
    cout << "1. Deposit" << endl;
    cout << "2. Withdraw" << endl;
    cout << "3. Send Cash" << endl;
    cout << "4. Check Balance" << endl;
    cout << "5. Exit" << endl;
    cout << "Enter choice: ";
}

void checkBalance() {
    cout << "--- Check Balance ---" << endl;
    cout << "Account Holder: " << names[currentUser] << endl;
    cout << "Account Number: " << accountNumbers[currentUser] << endl;
    cout << "Current Balance: R" << balances[currentUser] << endl;
}

void deposit() {
    double amount;
    cout << "--- Deposit ---" << endl;
    cout << "Enter amount to deposit: R";
    cin >> amount;

    if (amount <= 0) {
        cout << "Invalid amount! Amount must be more than 0." << endl;
    } else {
        balances[currentUser] += amount;
        cout << "Deposit successful! New balance: R" << balances[currentUser] << endl;
    }
}

void withdraw() {
    double amount;
    cout << "--- Withdraw ---" << endl;
    cout << "Enter amount to withdraw: R";
    cin >> amount;

    if (amount <= 0) {
        cout << "Invalid amount!" << endl;
    } else if (amount > balances[currentUser]) {
        cout << "Not enough funds! Your balance is R" << balances[currentUser] << endl;
    } else {
        balances[currentUser] -= amount;
        cout << "Withdrawal successful! New balance: R" << balances[currentUser] << endl;
    }
}

int findAccount(int accNum)
{
    for (int i = 0; i < 3; i++) {
        if (accountNumbers[i] == accNum) {
            return i;
        }
    }
    return -1; // Not found
}

void sendCash() {
    int targetAcc;
    double amount;
    cout << "--- Send Cash ---" << endl;
    cout << "Enter recipient account number: ";
    cin >> targetAcc;

    int targetIndex = findAccount(targetAcc);

    if (targetIndex == -1) {
        cout << "Error: Account number " << targetAcc << " does not exist!" << endl;
        return;
    }

    if (targetIndex == currentUser) {
        cout << "Error: You can't send cash to yr account!" << endl;
        return;
    }

    cout << "Recipient: " << names[targetIndex] << endl;
    cout << "Enter amount to send: R";
    cin >> amount;

    if (amount <= 0) {
        cout << "Invalid amount!  must be more than 0." << endl;
    } else if (amount > balances[currentUser]) {
        cout << "Not enough funds! Your balance is R" << balances[currentUser] << endl;
    } else {
        balances[currentUser] -= amount;
        balances[targetIndex] += amount;
        cout << "Transfer successful! R" << amount << " sent to " << names[targetIndex] << endl;
        cout << "Your new balance: R" << balances[currentUser] << endl;
    }
}

bool login() {
    int accNum, pin;
    cout << "===== GCC BANK LOGIN =====" << endl;
    cout << "Enter account number: ";
    cin >> accNum;
    cout << "Enter PIN: ";
    cin >> pin;

    int index = findAccount(accNum);

    if (index == -1) {
        cout << "Invalid account number!" << endl;
        return false;
    }

    if (pins[index] != pin) {
        cout << "Wrong PIN! Access denied." << endl;
        return false;
    }

    currentUser = index;
    cout << "Login successful! Welcome " << names[currentUser] << endl;
    return true;
}

int main()
{
    if (!login())
        {
        cout << "Exiting program..." << endl;
        return 0;
    }

    int choice;
    do
    {
        displayMenu();
        cin >> choice;

        switch (choice)
        {
            case 1:
                deposit();
                break;
            case 2:
                withdraw();
                break;
            case 3:
                sendCash();
                break;
            case 4:
                checkBalance();
                break;
            case 5:
                cout << "Thank you for banking with GCC BANK. Goodbye!" << endl;
                break;
            default:
                cout << "Invalid choice! Enter a number between 1 and 5." << endl;
                break;
        }
    } while (choice != 5);

    return 0;
}
