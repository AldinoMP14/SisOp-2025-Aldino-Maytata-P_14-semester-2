# TUGAS SISTEM OPERASI 5

---

![Image](https://github.com/user-attachments/assets/838b068c-4d85-452a-aca6-352d279fbd3f)

#### Dosen Pengampu :
**Dr. Ferry Astika Saputra ST, M.Sc**

#### Disusun oleh :
**Aldino Maytata Prandila**
**(3214521014)**
D3-LA IT-A

<br>

---
>TUGAS
>- Memberikan komentar flop/iops
> https://github.com/ferryastika/flops-iops
>
---

<br>

1.	            $ make
    Output:

        gcc -lpthread -Wno-overflow -pthread -o flops32 BenchmarkFLOPS32.c
        gcc -lpthread -Wno-overflow -pthread -o flops64 BenchmarkFLOPS64.c
        gcc -lpthread -Wno-overflow -pthread -o iops32 BenchmarkIOPS32.c
        gcc -lpthread -Wno-overflow -pthread -o iops64 BenchmarkIOPS64.c

    Komentar Saya:
    Dengan command $make kita bisa melihat menu yang dapat dijalankan. dan Program ini dikompilasi dengan dukungan multi-threading, yaitu (-lpthread dan -pthread)

<br>

---

2.	            $./flops64 $(nproc)
    Output:

        Benchmarking for 64 Bit Floating point operations per second
        || Tr 1: 2184646256 Tr 2: 2167311822 FLOPS = 4351958078
        Maximum CPU Throughput: 4.351958 Gigaflops.
        Maximum Single Core Throughput: 2.184646 Gigaflops.

    Komentar Saya:
Command ini untuk mengukur kinerja yang ada pada CPU dalam komputasi berbasis floating-point (yg biasa digunakan pada AI).

    1. Benchmarking for 64 Bit Floating point operations per second, Pengujian ini mengukur seberapa cepat CPU menangani operasi floating-point 64-bit.
   
    2. Tr 1: 218,464,265 | Tr 2: 216,731,182 | FLOPS = 435,195,8078, Jumlah operasi floating-point yang dieksekusi dalam dua tahap (Tr 1 dan Tr 2), Total FLOPS = 4.35 GigaFLOPS (4,351,958,078 operasi per detik).
 
    3. Maximum CPU Throughput: 4.35 Gigaflops, Kinerja maksimum CPU dalam menangani operasi floating-point. Maximum Single Core Throughput: 2.18 Gigaflops Kinerja maksimum per core dari CPU Anda.
   
<br>

---

3.	        $./iops64 $(nproc)
    Output:

        Benchmarking for 64 Bit Integer operations per second
        || Tr 1: 1933910914 Tr 2: 1960510786 IOPS = 3894421700
        Maximum CPU Throughput: 3.894422 Gigaiops.
        Maximum Single Core Throughput: 1.960511 Gigaiops.

    Komentar Saya:
Command ini berguna untuk menilai performa CPU dalam pemrosesan data numerik berbasis bilangan bulat menangani tugas integer-heavy seperti kriptografi atau database.
    
    1. Tr 1: 1933910914 dan Tr 2: 1960510786 Menunjukkan jumlah operasi integer/INT 64bit yang dihitung dalam dua tahap pengujian

    2. IOPS = 3894421700 Total jumlah operasi INT 64bit yang dilakukan perdetik 3,8 milyar operasi perdetik (3,8 GigaIOPS)

    3. Maximum CPU Throughput:  3,894422 Gigaiops kapasitas maksimum CPU dalam menangani operasi integer 64bit secara keseluruhan menggunakan semua core yang tersedia

    4. Maximum Single Core Throughput: 1.960511 GigaIops. kapasitas maksimum satu core CPU dalam menangani operasi integer 64bit
   
