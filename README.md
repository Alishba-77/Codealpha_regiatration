# Codealpha_regiatration
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

// Function to register a new user
void registerUser() {
    string username, password;
    cout << "Enter username: ";
    cin >> username;
    cout << "Enter password: ";
    cin >> password;

    // Create a file for the user with the username as the file name
    ofstream userFile(username + ".txt");

    // Check if the file was created successfully
    if (userFile.is_open()) {
        userFile << username << endl;
        userFile << password << endl;
        userFile.close();
        cout << "Registration successful!" << endl;
    }
    else {
        cout << "Error creating user file. Registration failed." << endl;
    }
}

// Function to login a user
void loginUser() {
    string username, password, storedUsername, storedPassword;
    cout << "Enter username: ";
    cin >> username;
    cout << "Enter password: ";
    cin >> password;

    // Open the file for the user with the username as the file name
    ifstream userFile(username + ".txt");

    // Check if the file was opened successfully
    if (userFile.is_open()) {
        getline(userFile, storedUsername);
        getline(userFile, storedPassword);
        userFile.close();

        // Check if the entered credentials match the stored credentials
        if (username == storedUsername && password == storedPassword) {
            cout << "Login successful!" << endl;
        }
        else {
            cout << "Invalid username or password." << endl;
        }
    }
    else {
        cout << "User not found. Please register first." << endl;
    }
}

int main() {
    int choice;

    cout << "Welcome to the Login and Registration System" << endl;
    cout << "1. Register" << endl;
    cout << "2. Login" << endl;
    cout << "Enter your choice: ";
    cin >> choice;

    switch (choice) {
    case 1:
        registerUser();
        break;
    case 2:
        loginUser();
        break;
    default:
        cout << "Invalid choice." << endl;
        break;
    }

    return 0;
}
