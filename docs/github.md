---
id: github
title: GitHub
sidebar_label: GitHub
---

# GitHub

## Akun GitHub

Dalam modul ajar ini menggunakan GitHub sehingga dibutuhkan akun GitHub sebagai
kebutuhan. Untuk melakukan registrasi silahkan klik tautan [Join
GitHub](https://github.com/join) berikut. Kemudian lengkapi formulir isian yang
dibutuhkan.

## Integrasi GitHub dengan Android Studio

Untuk memudahkan penggunaan Git, digunakan Android Studio sebagai Git Client.
Terdapat beberapa langkah untuk menyiapkannya. Silahkan ikuti langkah-langkah
berikut:

- Buka aplikasi terminal (cmd) pada sistem operasi anda
- Untuk memeriksa apakah sudah terdapat setting akun Git, jalankan perintah `git
 config --global --get user.email`. Jika hasil perintah kosong, maka anda perlu
 mengkonfigurasi akun Git terlebih dahulu.
- Jalankan perintah di bawah ini untuk mengatur informasi akun Git berupa email
 (email akun GitHub) dan nama anda.

  ```
  git config --global  user.email "<youremail>@email.com"
  git config --global  user.name "<your name>"
  ```

- Buka aplikasi **Android Studio**, kemudian masuk ke **Settings**.
- Filter settings dengan keyword `github`, dan pilih menu `GitHub` pada bagian
 **Version Control**.

 ![Preferences GitHub](/img/preferences-github.png)

- Tambahkan akun baru dengan menekan **Add Account**, dan lengkapi informasi
 login dengan akun GitHub anda.

 ![Login to GitHub](/img/login-to-github.png)

- Jika proses login berhasil maka akan muncul akun profil GitHub anda.

  ![Akun GitHub](/img/github-account.png)

- Proses setup akun GitHub telah selesai.
