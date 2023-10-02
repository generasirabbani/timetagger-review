# Aplikasi Web TimeTagger
<h1 align="center"><img src="https://timetagger.app/timetagger_wl.svg"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:
## Sekilas Tentang
[`^ kembali ke atas ^`](#)

**TimeTagger** adalah sebuah aplikasi Time Tracking berbasis web dengan UX yang interaktif, gratis dan *Open Source*. Aplikasi ini dibuat oleh Almar Klein dari Belanda. **TimeTagger** dibuat dengan Python yang di-*compile* menjadi JavaScript menggunakan [PScript](https://github.com/flexxui/pscript). Server Backend aplikasi ini menggunakan [Upcloud](https://upcloud.com/) yang masih aktif hingga hari ini, sehingga masih berfungsi dengan baik sebagai aplikasi Time Tracking multi-user.


## Instalasi
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

#### Prasyarat :
- Windows, Unix, atau Linux
- Python 3.6+
- Git 2.34+
- Docker 24.0+
- Docker Compose 2.17+

#### Langkah Instalasi :
1. Pastikan seluruh paket sistem dalam versi terbaru, dan install seluruh kebutuhan sistem seperti modul `python3-pip`, `docker`, dan `docker-compose`.
    ```
    $ sudo apt-get update
    $ sudo apt-get install python3-pip
    $ sudo apt-get install git-all
    $ sudo apt-get remove docker docker-engine docker.io
    $ sudo apt install docker.io
    $ sudo snap install docker
    ```

2. Pull repository ke docker.
    ```
    $ docker pull ghcr.io/almarklein/timetagger:v23.9.2
    ```

3. Install library timetagger dengan module pip python.
    ```
    $ python3 -m pip install -U timetagger
    ```

4. Clone repository ke dalam direktori yang diinginkan.
    ```
    $ git clone https://github.com/almarklein/timetagger.git
    ```

5. Pindah direktori ke dalam timetagger/deploy
    ```
    $ cd timetagger/deploy
    ```

6. Deploy menggunakan docker-compose
    ```
    $ docker-compose up
    ```

7. Server localhost sudah berjalan dan bisa dilihat di `localhost/timetagger`

## Konfigurasi
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

- Kita bisa menambahkan akun user dengan mengubah konfigurasi di file `docker-compose.yml` di `timetagger/deploy` bagian TIMETAGGER_CREDENTIALS
    ```
    version: "3"
    services:
      timetagger:
        image: ghcr.io/almarklein/timetagger
        ports:
          - "80:80"
        volumes:
          - ./_timetagger:/root/_timetagger
        environment:
          - TIMETAGGER_BIND=0.0.0.0:80
          - TIMETAGGER_DATADIR=/root/_timetagger
          - TIMETAGGER_LOG_LEVEL=info
          - TIMETAGGER_CREDENTIALS=test:$$2a$$08$$zMsjPEGdXHzsu0N/felcbuWrffsH4.4ocDWY5oijsZ0cbwSiLNA8.  # test:test
    ```
- Bisa juga kita jalankan langsung di CLI menggunakan arguments
    ```
    $ python3 -m timetagger --credentials=test:$2a$08$0CD1NFiIbancwWsu3se1v.RNR/b7YeZd71yg3cZ/3whGlyU6Iny5i
    ```
- Kita perlu membuat string dengan BCrypt hash untuk username dan password yang akan menggantikan username test. **TimeTagger** menyediakan layanan hash BCrypt di website https://timetagger.app/cred. 

##  Maintenance (opsional)
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

## Otomatisasi (opsional)
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

## Cara Pemakaian
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

Cara pemakaian **TimeTagger** ini cukup mudah, karena aplikasi ini telah menyediakan *interface* yang mudah dimengerti. Berikut adalah langkah-langkah penggunaannya :
1. Sebelum menggunakan TimeTagger, kita bisa login ke akun user yang sudah diset pada `docker-compose.yml` atau dengan menggunakan default user untuk localhost.

    ![login](../main/Screenshots/Login.png)

2. Setelah login, kita akan masuk ke halaman utama. Disini kita dapat memasang tag pada alur waktu untuk penjadwalan.

    ![mainpage](../main/Screenshots/HalamanUtama.png)

3. Kita bisa menambahkan record berbentuk timer dengan menekan tombol Record dan Start Record. Bisa ditambahkan deskripsi kegiatan apa yang akan dimasukkan, pasang tag, dan waktu. Setelah selesai diset, maka klik tombol Start.

    ![startrecord](../main/Screenshots/StartRecord.png)

4. Pada bagian *Timeline* di kiri, kita bisa klik kemudian klik dan drag selama waktu yang diinginkan. Setelah itu akan muncul New Record untuk menandakan sesuatu yang sudah selesai dilaksanakan. Kita bisa menambahkan deskripsi kegiatan, tag, dan waktu. Setelah selesai, klik tombol Create.

    ![newrecord](../main/Screenshots/NewRecord.png)

5. Setelah menambahkan record, kita bisa mengedit record yang sudah ada dengan mengklik record tersebut dan muncul Edit Record. Kemudian bisa diubah deskripsi, tag dan waktunya. Setelah selesai, klik tombol Save.

    ![editrecord](../main/Screenshots/EditRecord.png)

6. Untuk mengekspor laporan, bisa klik tombol Report. Pilih jarak tanggal untuk diekspor menjadi file laporan. Bisa juga diset tag, grouping, tag order, format dan details. Setelah selesai, pilih file output yang diinginkan antara copy table, csv atau pdf.

    ![report](../main/Screenshots/Report.png)

## Pembahasan
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

**TimeTagger** ditulis dalam bahasa pemrograman `Python` yang dibuat oleh seorang dari Belanda, Almar Klein. Beliau membuat TimeTagger menggunakan *project open source* miliknya yang lain yaitu [Asgineer](https://github.com/almarklein/asgineer), [MyPaas](https://github.com/almarklein/mypaas), [ItemDB](https://github.com/almarklein/itemdb) dan [fastuaparser](https://github.com/almarklein/fastuaparser). Aplikasi ini memiliki beberapa fitur, diantaranya :
- Tracker intuitif untuk individu
- Bisa dibawa kemana saja
- Laporan dalam format pdf dan csv
- Privasi dipentingkan

Kelebihan aplikasi ini dibandingkan berbagai aplikasi yang sejenis adalah :
- Menggunakan HTML5 canvas API sebagai frontend, tidak menggunakan library JS sehingga semua interaksi cukup cepat untuk dikatakan real-time.
- Database sudha diset otomatis di server utama sehingga tidak butuh melakukan pemasangan database secara manual. 

Kekurangan dari aplikasi ini dibandingkan berbagai aplikasi yang sejenis adalah :
- Aplikasi ini tidak mendukung tracking waktu untuk tim dan bisnis.
- Manajemen waktu yang kurang canggih
- Tidak adanya analisis mendalam.

Jika dibandingkan dengan **Toggl**, **TimeTagger** memiliki beberapa perbedaan yang patut diperhatikan. 
- **TimeTagger** lebih fokus pada pelacakan waktu untuk tugas atau proyek tertentu, sementara **Toggl** adalah alat yang lebih kuat dan serbaguna yang cocok untuk manajemen waktu dan proyek yang lebih kompleks. 
- **TimeTagger** cenderung memiliki antarmuka yang lebih sederhana dan minimalis, yang dapat menjadi pilihan yang baik jika Anda mencari alat yang mudah digunakan tanpa banyak fitur tambahan, sedangkan **Toggl** memiliki fitur riwayat dan laporan yang mendalam, memungkinkan Anda menganalisis bagaimana waktu Anda dihabiskan dan menghasilkan laporan yang lebih terperinci.
- **Toggl** memiliki dukungan untuk berbagai platform, termasuk desktop, web, dan perangkat seluler, sementara **TimeTagger** mungkin lebih cocok untuk penggunaan pribadi atau kecil daripada penggunaan bisnis yang besar.

## Referensi
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

1. [About TimeTagger](https://timetagger.app/) - TimeTagger
2. [How to Install Docker on Ubuntu: A Step-By-Step Guide](https://www.simplilearn.com/tutorials/docker-tutorial/how-to-install-docker-on-ubuntu) - simplilearn
3. [How to host your own modified time tracker](https://timetagger.app/articles/selfhost/) - TimeTagger Articles
4. [How to self-host your time tracker with Docker](https://timetagger.app/articles/selfhost2/) - TimeTagger Articles
5. [TimeTagger Github Repository](https://github.com/almarklein/timetagger) - GitHub
6. [TimeTagger - Reviews, Pros & Cons](https://stackshare.io/timetagger) - stackshare