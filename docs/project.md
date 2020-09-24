---
id: project
title: Project Skor Bola
sidebar_label: Project Skor Bola
---

# Skor Bola

## Alat dan Bahan

1. Laptop atau PC
2. Android Studio
3. Akun [GitHub](https://github.com)
4. Starter Code [Skor Bola Starter](https://classroom.github.com/a/KJX8Gmyu)
   pada GitHub Classroom.

## Praktikum

- Pastikan anda telah menerima tugas (Accept the assignment) tautan pada GitHub
   Classroom. Tunggu sampai dengan proses import selesai.

- Bukalah layout `activity_main.xml`, dan pelajari desain layout yang telah
 disediakan. Dalam desain terdapat tampilan untuk tim Home dan tim Away. Untuk
 masing-masing tim terdapat tombol untuk menambah skor dan mengurangi skor jika
 terjadi kesalahan input. Dan juga terdapat sebuah tombol untuk me-*reset* skor
 ke semula.

 - Pada bagian layout, perhatikan id untuk masing-masing view/widget yang dapat
  dipaparkan pada tabel di bawah. Pada tabel tersebut mengandung informasi dari
  layout yang diperlukan untuk dihubungkan dalam `Activity`.

  | id                | Type     |
  | ---               | ---      |
  | txt_home_score    | TextView |
  | txt_away_score    | TextView |

- Bukalah file `MainActivity.java`, pelajari struktur dasar terkait `Activity`.
 Kemudian dari tabel yang telah dijabarkan dalam layout, dapat dijabarkan
 menjadi atribut-atribut sebagai berikut.

 | Variable           | Type     |
 | ---                | ---      |
 | homeScoreText      | TextView |
 | awayScoreText      | TextView |

```java
public class MainActivity extends AppCompatActivity {

  private TextView homeScoreText;
  private TextView awayScoreText;


	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
	}

}
```

- Lakukan proses binding dengan menggunakan method `findViewById` sehingga hasil
 kode akhir menjadi seperti berikut.

```java
public class MainActivity extends AppCompatActivity {

  private TextView homeScoreText;
  private TextView awayScoreText;


	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
    // proses binding
    homeScoreText = findViewById(R.id.txt_home_score);
    awayScoreText = findViewById(R.id.txt_away_score);
	}

}
```

- Pada aplikasi skor bola dibutuhkan pemodelan data untuk menampilkan nilai skor
 baik untuk tim Home maupun tim Away. Nilai skor berjenis angka, sehingga
 dibutuhkan tipe data integer. Tambahkan atribut pada file `MainActivity.java`
 sehingga kode akhir menjadi seperti berikut.

```java
public class MainActivity extends AppCompatActivity {

  private TextView homeScoreText;
  private TextView awayScoreText;

  private int homeScore;
  private int awayScore;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
    // proses binding
    homeScoreText = findViewById(R.id.txt_home_score);
    awayScoreText = findViewById(R.id.txt_away_score);
    homeScore = 0;
    awayScore = 0;
	}

}
```

- Buka kembali layout `activity_main.xml`, dan ubah mode tampilan menjadi code.
 Pada langkah ini akan ditambahkan interaksi click melalui property
 `android:onClick`. Modifikasi code sehingga tampilan akhir menjadi seperti
 berikut.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
	xmlns:app="http://schemas.android.com/apk/res-auto"
	xmlns:tools="http://schemas.android.com/tools"
	android:layout_width="match_parent"
	android:layout_height="match_parent"
	tools:context=".MainActivity">

	<TextView
		android:id="@+id/label_home"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:text="Home"
		android:textSize="36sp"
		android:textStyle="bold"
		app:layout_constraintBottom_toTopOf="@+id/txt_home_score"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toTopOf="parent" />

	<TextView
		android:id="@+id/label_away"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:text="Away"
		android:textSize="36sp"
		android:textStyle="bold"
		app:layout_constraintBottom_toBottomOf="parent"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toBottomOf="@+id/txt_away_score" />

	<TextView
		android:id="@+id/txt_home_score"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:layout_marginBottom="20dp"
		android:text="0"
		android:textSize="72sp"
		app:layout_constraintBottom_toTopOf="@+id/btn_reset"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toTopOf="parent" />

	<TextView
		android:id="@+id/txt_away_score"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:text="0"
		android:textSize="72sp"
		app:layout_constraintBottom_toBottomOf="parent"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toBottomOf="@+id/btn_reset" />

	<Button
		android:id="@+id/btn_reset"
		android:layout_width="0dp"
		android:layout_height="wrap_content"
		android:layout_marginStart="24dp"
		android:layout_marginEnd="24dp"
		android:onClick="handleReset"
		android:text="Reset"
		app:layout_constraintBottom_toBottomOf="parent"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toTopOf="parent" />

	<Button
		android:id="@+id/btn_increase_home"
		android:layout_width="0dp"
		android:layout_height="wrap_content"
		android:layout_marginStart="24dp"
		android:layout_marginEnd="24dp"
		android:onClick="handleIncreaseHomeScore"
		android:text="+1"
		android:textStyle="bold"
		app:layout_constraintBottom_toTopOf="@+id/btn_reset"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toEndOf="@+id/txt_home_score"
		app:layout_constraintTop_toTopOf="parent" />

	<Button
		android:id="@+id/btn_decrease_home"
		android:layout_width="0dp"
		android:layout_height="wrap_content"
		android:layout_marginStart="24dp"
		android:layout_marginEnd="24dp"
		android:onClick="handleDecreaseHomeScore"
		android:text="-1"
		android:textStyle="bold"
		app:layout_constraintBottom_toTopOf="@+id/btn_reset"
		app:layout_constraintEnd_toStartOf="@+id/txt_home_score"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toTopOf="parent" />

	<Button
		android:id="@+id/btn_increase_away"
		android:layout_width="0dp"
		android:layout_height="wrap_content"
		android:layout_marginStart="24dp"
		android:layout_marginEnd="24dp"
		android:onClick="handleIncreaseAwayScore"
		android:text="+1"
		android:textStyle="bold"
		app:layout_constraintBottom_toBottomOf="parent"
		app:layout_constraintEnd_toEndOf="parent"
		app:layout_constraintStart_toEndOf="@+id/txt_away_score"
		app:layout_constraintTop_toBottomOf="@+id/btn_reset" />

	<Button
		android:id="@+id/btn_decrease_away"
		android:layout_width="0dp"
		android:layout_height="wrap_content"
		android:layout_marginStart="24dp"
		android:layout_marginEnd="24dp"
		android:onClick="handleDecreaseAwayScore"
		android:text="-1"
		android:textStyle="bold"
		app:layout_constraintBottom_toBottomOf="parent"
		app:layout_constraintEnd_toStartOf="@+id/txt_away_score"
		app:layout_constraintStart_toStartOf="parent"
		app:layout_constraintTop_toBottomOf="@+id/btn_reset" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

- Pada aplikasi Android Studio dalam layout `activity_main.xml` akan muncul
 garis warna merah, untuk masing-masing tombol silahkan tekan tombol shortcut
 `Alt+Enter`. Android Studio akan meng-*generate* method dalam
 `MainActivity.java` yang telah terhubung dengan layout.

- Jika langkah-langkah anda benar, maka hasil akhir dalam file
 `MainActivity.java` akan menjadi seperti berikut.

 > Urutan lokasi method-method tidak harus sama, selama tidak ada kesalahan dalam
 > penulisan sintaks kode tidak menjadi masalah.

```java
public class MainActivity extends AppCompatActivity {

	private TextView homeScoreText;
	private TextView awayScoreText;

	private int homeScore;
	private int awayScore;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		homeScoreText = findViewById(R.id.txt_home_score);
		awayScoreText = findViewById(R.id.txt_away_score);
		homeScore = 0;
		awayScore = 0;
	}

	public void handleDecreaseHomeScore(View view) {
	}

	public void handleIncreaseHomeScore(View view) {
	}

	public void handleDecreaseAwayScore(View view) {
	}

	public void handleIncreaseAwayScore(View view) {
	}

	public void handleReset(View view) {
	}
}
```
- Ketika tombol `-1` pada tim Home ditekan maka skor yang akan ditampilkan
 berkurang satu dari nilai semula. Kemudian nilai skor yang baru ditampilkan
 pada tampilan TextView. Proses ini dilakukan jika nilai skor sebelumnya bukan
 `0`. Dari logika tersebut, dapat diubah menjadi kode java berikut.

```java
public void handleDecreaseHomeScore(View view) {
		if (homeScore > 0) {
			homeScore--;
			homeScoreText.setText(String.valueOf(homeScore));
		}
}
```

- Ketika tombol `+1` pada tim Home ditekan maka skor yang akan ditampilkan
bertambah satu dari nilai semula. Kemudian nilai skor yang baru ditampilkan
pada tampilan TextView. Dari logika tersebut, dapat diubah menjadi kode java
berikut.

```java
public void handleIncreaseHomeScore(View view) {
		homeScore++;
		homeScoreText.setText(String.valueOf(homeScore));
}
```

## Challenge

- Selesaikan logika untuk implementasi nilai skor pada tim Away dan implementasi
 fungsi reset skor.

> Jangan lupa melakukan commit dan push ke repository GitHub yang telah disiapkan.
> Jika anda mendapatkan tanda hijau pada proses build, berarti anda telah berhasil
> menyelesaikan semua fungsional project ini.
