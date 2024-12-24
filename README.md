# calculate-grade-for-collage
this is a... grade calculate with c++ :D
## how to use
```bash
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