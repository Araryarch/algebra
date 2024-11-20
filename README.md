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

Semoga cheat sheet ini membantu! Jika ada yang ingin dijelaskan lebih detail, beri tahu saya. 😊
