# TUGAS SISTEM OPERASI 

---

![Image](https://github.com/user-attachments/assets/838b068c-4d85-452a-aca6-352d279fbd3f)

#### Dosen Pengampu :
**Dr. Ferry Astika Saputra ST, M.Sc**

#### Dibuat oleh :
**Aldino Maytata Prandila**
**(3214521014)**
D3-LA IT-A

---

## Soal

Diketahui proses-proses berikut datang untuk dieksekusi pada waktu yang ditentukan. 
Setiap proses memiliki waktu burst seperti yang tertera. 
Gunakan algoritma penjadwalan **Shortest Job First (SJF) non-preemptive** untuk menjawab pertanyaan berikut. 
Hitung waktu tunggu rata-rata dan waktu turnaround rata-rata untuk seluruh proses.

| Proses | Waktu Kedatangan | Burst Time |
|--------|------------------|------------|
| P₁     | 0.0              | 7          |
| P₂     | 2.0              | 4          |
| P₃     | 4.0              | 1          |
| P₄     | 5.0              | 4          |

---
## jawab

## 1. Shortest Job First (SJF) - Non-Preemptive

### Urutan Eksekusi:
- P₁ (0–7)
- P₃ (7–8)
- P₂ (8–12)
- P₄ (12–16)

| Proses | Mulai | Selesai | Waiting Time | Turnaround Time |
|--------|-------|---------|---------------|------------------|
| P₁     | 0     | 7       | 0             | 7                |
| P₃     | 7     | 8       | 3             | 4                |
| P₂     | 8     | 12      | 6             | 10               |
| P₄     | 12    | 16      | 7             | 11               |

**Rata-rata:**
- Waiting Time: 4
- Turnaround Time: 8

---

## 2. Shortest Job First (SJF) - Preemptive

### Simulasi Eksekusi:
- 0-2: P₁ (sisa 5)
- 2-4: P₂ (sisa 2)
- 4-5: P₃ (selesai)
- 5-7: P₂ (selesai)
- 7-11: P₄ (selesai)
- 11-16: P₁ (selesai)

| Proses | Selesai | Waiting Time | Turnaround Time |
|--------|---------|---------------|------------------|
| P₁     | 16      | 9             | 16               |
| P₂     | 7       | 1             | 5                |
| P₃     | 5       | 0             | 1                |
| P₄     | 11      | 2             | 6                |

**Rata-rata:**
- Waiting Time: 3
- Turnaround Time: 7

---

## 3. First Come First Serve (FCFS)

### Urutan: P₁ → P₂ → P₃ → P₄

| Proses | Mulai | Selesai | Waiting Time | Turnaround Time |
|--------|-------|---------|---------------|------------------|
| P₁     | 0     | 7       | 0             | 7                |
| P₂     | 7     | 11      | 5             | 9                |
| P₃     | 11    | 12      | 7             | 8                |
| P₄     | 12    | 16      | 7             | 11               |

**Rata-rata:**
- Waiting Time: 4.75
- Turnaround Time: 8.75

---

## 4. Round Robin (Quantum = 2)

### Simulasi Eksekusi:
- 0-2: P₁ (sisa 5)
- 2-4: P₂ (sisa 2)
- 4-5: P₃ (selesai)
- 5-6: P₁ (sisa 4)
- 6-8: P₄ (sisa 2)
- 8-10: P₁ (sisa 2)
- 10-12: P₂ (selesai)
- 12-14: P₄ (selesai)
- 14-16: P₁ (selesai)

| Proses | Selesai | Waiting Time | Turnaround Time |
|--------|---------|---------------|------------------|
| P₁     | 16      | 9             | 16               |
| P₂     | 12      | 6             | 10               |
| P₃     | 5       | 0             | 1                |
| P₄     | 14      | 5             | 9                |

**Rata-rata:**
- Waiting Time: 5
- Turnaround Time: 9

---

## Ringkasan Perbandingan

| Algoritma          | Avg Waiting Time | Avg Turnaround Time |
|--------------------|------------------|----------------------|
| SJF Non-Preemptive | 4                | 8                    |
| SJF Preemptive     | **3**            | **7**                |
| FCFS               | 4.75             | 8.75                 |
| Round Robin (Q=2)  | 5                | 9                    |

---

