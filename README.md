# Cheat Sheet Relational Algebra

---

### **Operasi Dasar**
| Notasi/Symbol   | Nama             | Deskripsi                                                                                             | Contoh                              |
|------------------|------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------|
| $\sigma$         | Selection        | Memilih baris dari sebuah relasi yang memenuhi kondisi tertentu.                                       | $\sigma_{usia > 30}(Karyawan)$     |
| $\pi$            | Projection       | Memilih kolom tertentu dari sebuah relasi.                                                            | $\pi_{nama, gaji}(Karyawan)$       |
| $\rho$           | Rename           | Mengubah nama relasi atau atribut untuk keperluan tertentu.                                           | $\rho_{KaryawanBaru}(Karyawan)$    |

---

### **Operasi Himpunan**
| Notasi/Symbol   | Nama             | Deskripsi                                                                                             | Contoh                              |
|------------------|------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------|
| $\cup$           | Union            | Menggabungkan semua tuple dari dua relasi (menghilangkan duplikasi).                                  | $A \cup B$                         |
| $\cap$           | Intersection     | Mengambil tuple yang ada di kedua relasi (irisan).                                                    | $A \cap B$                         |
| $-$              | Difference       | Mengambil tuple yang ada di satu relasi tetapi tidak ada di relasi lain.                              | $A - B$                            |

---

### **Operasi Join**
| Notasi/Symbol       | Nama                | Deskripsi                                                                                             | Contoh                              |
|----------------------|---------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------|
| $\bowtie$            | Natural Join        | Menggabungkan dua relasi berdasarkan atribut yang sama.                                               | $R \bowtie S$                      |
| $\ltimes$            | Left Outer Join     | Menyertakan semua tuple dari relasi kiri, dengan nilai null untuk tuple yang tidak cocok di relasi kanan. | $R \ltimes S$                      |
| $\rtimes$            | Right Outer Join    | Menyertakan semua tuple dari relasi kanan, dengan nilai null untuk tuple yang tidak cocok di relasi kiri. | $R \rtimes S$                      |
| $\bowtie_{cond}$     | Theta Join          | Menggabungkan dua relasi berdasarkan kondisi tertentu.                                                | $R \bowtie_{R.A = S.B} S$          |

---

### **Operasi Lanjutan**
| Notasi/Symbol   | Nama                 | Deskripsi                                                                                             | Contoh                              |
|------------------|----------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------|
| $\times$         | Cartesian Product    | Menghasilkan semua kombinasi tuple dari dua relasi.                                                  | $R \times S$                       |
| $\gamma$         | Group By            | Mengelompokkan tuple berdasarkan atribut tertentu dan menerapkan fungsi agregasi.                     | $\gamma_{dept, SUM(gaji)}(Karyawan)$ |
| $\delta$         | Duplicate Elimination | Menghilangkan tuple duplikat dalam sebuah relasi.                                                     | $\delta(Karyawan)$                 |

---

### **Operasi Turunan**
| Notasi/Symbol   | Nama                 | Deskripsi                                                                                             | Contoh                              |
|------------------|----------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------|
| $\theta$         | Conditional Join     | Menggabungkan tuple dari dua relasi yang memenuhi kondisi tertentu.                                   | $R \bowtie_{R.A < S.B} S$          |
| $\divide$        | Division             | Menghasilkan tuple dari satu relasi yang sesuai dengan semua tuple di relasi lain.                   | $R \divide S$                      |

---

### **Fungsi Agregasi**
| Fungsi  | Deskripsi                                                                                                   |
|---------|------------------------------------------------------------------------------------------------------------|
| SUM     | Menghitung jumlah total dari atribut numerik.                                                               |
| AVG     | Menghitung nilai rata-rata dari atribut numerik.                                                            |
| MAX     | Menentukan nilai maksimum dalam sebuah atribut.                                                             |
| MIN     | Menentukan nilai minimum dalam sebuah atribut.                                                              |
| COUNT   | Menghitung jumlah tuple dalam sebuah relasi.                                                                |

---

# CONTOH IMPLEMENTASI

---

### **Relasi Awal**
#### Relasi `Karyawan`
| id_karyawan | nama       | usia | id_departemen | gaji  |
|-------------|------------|------|---------------|-------|
| 1           | Andi       | 35   | 101           | 15000 |
| 2           | Budi       | 28   | 102           | 12000 |
| 3           | Citra      | 40   | 101           | 18000 |
| 4           | Diana      | 25   | 103           | 10000 |

#### Relasi `Departemen`
| id_departemen | nama_departemen |
|---------------|-----------------|
| 101           | IT              |
| 102           | HR              |
| 103           | Finance         |

#### Relasi `Proyek`
| id_proyek | nama_proyek | id_departemen | budget |
|-----------|-------------|---------------|--------|
| 1         | Proyek A    | 101           | 20000  |
| 2         | Proyek B    | 103           | 15000  |
| 3         | Proyek C    | 102           | 10000  |

---

