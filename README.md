# codsoft_3

//Develop a program that simulates a movie ticket booking system.
Allow users to view movie listings, select seats, make bookings,
and calculate the total cost. Consider implementing seat
availability and seat selection validation.






#include <iostream>
#include <vector>

using namespace std;

const int NUM_ROWS = 5;    // Number of rows in the theater
const int NUM_COLS = 10;   // Number of seats per row

// Function to display the seating chart
void displaySeatingChart(const vector<vector<bool>>& seats) {
    cout << "Seating Chart:" << endl;
    for (int row = 0; row < NUM_ROWS; row++) {
        for (int col = 0; col < NUM_COLS; col++) {
            if (seats[row][col]) {
                cout << "X "; // Seat is taken
            } else {
                cout << "O "; // Seat is available
            }
        }
        cout << endl;
    }
}

int main() {
    vector<vector<bool>> seats(NUM_ROWS, vector<bool>(NUM_COLS, false)); // Initialize all seats as available

    while (true) {
        int row, col;
        displaySeatingChart(seats);

        // User input for seat selection
        cout << "Enter row and column (e.g., 1 2) or -1 to exit: ";
        cin >> row >> col;

        if (row == -1) {
            break; // Exit the program
        }

        if (row < 1 || row > NUM_ROWS || col < 1 || col > NUM_COLS) {
            cout << "Invalid seat selection. Please try again." << endl;
            continue;
        }

        // Check seat availability
        if (seats[row - 1][col - 1]) {
            cout << "Seat already taken. Please select another seat." << endl;
        } else {
            seats[row - 1][col - 1] = true; // Mark the seat as taken
            cout << "Seat " << row << " " << col << " booked successfully!" << endl;
        }
    }

    return 0;
}
