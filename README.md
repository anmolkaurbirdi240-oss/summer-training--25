#include <iostream>
#include <fstream>
#include <string>
using namespace std;

class Student {
public:
    int roll;
    string name;
    float marks;

    void addStudent() {
        cout << "Enter Roll Number: ";
        cin >> roll;
        cin.ignore();

        cout << "Enter Name: ";
        getline(cin, name);

        cout << "Enter Marks: ";
        cin >> marks;

        ofstream file("students.txt", ios::app);
        file << roll << " " << name << " " << marks << endl;
        file.close();

        cout << "\nStudent Added Successfully!\n";
    }

    void displayStudents() {
        ifstream file("students.txt");

        cout << "\n----- Student Records -----\n";

        while (file >> roll) {
            file.ignore();
            getline(file, name, ' ');
            file >> marks;

            cout << "Roll: " << roll << endl;
            cout << "Name: " << name << endl;
            cout << "Marks: " << marks << endl;
            cout << "--------------------------\n";
        }

        file.close();
    }
};

int main() {
    Student s;
    int choice;

    do {
        cout << "\n===== Student Management System =====\n";
        cout << "1. Add Student\n";
        cout << "2. Display Students\n";
        cout << "3. Exit\n";
        cout << "Enter Choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                s.addStudent();
                break;
            case 2:
                s.displayStudents();
                break;
            case 3:
                cout << "Thank You!\n";
                break;
            default:
                cout << "Invalid Choice!\n";
        }
    } while (choice != 3);

    return 0;
}