### **Operasi Dasar**
1. **Selection ($\sigma$)**  
   **Query:** $\sigma_{usia > 30}(Karyawan)$  
   **Deskripsi:** Pilih karyawan dengan usia lebih dari 30 tahun.  
   **Hasil:**
   | id_karyawan | nama   | usia | id_departemen | gaji  |
   |-------------|--------|------|---------------|-------|
   | 1           | Andi   | 35   | 101           | 15000 |
   | 3           | Citra  | 40   | 101           | 18000 |

2. **Projection ($\pi$)**  
   **Query:** $\pi_{nama, gaji}(Karyawan)$  
   **Deskripsi:** Tampilkan hanya kolom `nama` dan `gaji`.  
   **Hasil:**
   | nama  | gaji  |
   |-------|-------|
   | Andi  | 15000 |
   | Budi  | 12000 |
   | Citra | 18000 |
   | Diana | 10000 |

3. **Rename ($\rho$)**  
   **Query:** $\rho_{KaryawanBaru}(Karyawan)$  
   **Deskripsi:** Ganti nama relasi `Karyawan` menjadi `KaryawanBaru`.  
   **Hasil:** Sama dengan tabel `Karyawan` tetapi dengan nama baru.

---

### **Operasi Himpunan**
1. **Union ($\cup$)**  
   Misalkan ada relasi tambahan:  
   #### Relasi `Karyawan_Cabang2`
   | id_karyawan | nama       | usia | id_departemen | gaji  |
   |-------------|------------|------|---------------|-------|
   | 5           | Eko        | 30   | 104           | 11000 |
   | 3           | Citra      | 40   | 101           | 18000 |

   **Query:** $Karyawan \cup Karyawan\_Cabang2$  
   **Hasil:**  
   | id_karyawan | nama   | usia | id_departemen | gaji  |
   |-------------|--------|------|---------------|-------|
   | 1           | Andi   | 35   | 101           | 15000 |
   | 2           | Budi   | 28   | 102           | 12000 |
   | 3           | Citra  | 40   | 101           | 18000 |
   | 4           | Diana  | 25   | 103           | 10000 |
   | 5           | Eko    | 30   | 104           | 11000 |

2. **Intersection ($\cap$)**  
   **Query:** $Karyawan \cap Karyawan\_Cabang2$  
   **Hasil:**  
   | id_karyawan | nama   | usia | id_departemen | gaji  |
   |-------------|--------|------|---------------|-------|
   | 3           | Citra  | 40   | 101           | 18000 |

3. **Difference ($-$)**  
   **Query:** $Karyawan - Karyawan\_Cabang2$  
   **Hasil:**  
   | id_karyawan | nama   | usia | id_departemen | gaji  |
   |-------------|--------|------|---------------|-------|
   | 1           | Andi   | 35   | 101           | 15000 |
   | 2           | Budi   | 28   | 102           | 12000 |
   | 4           | Diana  | 25   | 103           | 10000 |

---

### **Operasi Join**
1. **Natural Join ($\bowtie$)**  
   **Query:** $Karyawan \bowtie Departemen$  
   **Deskripsi:** Gabungkan karyawan dengan departemen berdasarkan `id_departemen`.  
   **Hasil:**
   | id_karyawan | nama   | usia | id_departemen | gaji  | nama_departemen |
   |-------------|--------|------|---------------|-------|-----------------|
   | 1           | Andi   | 35   | 101           | 15000 | IT              |
   | 2           | Budi   | 28   | 102           | 12000 | HR              |
   | 3           | Citra  | 40   | 101           | 18000 | IT              |
   | 4           | Diana  | 25   | 103           | 10000 | Finance         |

2. **Theta Join ($\bowtie_{cond}$)**  
   **Query:** $Karyawan \bowtie_{gaji > budget} Proyek$  
   **Deskripsi:** Gabungkan karyawan dengan proyek jika `gaji > budget`.  
   **Hasil:**
   | id_karyawan | nama   | usia | id_departemen | gaji  | id_proyek | nama_proyek | id_departemen | budget |
   |-------------|--------|------|---------------|-------|-----------|-------------|---------------|--------|
   | 3           | Citra  | 40   | 101           | 18000 | 2         | Proyek B    | 103           | 15000 |

---

### **Operasi Lanjutan**
1. **Group By ($\gamma$)**  
   **Query:** $\gamma_{id_departemen, SUM(gaji)}(Karyawan)$  
   **Deskripsi:** Hitung total gaji untuk setiap departemen.  
   **Hasil:**
   | id_departemen | total_gaji |
   |---------------|------------|
   | 101           | 33000      |
   | 102           | 12000      |
   | 103           | 10000      |

2. **Division ($\divide$)**  
   Misalkan relasi `Proyek_Wajib` memiliki:  
   #### Relasi `Proyek_Wajib`
   | id_proyek |
   |-----------|
   | 1         |
   | 2         |

   **Query:** $Karyawan \divide Proyek\_Wajib$  
   **Deskripsi:** Cari karyawan yang bekerja di semua proyek wajib (Proyek A dan B).  
   **Hasil:**
   | id_karyawan | nama   |
   |-------------|--------|
   | (kosong)    | Tidak ada karyawan yang bekerja di semua proyek wajib. |

---

Semoga contoh ini membantu! Jika Anda butuh penjelasan tambahan, beri tahu saya. 😊
