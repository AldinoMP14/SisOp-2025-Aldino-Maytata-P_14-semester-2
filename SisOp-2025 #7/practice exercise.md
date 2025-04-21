# TUGAS SISTEM OPERASI 

---

![Image](https://github.com/user-attachments/assets/838b068c-4d85-452a-aca6-352d279fbd3f)

#### Dosen Pengampu :
**Dr. Ferry Astika Saputra ST, M.Sc**

#### Disusun oleh :
**Aldino Maytata Prandila**
**(3214521014)**
D3-LA IT-A

---

## Practice Exercises Chapter 4

---

## 4.1 Provide three programming examples in which multithreading provides better performance than a single-threaded solution.

    - **Web Server**
    Web server seperti **Apache** sering menerima request dari client secara bersamaan. Oleh sebab itu, apabila menggunakan **Multithreading** setiap permintaan nantinya bisa diproses di **thread** masing-masing secara terpisah.
    
    - **Audio/Video Streaming**
    Pada saat menonton video/mendengarkan musik di platform-platform tertentu, terdapat juga proses yang berjalan dibaliknya. Oleh sebab itu, ***Multithreading*** dimanfaatkan agar satu **thread** bisa menguduh, satu lagi memproses decoding, satu lagi mengelola output, sehingga nanti hasil dari playback platform tersebut berjalan dengan lancar tanpa ada kendala.
    
    - **Game Development**
    Pada pengembangan sebuah game, terjadi banyak proses berjalan secara bersamaan. Oleh sebab itu, ***Multithreading*** dapat menjadi solusi untuk pengembangan sebuah game. Karena dapat membagi tugas ke **thread** secara terpisah, sehingga membuah game lebih responsif dan lancar.

---

## 4.2 Using Amdahl’s Law, calculate the speedup gain of an application that has a 60 percent parallel component for (a) two processing cores and (b) four processing cores.

    Diketahui : 
    
    - Komponen paralel (P) = 60% = 0.6
    - Komponen serial (1-P) = 40% = 0.4

    Ditanya :
    Berapa peningkatan kecepatan (speedup) dari aplikasi tersebut?
    
    Rumus :
    Speedup = 1 / [(1 - P) + (P/N)]
    
    
    Jawab :
    
    a) Dua Core (N=2) :
    Speedup = 1 / [0.4 + (0.6/2)]
    = 1 / (0.4 + 0.3)
    = 1 / 0.7
    ≈ 1.43x
    
    
    b) Empat Core (N=4) :
    Speedup = 1 / [0.4 + (0.6/4)]
    = 1 / (0.4 + 0.15)
    = 1 / 0.55
    ≈ 1.82x


---

## 4.3 Does the multithreaded web server described in Section 4.1 exhibit task or data parallelism?

    Web server multithread pada Section 4.1 menunjukkan task paralellism
    itu karena setiap thread menjalankan tugas yang berbeda secara bersamaan. Pada web server multithreaded, setiap thread menangani permintaan klien yang berbeda (misalnya, permintaan HTTP untuk file berbeda atau dari klien berbeda). 
    Meskipun semua thread menjalankan kode server yang mirip, data yang mereka proses (permintaan dari klien) berbeda-beda. Ini adalah ciri khas dari task parallelism, bukan data parallelism (di mana data besar dibagi menjadi bagian-bagian kecil dan diproses secara paralel oleh beberapa thread)

---

## 4.4 What are two differences between user-level threads and kernel-level threads? Under what circumstances is one type better than the other?

    Perbedaan:
    - Manajemen
    User-level: Dikelola library (contoh: pthreads) tanpa campur tangan OS
    Kernel-level: Dikelola langsung oleh OS
    
    - Kinerja
    User-level: Context switch lebih cepat (tidak butuh syscall)
    Kernel-level: Blocking syscall tidak menghentikan seluruh proses
    
    - Keunggulan
    User-level cocok untuk aplikasi dengan banyak thread ringan (contoh: JVM)
    Kernel-level lebih baik untuk tugas blocking (contoh: I/O intensif)

    - Kapan lebih baik?

    User-level thread lebih baik digunakan saat aplikasi membutuhkan performa tinggi dan tidak membutuhkan pemrosesan paralel di banyak core CPU
    Kernel-level thread lebih baik digunakan saat kita butuh benar-benar menjalankan thread secara paralel di beberapa core atau memanfaatkan fitur sistem operasi seperti preemption

---

## 4.5 Describe the actions taken by a kernel to context-switch between kernel-level threads.

    tindakan-tindakan yang dilakukan kernel untuk melakukan context-switch antar thread kernel-level antara lain
    
    - Menyimpan Status Thread Saat Ini
        Kernel menyimpan semua register CPU, program counter, stack pointer, dan informasi penting lainnya dari thread yang sedang berjalan ke Thread Control Block (TCB)
    
    - Memilih Thread Baru
        Kernel menggunakan scheduler untuk memilih thread lain yang siap dijalankan berdasarkan algoritma penjadwalan (seperti *round-robin* atau *priority-based*)
    
    - Memuat Status Thread Baru
        Kernel memuat kembali semua register CPU, program counter, stack pointer, dan informasi lainnya dari TCB thread baru.
    
    - Melanjutkan Eksekusi Thread Baru
        CPU mulai menjalankan instruksi thread baru dari titik terakhir eksekusi
    

---

## 4.6 What resources are used when a thread is created? How do they differ from those used when a process is created?

    Saat thread dibuat, ia berbagi sumber daya proses induknya seperti memori, file descriptor, dan ruang alamat. Yang dibuat hanya stack, program counter, dan register sendiri

    Saat proses dibuat, semua sumber daya baru dialokasikan termasuk ruang alamat memori, file descriptor sendiri, tabel proses, dan sebagainya    

---

## 4.7 Assume that an operating system maps user-level threads to the kernel using the many-to-many model and that the mapping is done through LWPs. Furthermore, the system allows developers to create real-time threads for use in real-time systems. Is it necessary to bind a real-time thread to an LWP? Explain.

      Ya, perlu mengikat thread real-time ke LWP.
    Alasannya, pada model many-to-many, tidak semua thread pengguna secara langsung dipetakan ke thread kernel. Jika sebuah thread real-time tidak diikat ke LWP, maka ia tidak dijamin akan langsung dijadwalkan oleh kernel.
    
    Mengikat thread real-time ke LWP memastikan thread tersebut memiliki jalur langsung ke prosesor melalui kernel, sehingga sistem dapat menjadwalkannya sesuai prioritas real-time tanpa penundaan. 
    Ini penting karena thread real-time membutuhkan waktu respon yang cepat dan terprediksi.

---
