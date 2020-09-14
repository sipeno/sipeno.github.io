---
id: git
title: Git
sidebar_label: Pengenalan Git
---

## Apa itu Git?

Git adalah Version Control System (VCS) terdistribusi yang diciptakan oleh Linus
Torvalds. Digunakan sebagai perkakas bantu untuk bekerja antar para programmer.
Git digunakan untuk melacak perubahan pada berkas-berkas code. Pada praktikum
ini digunakan GitHub yang merupakan salah satu penyedia layanan Git di cloud.
Untuk memeriksa apakah Git sudah terinstall silahkan jalankan perintah berikut
pada terminal anda.

```
git --version
```

Jika luaran yang didapatkan menunjukkan versi git yang terinstall, maka anda
telah mempunyai program git.

## Instalasi

Cara instalasi git berbeda-beda tergantung dari sistem operasi yang digunakan.
Pada bagian ini akan dijabarkan langkah-langkah untuk instalasinya.

### Instalasi Git pada Windows
Berikut ini langkah langkah installasi git pada sistem operasi windows 10.

- Double click installer dan ikuti langkah langkahnya

- Halaman lisensi git, perhatikan lisensi nya dengan seksama apabila anda tidak
cocok dengan lisensi yang di berikan jangan melanjutkan installasi :)

  ![install](/img/01-install-git.png)

- Pilihlah lokasi install yang sesuai menurut kebutuhan anda :

  ![install](/img/02-install-git.png)

- Pilihlah komponen komponen Git yang anda butuhkan, jika tidak mengerti biarkan
sesuai dengan opsi default

  ![install](/img/03-install-git.png)

- Pilihlah apakah akan menambahkan git ke start menu :

  ![install](/img/04-install-git.png)

- Pilihlah default editor untuk perintah git. Vim adalah default editor pada git,
silahkan pilih editor lain jika anda tidak familiar dengan Vim.

  ![install](/img/05-install-git.png)

- Setting path environment pilihlah pilihan kedua untuk dapat menjalankan git baik
dari terminal bawaan windows dan git bash

  ![install](/img/06-install-git.png)

- Untuk https transport backend pilihlah OpenSSL

  ![install](/img/07-install-git.png)

- Untuk pilihan selanjutnya gunakan opsi default jika anda tidak mengerti pilihan yang diberikan

  ![install](/img/08-install-git.png)

  ![install](/img/09-install-git.png)

  ![install](/img/10-install-git.png)

  ![install](/img/11-install-git.png)

  ![install](/img/12-install-git.png)

  ![install](/img/13-install-git.png)

- Setelah proses install selesai bukalah command prompt anda dan ketikkan perintah
`git` jika git berhasil dijalankan akan tampil oputput seperti pada gambar
dibawah ini

  ![install](images/installgit/14-install-git.png)

### Instalasi Git pada Linux

Untuk instalasi pada sistem opersi Linux silahkan sesuaikan dengan package
manager pada distribusi yang anda gunakan. Silahkan lakukan perintah berikut
dengan akses root.

- Ubuntu/Debian dan turunannya

    ```
    apt install git
    ```

- Fedora/CentOS dan turunannya

    ```
    yum install git
    ```

### Instalasi Git pada Mac

Anda dapat menginstall Git pada Mac dengan cara menginstall program `Xcode
Command Line Tools`. Tetapi jika anda ingin mendapatkan versi git yang lebih
baru, anda dapat menggunakan instalasi melalui HomeBrew. Silahkan baca
dokumentasinya di brew.sh kemudian anda dapat menginstall git dengan perintah
berikut.

```
brew install git
```

