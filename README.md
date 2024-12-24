# calculate-grade-for-collage
this is a... grade calculate with c++ :D
## how to use
```cpp
#include <iostream>
#include <string>
#include <iomanip>

using namespace std;

void table(int nim[], string nama[], float tugas[], float uts[], float uas[], float nilai_akhir[], int brpMhs)
{
    // Print table header
    cout << left << setw(5) << "No" << setw(15) << "NIM" << setw(25) << "Nama Mahasiswa" 
         << setw(15) << "Tugas" << setw(15) << "UTS" << setw(15) << "UAS" << "Nilai Akhir" << endl;
    cout << "----------------------------------------------------------------------------------------------------------------------" << endl;
    
    // Print table rows
    for (int i = 0; i < brpMhs; i++) {
        cout << left << setw(5) << i + 1 
             << setw(15) << nim[i] 
             << setw(25) << nama[i] 
             << setw(15) << fixed << setprecision(2) << tugas[i] 
             << setw(15) << fixed << setprecision(2) << uts[i] 
             << setw(15) << fixed << setprecision(2) << uas[i] 
             << fixed << setprecision(2) << nilai_akhir[i] << endl;
    }
    
    // Calculate and display the average of all students' final grades
    float total_nilai = 0;
    for (int i = 0; i < brpMhs; i++) {
        total_nilai += nilai_akhir[i];
    }
    float rata_rata = total_nilai / brpMhs;
    cout << endl << "Rata-rata Nilai Akhir: " << fixed << setprecision(2) << rata_rata << endl;
}

int main()
{
    float tugas = 0.3, uts = 0.3, uas = 0.4;
    float nilai_akhir, nilTugas, nilUts, nilUas;
    int brpMhs;

    // Input jumlah mahasiswa
    cout << "Masukkan jumlah mahasiswa: "; 
    cin >> brpMhs;
    cout << endl;

    // Declare arrays after brpMhs is input
    int nim[brpMhs];
    string namaMhs[brpMhs];
    float nilaiAkhir[brpMhs];
    float nilaiTugas[brpMhs], nilaiUts[brpMhs], nilaiUas[brpMhs];

    // Loop to input data for each student
    for (int i = 0; i < brpMhs; i++) {
        cin.ignore();  // To ignore the newline character after reading brpMhs
        
        // Input student name
        cout << "Masukkan Nama Mahasiswa ke-" << i + 1 << ": ";
        getline(cin, namaMhs[i]);
        
        // Input NIM
        cout << "Masukkan NIM Mahasiswa ke-" << i + 1 << ": ";
        cin >> nim[i];
        
        // Input grades
        cout << "Masukkan nilai tugas: "; 
        cin >> nilTugas;
        cout << "Masukkan nilai uts: "; 
        cin >> nilUts;
        cout << "Masukkan nilai uas: "; 
        cin >> nilUas;
        cout << endl;
        
        // Store individual grades
        nilaiTugas[i] = nilTugas;
        nilaiUts[i] = nilUts;
        nilaiUas[i] = nilUas;
        
        // Calculate final grade
        nilai_akhir = (nilTugas * tugas) + (nilUts * uts) + (nilUas * uas);
        nilaiAkhir[i] = nilai_akhir;  // Store final grade in array
    }

    // Call table function to display data
    table(nim, namaMhs, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir, brpMhs);

    return 0;
}
```
# Running
- run and compile the code in your preferred IDE or compiler
- input the number of students, their names, NIM, and grades
- the program will display a table with the input data and the final grade for each student.

# Example Use Cases
```bash
Input data for 3 students

Nama Mahasiswa 1: John Doe
NIM: 123456
nilai tugas: 80
nilai uts: 90
nilai uas: 85

Nama Mahasiswa 2: Jane Doe
NIM: 234567
nilai tugas: 70
nilai uts: 80
nilai uas: 90

Nama Mahasiswa 3: Bob Smith
NIM: 345678
nilai tugas: 90
nilai uts: 95
nilai uas: 92
```
- The program will display a table with the input data and the final grade for each student. 
```bash
No   NIM            Nama Mahasiswa           Tugas          UTS            UAS            Nilai Akhir
----------------------------------------------------------------------------------------------------------------------
1    123456         John Doe                 80.00          90.00          85.00          85.00
2    234567         Jane Doe                 70.00          80.00          90.00          81.00
3    345678         Bob Smith                90.00          95.00          92.00          92.30

Rata-rata Nilai Akhir: 86.10
```
# Note
- The code uses a simple array to store the input data and the final grades.
- The table function is not implemented in this code, you need to implement it according to your needs.
- The code assumes that the input data is valid and does not contain any errors.