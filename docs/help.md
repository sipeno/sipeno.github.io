---
id: help
title: Panduan untuk Pengajar
sidebar_label: Panduan untuk Pengajar
---

Pada bagian ini akan dibahas mengenai panduan untuk penggunaan sistem dari sudut
pandang pengajar. Sebelum melanjutkan diharapkan pengajar telah memiliki
kemampuan dasar berikut untuk memudahkan penggunaan sistem Sipeno.

1. Dapat mengoperasikan aplikasi terminal pada sistem operasi, baik itu terminal
   pada unix atau cmd di Windows.
2. Perangkat lunak versioning git telah terpasang pada piranti masing-masing.
3. Memahami konsep dan perintah dasar git (init, add, commit, push dan pull).
4. Memiliki akun GitHub.
5. Memiliki akun organisasi GitHub untuk digunakan dalam GitHub Classroom.
6. Memahami konsep unit testing atau instrument testing.

## Pengaturan Awal

Untuk menggunakan sistem penilaian otomatis, silahkan lakukan registrasi akun
GitHub terlebih dahulu pada tautan [Join GitHub](https://github.com/join) (jika
belum mempunyai akun GitHub). Ikuti langkah-langkah isian yang diperlukan,
kemudian pastikan anda telah masuk ke dalam dashboard GitHub. Jika anda telah
memiliki akun GitHub maka anda dapat melewati tahapan ini dan dilanjutkan ke
tahapan untuk membuat akun organisasi.

Pada dashboard GitHub, perhatikan menu di bagian pojok kanan dengan icon `+`.
Klik menu tersebut kemudian sorot menut `New organization`.

![Menu Github](/img/menu-github.png)

Langkah berikutnya silahkan pilih plan yang diinginkan. Jika kebutuhan anda
dalam skala kecil, silahkan pilih plan yang gratis dengan menekan tombol **Join
for free** pada plan yang paling kiri.

![GitHub Plan](/img/github-plan.png)

lengkapi form isian sesuai dengan kebutuhan. Silahkan pilih nama organisasi yang
unique, dan lengkapi juga dengan email anda. Jika organisasi ini untuk kebutuhan
pribadi silahkan pilih **My Personal account** jika tidak silahkan pilihan
lainnya. Lengkapi form isian yang masih dibutuhkan. Pada gambar berikut adalah
contoh pengisian form untuk organisasi baru.

![New Organization](/img/new-organization.png)

## Pengaturan GitHub Classroom

GitHub Classroom merupakan learning management system yang berbasiskan Git.
Dengan GitHub Classroom anda dapat mengelola tugas-tugas dalam repository git.
Silahkan buka tautan https://classroom.github.com dan lakukan login dengan akun
GitHub anda.

![Github Classroom](/img/github-classroom.png)

Tekan tombol **New classroom** atau anda dapat mengakses tautan
https://classroom.github.com/classrooms/new untuk membuat classroom baru. Pada
halaman perambah anda akan ditampilkan daftar organisasi yang telah terhubung
dengan GitHub Classroom. Jika nama organisasi anda tidak tampil, silahkan akses
tautan [grant us access]. Pilih nama organisasi yang diinginkan. Ikuti langkah
wizard yang dibutuhkan.

Untuk membuat classroom baru dibutuhkan nama, silahkan beri nama sesuai dengan
kebutuhan.

Sebagai langkah selanjutnya, jika dalam mengajar terdapat team teaching anda
dapat mengundang pengajar pada form berikutnya.

Selain itu GitHub classroom terdapat juga integrasi dengan platform LMS lainnya,
seperti Google classroom, moodle, canvas dan lainnya.

Setelah muncul tampilan seperti gambar di bawah, maka anda sudah siap untuk
memberikan penugasan dengan menggunakan GitHub classroom.

## Penugasan dengan GitHub Classroom

Untuk membuat penugasan dengan GitHub Classroom silahkan tekan tombol *Create an
assignment**. Kemudian lengkapi isian pada form yang tampil. Sebuah tugas
membutuhkan nama, deadline (bersifat opsional), jenis tugas individu atau
berkelompok, sifat repository private atau public, serta status hak akses
terkait pengaturan admin pada repository. Lengkapi isian seperti pada gambar
berikut. Kemudian tekan tombol **Continue** untuk lanjut ke langkah berikutnya.

