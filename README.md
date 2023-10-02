# Aplikasi Web TimeTagger
<h1 align="center"><img src="https://timetagger.app/timetagger_wl.svg"></h1>

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
- RAM minimal 64 Mb+

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

- -

## Otomatisasi (opsional)
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

- -


## Cara Pemakaian
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

Cara pemakaian **TimeTagger** ini cukup mudah, karena aplikasi ini telah menyediakan *interface* yang mudah dimengerti. Berikut adalah langkah-langkah penggunaannya :
1. Sebelum menggunakan TimeTagger, kita bisa login ke akun user yang sudah diset pada `docker-compose.yml` atau dengan menggunakan default user untuk localhost.

    ![login](../main/Screenshots/Login.png)

2. Setelah login, kita akan masuk ke halaman utama. Disini kita dapat memasang tag pada alur waktu untuk penjadwalan.

    ![mainpage](../main/Screenshots/Halaman Utama.png)

3. Kita bisa menambahkan *Record* baru dengan menekan tombol Record dan Start Record 

    ![startrecord](../main/Screenshots/Start Record.png)
- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
- Bandingkan dengan aplikasi web lain yang sejenis


## Referensi
[`^ kembali ke atas ^`](#aplikasi-web-timetagger)

Cantumkan tiap sumber informasi yang anda pakai.
