---

# **CHEAT SHEET: RELATIONAL ALGEBRA**

---

## **1. Operasi Dasar**

| **Notasi**    | **Nama**          | **Deskripsi**                                                                              | **Contoh**                             |
|----------------|-------------------|------------------------------------------------------------------------------------------|----------------------------------------|
| $\sigma$       | **Selection**     | Memilih **baris** dari relasi yang memenuhi kondisi tertentu.                             | $\sigma_{usia > 30}(Karyawan)$        |
| $\pi$          | **Projection**    | Memilih **kolom** tertentu dari relasi.                                                   | $\pi_{nama, gaji}(Karyawan)$          |
| $\rho$         | **Rename**        | Mengganti nama **relasi** atau **atribut** untuk kejelasan atau keperluan tertentu.        | $\rho_{KaryawanBaru}(Karyawan)$       |

---

## **2. Operasi Himpunan**

| **Notasi**     | **Nama**           | **Deskripsi**                                                                              | **Contoh**                             |
|-----------------|--------------------|------------------------------------------------------------------------------------------|----------------------------------------|
| $\cup$          | **Union**          | Menggabungkan **semua tuple** dari dua relasi, tanpa duplikasi.                           | $A \cup B$                            |
| $\cap$          | **Intersection**   | Mengambil **irisan tuple**, yaitu yang ada di kedua relasi.                               | $A \cap B$                            |
| $-$             | **Difference**     | Mengambil **tuple yang unik** di satu relasi dibandingkan relasi lain.                    | $A - B$                               |

---

## **3. Operasi Join**

| **Notasi**            | **Nama**             | **Deskripsi**                                                                                   | **Contoh**                                  |
|------------------------|----------------------|-----------------------------------------------------------------------------------------------|---------------------------------------------|
| $\bowtie$              | **Natural Join**     | Menggabungkan dua relasi berdasarkan atribut yang sama (common attributes).                    | $R \bowtie S$                               |
| $\bowtie_{cond}$       | **Theta Join**       | Menggabungkan dua relasi berdasarkan kondisi tertentu.                                          | $R \bowtie_{R.A > S.B} S$                   |
| $\ltimes$              | **Left Outer Join**  | Menggabungkan relasi dengan semua tuple dari relasi kiri, menyertakan **null** jika tidak cocok. | $R \ltimes S$                               |
| $\rtimes$              | **Right Outer Join** | Menggabungkan relasi dengan semua tuple dari relasi kanan, menyertakan **null** jika tidak cocok.| $R \rtimes S$                               |

---

## **4. Operasi Lanjutan**

| **Notasi**   | **Nama**              | **Deskripsi**                                                                               | **Contoh**                                  |
|--------------|-----------------------|-------------------------------------------------------------------------------------------|---------------------------------------------|
| $\times$     | **Cartesian Product** | Menghasilkan kombinasi semua tuple dari dua relasi (tanpa kondisi).                        | $R \times S$                                |
| $\gamma$     | **Group By**          | Mengelompokkan tuple berdasarkan atribut tertentu, sering disertai fungsi agregasi.        | $\gamma_{dept, SUM(gaji)}(Karyawan)$        |
| $\delta$     | **Duplicate Elimination** | Menghilangkan **tuple duplikat** dalam sebuah relasi.                                      | $\delta(Karyawan)$                          |
| $\divide$    | **Division**          | Menghasilkan tuple yang memenuhi semua atribut relasi pembagi.                             | $R \divide S$                               |

---

## **5. Fungsi Agregasi**

| **Fungsi** | **Deskripsi**                       | **Contoh**                             |
|------------|------------------------------------|----------------------------------------|
| SUM        | Menghitung total nilai atribut.    | $\gamma_{SUM(gaji)}(Karyawan)$         |
| AVG        | Menghitung rata-rata nilai.        | $\gamma_{AVG(gaji)}(Karyawan)$         |
| MAX        | Menemukan nilai maksimum.          | $\gamma_{MAX(gaji)}(Karyawan)$         |
| MIN        | Menemukan nilai minimum.           | $\gamma_{MIN(gaji)}(Karyawan)$         |
| COUNT      | Menghitung jumlah tuple.           | $\gamma_{COUNT(id_karyawan)}(Karyawan)$|

---

## **6. Contoh Implementasi**

### **Relasi Awal**

**Relasi `Karyawan`**  
| id_karyawan | nama       | usia | id_departemen | gaji  |
|-------------|------------|------|---------------|-------|
| 1           | Andi       | 35   | 101           | 15000 |
| 2           | Budi       | 28   | 102           | 12000 |
| 3           | Citra      | 40   | 101           | 18000 |
| 4           | Diana      | 25   | 103           | 10000 |

**Relasi `Departemen`**  
| id_departemen | nama_departemen |
|---------------|-----------------|
| 101           | IT              |
| 102           | HR              |
| 103           | Finance         |

---

### **Operasi Dasar**

1. **Selection ($\sigma$)**  
   **Query:** $\sigma_{usia > 30}(Karyawan)$  
   **Hasil:**  
   | id_karyawan | nama   | usia | id_departemen | gaji  |
   |-------------|--------|------|---------------|-------|
   | 1           | Andi   | 35   | 101           | 15000 |
   | 3           | Citra  | 40   | 101           | 18000 |

2. **Projection ($\pi$)**  
   **Query:** $\pi_{nama, gaji}(Karyawan)$  
   **Hasil:**  
   | nama  | gaji  |
   |-------|-------|
   | Andi  | 15000 |
   | Budi  | 12000 |
   | Citra | 18000 |
   | Diana | 10000 |

---

### **Operasi Join**

1. **Natural Join ($\bowtie$)**  
   **Query:** $Karyawan \bowtie Departemen$  
   **Hasil:**  
   | id_karyawan | nama   | usia | id_departemen | gaji  | nama_departemen |
   |-------------|--------|------|---------------|-------|-----------------|
   | 1           | Andi   | 35   | 101           | 15000 | IT              |
   | 2           | Budi   | 28   | 102           | 12000 | HR              |
   | 3           | Citra  | 40   | 101           | 18000 | IT              |
   | 4           | Diana  | 25   | 103           | 10000 | Finance         |

---

### **Group By ($\gamma$)**  
**Query:** $\gamma_{id_departemen, SUM(gaji)}(Karyawan)$  
**Hasil:**  
| id_departemen | total_gaji |
|---------------|------------|
| 101           | 33000      |
| 102           | 12000      |
| 103           | 10000      |

---

### **Union dan Difference**

**Union ($\cup$)**  
**Query:** $Karyawan \cup Karyawan\_Cabang2$  
Menggabungkan karyawan dari dua cabang.

**Difference ($-$)**  
**Query:** $Karyawan - Karyawan\_Cabang2$  
Mengambil karyawan yang hanya ada di cabang utama.

---
