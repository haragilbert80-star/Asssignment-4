#include <iostream>
#include <iomanip>
#include <cstring>
using namespace std;

// Function to print the seat map
void print_seat(int **seat, int row, int col) {
    for (int i = 0; i < row; i++) {
        for (int j = 0; j < col; j++) {
            cout << setfill('0') << setw(2) << seat[i][j];
            if (j < col - 1) cout << " ";
        }
        cout << endl;
    }
}

int main() {
    const int ROW = 10;
    const int COL = 10;

    // 1. Dynamically allocate 10x10 integer array
    int **seat = new int*[ROW];
    for (int i = 0; i < ROW; i++) {
        seat[i] = new int[COL];
    }

    // Initialize the whole array to 0 using memset
    for (int i = 0; i < ROW; i++) {
        memset(seat[i], 0, COL * sizeof(int));
    }

    // Assign values to specific seats
    seat[0][0] = 11;
    seat[0][3] = 24;
    seat[1][1] = 35;
    seat[2][5] = 47;
    seat[3][3] = 58;
    seat[4][9] = 69;
    seat[5][0] = 70;
    seat[5][5] = 81;
    seat[5][9] = 92;
    seat[6][4] = 13;
    seat[7][7] = 26;
    seat[8][2] = 39;
    seat[9][9] = 44;

    // Print the original seat map
    cout << "[Original Seat Map]" << endl;
    print_seat(seat, ROW, COL);
    cout << endl;

    // 3. Create another dynamically allocated 10x10 array named backup
    int **backup = new int*[ROW];
    for (int i = 0; i < ROW; i++) {
        backup[i] = new int[COL];
    }

    // Copy the original seat map into backup using memcpy (row by row)
    for (int i = 0; i < ROW; i++) {
        memcpy(backup[i], seat[i], COL * sizeof(int));
    }

    cout << "[Backup Seat Map]" << endl;
    print_seat(backup, ROW, COL);
    cout << endl;

    // 4. Clear entire row 5 in the original seat map only
    memset(seat[5], 0, COL * sizeof(int));

    cout << "[Original Seat Map After Clearing Row 5]" << endl;
    print_seat(seat, ROW, COL);
    cout << endl;

    cout << "[Backup Seat Map After Original Was Modified]" << endl;
    print_seat(backup, ROW, COL);
    cout << endl;

    // 5. Find the row with the largest number of assigned seats in backup
    int maxCount = 0;
    int maxRow = 0;

    for (int i = 0; i < ROW; i++) {
        int count = 0;
        for (int j = 0; j < COL; j++) {
            if (backup[i][j] != 0) {
                count++;
            }
        }
        if (count > maxCount) {
            maxCount = count;
            maxRow = i;
        }
    }

    cout << "[Row With Most Assigned Seats]" << endl;
    cout << "Row: " << maxRow << endl;
    cout << "Count: " << maxCount << endl;
    cout << endl;

    // Release all dynamically allocated memory
    for (int i = 0; i < ROW; i++) {
        delete[] seat[i];
        delete[] backup[i];
    }
    delete[] seat;
    delete[] backup;

    cout << "All memory released successfully!" << endl;

    return 0;
}
