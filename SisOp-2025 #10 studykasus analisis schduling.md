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

## Soal 5.3

### Data Proses:

| Process | Arrival Time | Burst Time |
| ------- | ------------ | ---------- |
| P₁      | 0.0          | 8          |
| P₂      | 0.4          | 4          |
| P₃      | 1.0          | 1          |

Dari soal 5.3 ini, kita akan melakukan simulasi menggunakan 3 algoritma:

1. **SJF Non-Preemptive tanpa arrival time**
2. **SJF Non-Preemptive dengan arrival time**
3. **SRTF (Shortest Remaining Time First)**

Seperti pada kasus pertemuan sebelumnya.

---

## 1. SJF Non-Preemptive (Tanpa Arrival Time)

### Asumsi:

* Semua proses diasumsikan datang pada waktu 0.
* Pemilihan proses berdasarkan burst time terkecil terlebih dahulu.

### Urutan Eksekusi Berdasarkan Burst Time:

| Process | Burst Time |
| ------- | ---------- |
| P₃      | 1          |
| P₂      | 4          |
| P₁      | 8          |

### Gantt Chart:

```
| 0 |--P₃--| 1 |--P₂--| 5 |--P₁--| 13 |
```

### Perhitungan:

| Process | Waiting Time | Turnaround Time |
| ------- | ------------ | --------------- |
| P₃      | 0            | 1               |
| P₂      | 1            | 5               |
| P₁      | 5            | 13              |

**Rata-rata:**

* 🕓 Waiting Time: (0 + 1 + 5) / 3 = **2.0**
* 🕓 Turnaround Time: (1 + 5 + 13) / 3 = **6.33**

---

## 2. SJF Non-Preemptive (Dengan Arrival Time)

### Pertimbangan Arrival Time:

| Process | Arrival | Burst |
| ------- | ------- | ----- |
| P₁      | 0.0     | 8     |
| P₂      | 0.4     | 4     |
| P₃      | 1.0     | 1     |

### Gantt Chart:

```
| 0 |--P₁--| 8 |--P₃--| 9 |--P₂--| 13 |
```

### Perhitungan:

| Process | Arrival | Start | Waiting | Completion | Turnaround |
| ------- | ------- | ----- | ------- | ---------- | ---------- |
| P₁      | 0.0     | 0.0   | 0.0     | 8.0        | 8.0        |
| P₃      | 1.0     | 8.0   | 7.0     | 9.0        | 8.0        |
| P₂      | 0.4     | 9.0   | 8.6     | 13.0       | 12.6       |

**Rata-rata:**

*  Waiting Time: (0 + 7 + 8.6) / 3 = **5.2**
*  Turnaround Time: (8 + 8 + 12.6) / 3 = **9.53**

---

##  3. SRTF (Shortest Remaining Time First - Preemptive)

###  Gantt Chart:

```
| 0.0 |--P₁--| 0.4 |--P₂--| 1.0 |--P₃--| 2.0 |--P₂--| 6.0 |--P₁--| 14.0 |
```

### Perhitungan:

| Process | Arrival | Completion | Turnaround | Waiting |
| ------- | ------- | ---------- | ---------- | ------- |
| P₁      | 0.0     | 14.0       | 14.0       | 6.0     |
| P₂      | 0.4     | 6.0        | 5.6        | 1.6     |
| P₃      | 1.0     | 2.0        | 1.0        | 0.0     |

**Rata-rata:**

* 🕓 Waiting Time: (6 + 1.6 + 0) / 3 = **2.53**
* 🕓 Turnaround Time: (14 + 5.6 + 1) / 3 = **6.87**

---

##  Soal 5.4: Priority Scheduling (Non-Preemptive)

### Data Proses:

| Process | Burst Time | Priority |
| ------- | ---------- | -------- |
| P₁      | 2          | 2        |
| P₂      | 1          | 1 (🔼)   |
| P₃      | 8          | 4        |
| P₄      | 4          | 2        |
| P₅      | 5          | 3        |

> *Semakin kecil angka priority, semakin tinggi prioritasnya.*

### Urutan Eksekusi Berdasarkan Prioritas:

1. P₂ (Priority 1)
2. P₁ (Priority 2)
3. P₄ (Priority 2)
4. P₅ (Priority 3)
5. P₃ (Priority 4)

### Gantt Chart:

```
| 0 |--P₂--| 1 |--P₁--| 3 |--P₄--| 7 |--P₅--| 12 |--P₃--| 20 |
```

### Perhitungan:

| Process | Burst | Priority | Start | Completion | Waiting | Turnaround |
| ------- | ----- | -------- | ----- | ---------- | ------- | ---------- |
| P₂      | 1     | 1        | 0     | 1          | 0       | 1          |
| P₁      | 2     | 2        | 1     | 3          | 1       | 3          |
| P₄      | 4     | 2        | 3     | 7          | 3       | 7          |
| P₅      | 5     | 3        | 7     | 12         | 7       | 12         |
| P₃      | 8     | 4        | 12    | 20         | 12      | 20         |

**Rata-rata:**

*  Waiting Time: (0 + 1 + 3 + 7 + 12) / 5 = **4.6**
*  Turnaround Time: (1 + 3 + 7 + 12 + 20) / 5 = **8.6**

---