![Assignments Basic](/img/assignments-basic.png)

Pada tahapan berikutnya terdapat pengaturan terkait starter code dan IDE online.
Lengkapi starter code yang berupa repository project template. Dalam starter
code terdapat unit test serta workflow untuk proses penilaian. Jika anda belum
mempunyai starter code, silahkan gunakan `sipeno/skorbola-starter` sebagai
isian. Kemudian tekan tombol **Continue** untuk lanjut ke langkah berikutnya.

![Starter Code](/img/starter-code.png)

Pada langkah berikutnya berkaitan dengan grading. Karena dalam penilaian ini
digunakan custom grading, silahkan lewati langkah ini. Saat ini GitHub Classroom
sudah mendukung untuk penilaian project sederhana seperti Java, NodeJS dan
lain-lain.

Penugasan GitHub Classroom berupa undangan URL yang dapat dibagikan. Silahkan
salin undangan dengan menekan tombol **Copy invitation link**, kemudian bagikan
kepada mahasiswa anda.

![URL Invitation](/img/invitation-url.png)

Undangan URL ketika dibuka akan menampilkan sebuah form konfirmasi untuk
menerima penugasan yang diberikan. Silahkan tekan tombol **Accept this
assignment** untuk melanjutkan. GitHub Classroom secara otomatis akan membuatkan
repository baru dengan format `<organisasi>/<tugas>-<username>` dan juga
menyiapkan code yang disalin dari starter code. Sebagai langkah akhir, silahkan
clone repository yang telah disiapkan.

![Accept this assignment](/img/accept-this-assignment.png)

## Menyiapkan Starter Code

Pada langkah penugasan GitHub Classroom telah disinggung terkait starter code.
Starter Code dibutuhkan untuk menyiapkan tugas yang akan diselesaikan dan juga
sebagai dasar penilaian. Dalam starter code setidaknya terdiri dari tiga
bagian, yaitu:

- GitHub Workflow
- Instrument Test
- Code

### Menyiapkan GitHub Workflow

GitHub Workflow merupakan CI/CD yang dikembangkan oleh GitHub. Format
penulisannya menggunakan yaml. Dalam workflow didefinisikan proses-proses yang
akan dilakukan jika terdapat kondisi yang dipenuhi ketika terjadi git event.
Sebagai contoh pada workflow di bawah akan dieksekusi jika ada event `push` pada
branch `master`.

```yml
name: Run Sipeno Checks

on:
  push:
    branches:
      - master

jobs:
  test:
    name: Run Espresso Tests
    runs-on: macOS-latest

    steps:
      - uses: actions/checkout@v2
      - name: Setup JDK 1.8
        uses: actions/setup-java@v1
        with:
          java-version: 1.8

      - name: Run unit tests
        uses: reactivecircus/android-emulator-runner@v2
        with:
          api-level: 29
          script: ./gradlew connectedCheck
```

### Menyiapkan Instrument Test

Untuk menentukan apakah project yang dikerjakan sudah sesuai, dibutuhkan
instrument test. Pada sistem ini digunakan library `espresso`. Pada contoh di
bawah terdapat definisi test yang akan mencocokan hasil output apakah bernilai
`1` jika tombol tambah ditekan. Secara singkat bagian ini dapat dianalogikan
sebagai kunci jawaban.

```java
public class MainActivityTest {

	@Rule
	public ActivityScenarioRule<MainActivity> mActivityScenarioRule =
    new ActivityScenarioRule<MainActivity>(MainActivity.class);

	@Test
	public void increaseScoreHomeTest() {
		onView(withId(R.id.btn_increase_home))
			.perform(click());
		onView(withId(R.id.txt_home_score))
			.check(matches(withText("1")));
	}

}
```

### Menyiapkan Code

Ada kalanya akan mahasiswa akan mengalami kesulitan jika project yang dikerjakan
harus dibangun dari awal. Sehingga untuk mengatasi masalah ini, dapat disiapkan
code dasar. Mahasiswa cukup melanjutkan hal teknis apa yang belum
diimplementasikan.

## Repository GitHub

Starter code yang telah disiapkan selanjutnya harus diletakkan ke dalam
repository GitHub. Untuk melakukan ini silahkan gunakan konsep dan perintah pada
Git.
