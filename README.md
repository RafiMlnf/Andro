# ULANGAN AKHIR SEMESTER - PEMROGRAMAN MOBILE 1

```
Mata Kuliah : Pemrograman Mobile 1
Dosen       : Donny Maulana, S.Kom., M.M.S.I.
Nama        : Rizjky Dito Ridwansyah
NIM         : 312210405
```

Mata Kuliah Pemrograman mobile menggunakan aplikasi Android Studio.

## 1. Hello
Activity pertama yang dibuat adalah teks greeting, contoh Hello!

```Java
<TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Halo Selamat Datang Di Aplikasi Saya.Perkenalkan Nama Saya Rizjky Dito Ridwansyah"
        android:textColor="#FF0000"
        android:textAlignment="center"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
```

###  Capture hasil:
![image](https://github.com/RafiMlnf/Andro/assets/115614668/9e90bc8a-5ce5-40fa-9e53-72e086468a71)


## 2. Toast

```Java
    public void showToast(View view) {
        Toast toast = Toast.makeText(this, R.string.toast_message, Toast.LENGTH_SHORT);
        toast.show();
    }
```

Kode diatas adalah metode suatu kelas di Android yang bertujuan untuk menampilkan pesan toast. Penjelasannya:

- Metode showToast(View view): metode yang akan dipanggil saat suatu tindakan terjadi, seperti menekan tombol yang terhubung dengan metode ini.
- Toast toast = Toast.makeText(this, R.string.toast_message, Toast.LENGTH_SHORT);:
- Toast: Objek dari kelas Toast yang digunakan untuk menampilkan pesan sementara.
makeText(): Metode statis dari kelas Toast untuk membuat instans Toast baru.
- this: Merujuk pada konteks saat ini, yaitu aktivitas atau objek konteks tempat metode ini dipanggil.
- R.string.toast_message: Menggunakan string dari sumber daya string (biasanya didefinisikan di file res/values/strings.xml). Ini memungkinkan untuk lebih mudah mengelola pesan yang ditampilkan.
- Toast.LENGTH_SHORT: Menunjukkan durasi tampilan pesan toast, dalam hal ini, pesan akan ditampilkan dalam waktu singkat.
- toast.show();: Memanggil metode show() untuk menampilkan pesan toast yang telah disiapkan sebelumnya.

Jadi Toast itu tujuannya uuntuk menampilkan pesan singkat kepada pengguna (sesuai dengan nilai yang didefinisikan dalam R.string.toast_message) melalui elemen UI, seperti tombol, yang terhubung dengan metode showToast.

### Capture hasil:

## 3. Scrolling (Ice Cold)
Menampilkan teks berita yang dapat di scroll. Menggunakan metode `scrollview` yang didalamnya diisi dengan `textview` berita.

```JAVA
<ScrollView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
       <TextView ... />
</ScrollView>
```
###  Capture hasil:


## 4. Fibonacci
### 1. Metode countUp(View view)

```JAVA
public void countUp(View view) {
    EditText inputLimit = findViewById(R.id.input_limit);
    if(!inputLimit.getText().toString().isEmpty()) {
        int limit = Integer.parseInt(inputLimit.getText().toString());
        if(mCount >= limit) {
            Toast.makeText(this, "Telah mencapai limit", Toast.LENGTH_LONG).show();
            return;
        }
    }
    int next = mCount;
    mCount = secondCount;
    secondCount = next + mCount;
    if (mShowCount != null)
        mShowCount.setTextColor(setColor());
    mShowCount.setText(Integer.toString(next));
}
```

Metode ini terfokus pada perhitungan deret Fibonacci dan pembaruan tampilan pada suatu aplikasi. Pertama, nilai batas diambil dari komponen EditText dengan ID "input_limit". Proses ini melibatkan pengecekan apakah nilai batas tidak kosong. Jika tidak kosong, nilai tersebut dikonversi ke tipe data int. Selanjutnya, dilakukan pengecekan apakah nilai saat ini (mCount) lebih besar atau sama dengan batas yang telah ditetapkan. Jika kondisi ini terpenuhi, metode akan menampilkan pesan Toast dan menghentikan eksekusi lebih lanjut.

Jika batas tidak tercapai, metode akan melanjutkan dengan melakukan perhitungan deret Fibonacci dan mengupdate tampilan aplikasi sesuai dengan nilai yang dihitung. Selain itu, metode ini juga mengatur warna teks pada tampilan menggunakan metode setColor(). Dengan pendekatan ini, aplikasi dapat memberikan respons yang sesuai terhadap input pengguna dan memastikan bahwa perhitungan deret Fibonacci dan pembaruan tampilan berjalan dengan tepat.

### Poin-poin:

- Metode ini terkait dengan penanganan perhitungan deret Fibonacci dan pembaruan tampilan.
- Mengambil nilai batas dari EditText dengan ID input_limit.
- Jika batas tidak kosong, maka konversi nilai tersebut ke tipe data int.
- Jika nilai saat ini (mCount) lebih besar atau sama dengan batas, tampilkan pesan Toast dan hentikan eksekusi metode.
- Selanjutnya, lakukan perhitungan deret Fibonacci dan perbarui tampilan sesuai dengan nilai yang dihitung.
- Set juga warna teks pada tampilan menggunakan metode setColor().

### 2. Metode reset(View view)

```JAVA
public void reset(View view) {
    mCount = 0;
    secondCount = 1;
    if (mShowCount != null)
        mShowCount.setText(Integer.toString(mCount));
}
```

### Penjelasan

Metode ini digunakan untuk mereset nilai deret Fibonacci ke awal, di mana variabel mCount diatur kembali menjadi 0 dan secondCount menjadi 1. Setelah reset dilakukan, tampilan kemudian diperbarui dengan nilai-nilai yang telah direset. Proses ini membantu memulai ulang deret Fibonacci dari awal, memberikan basis yang bersih untuk menghitung nilai-nilai selanjutnya dalam deret tersebut.

### Poin-poin:

- Metode ini digunakan untuk mereset nilai deret Fibonacci ke awal (mCount = 0 dan secondCount = 1).
- Kemudian, perbarui tampilan dengan nilai yang direset.

### 3. Metode setColor()

```JAVA
public int setColor() {
    currentFib++;
    if(currentFib % 2 == 0) {
        return ContextCompat.getColor(this, R.color.black);
    } else {
        return ContextCompat.getColor(this, R.color.white);
    }
}
```

### Penjelasan

Metode ini menawarkan fungsionalitas perubahan warna yang sesuai dengan setiap pemanggilannya. Untuk melacak urutan pemanggilan, digunakan variabel currentFib. Ketika currentFib memiliki nilai genap, metode ini mengembalikan warna hitam; sebaliknya, jika nilai currentFib adalah ganjil, warna yang dikembalikan adalah warna putih. Implementasi warna ini memanfaatkan fungsi ContextCompat.getColor() dengan merujuk pada sumber daya warna dari file resource (R.color). Dengan demikian, metode ini memberikan dinamika visual yang menarik, menciptakan variasi warna yang berubah sesuai dengan karakteristik bilangan dalam deret Fibonacci.

### Poin-poin:

- Metode ini memberikan warna yang berubah sesuai dengan setiap pemanggilannya.
- Menggunakan variabel currentFib untuk melacak pemanggilan.
- Jika currentFib adalah bilangan genap, maka warna yang dikembalikan adalah warna hitam; jika ganjil, warna yang dikembalikan adalah warna putih.
- Warna didapatkan menggunakan ContextCompat.getColor() dengan referensi warna dari resource (R.color).

###  Capture hasil:

## 5. Pesan
Kode ini adalah bagian dari sebuah aplikasi Android yang terdiri dari dua aktivitas (MainActivityOne dan MainActivitySecond) dan digunakan untuk berinteraksi antaraktivitas. Berikut adalah penjelasan singkatnya:

Deklarasi Variabel:
- `LOG_TAG`: Variabel untuk tag log, digunakan untuk memudahkan identifikasi log.
- `EXTRA_MESSAGE`: String konstanta yang digunakan sebagai kunci untuk mengirim pesan antar aktivitas.
- `TEXT_REQUEST`: Integer konstanta yang digunakan sebagai kode permintaan untuk `startActivityForResult`.

Inisialisasi UI:
- `onCreate`: Metode yang dipanggil saat aktivitas pertama kali dibuat.
- Mengatur tata letak dengan menggunakan layout dari file `R.layout.activity_one`.
- Mendapatkan referensi ke elemen UI seperti `EditText` dan dua `TextView`.

Button Click Event:
- `launchSecondActivity`: Dipanggil saat tombol diaktivitas ini diklik.
- Membuat objek Intent untuk memulai aktivitas kedua `(MainActivitySecond)`.
- Mengirim pesan yang dimasukkan oleh pengguna melalui `EditText` ke aktivitas kedua menggunakan `putExtra`.
- Memulai aktivitas kedua dengan `startActivityForResult` untuk menerima hasil dari aktivitas kedua.

Handle Result:
- `onActivityResult`: Metode yang dipanggil ketika aktivitas kedua selesai dan memberikan hasil kembali.
- Memeriksa apakah hasil diterima sesuai dengan kode permintaan `(TEXT_REQUEST)`.
- Jika hasil OK, menampilkan header dan isi pesan yang dikirim kembali dari aktivitas kedua pada dua `TextView`.

Kode ini menciptakan pengalaman pengguna di mana pengguna dapat memasukkan pesan di `MainActivityOne`, mengirimkannya ke `MainActivitySecond` melalui tombol, dan menampilkan balasan di `MainActivityOne` setelah aktivitas kedua selesai.

###  Capture hasil:

## 6. Menu
Menu ini adalah bagian dari sebuah aplikasi Android yang mengimplementasikan aktivitas menu dengan menggunakan CardView untuk setiap opsi menu. Kita dapat memilih aplikasi-aplikasi yang kita buat, dengan menggunakan metode intent. Berikut adalah penjelasannya:

Deklarasi Variabel:
`tombolSatu`, `tombolDua`, ..., `tombolDelapan`: Variabel yang merepresentasikan `CardView` untuk setiap opsi menu.

Inisialisasi UI:
- `onCreate`: Metode yang dipanggil saat aktivitas pertama kali dibuat.
- Mengatur tata letak dengan menggunakan layout dari file `R.layout.activity_menuaplikasi`.
- Menginisialisasi setiap `CardView` dan menetapkan `OnClickListener` untuk setiap tombol.

Pengaturan Tombol:
- Setiap tombol (tombolSatu hingga tombolDelapan) memiliki `OnClickListener` yang memulai aktivitas tertentu ketika tombol tersebut diklik. Aktivitas yang dimulai bervariasi dari `MainActivity` hingga `ViewPagerActivity`, dan bahkan membuka aplikasi Google Maps untuk menavigasi ke "Universitas Pelita Bangsa" pada tombol tujuh.
Kode ini memberikan pengguna akses ke berbagai fitur dan aktivitas dalam aplikasi melalui menu dengan menggunakan CardView sebagai elemen UI yang responsif terhadap sentuhan.

###  Capture hasil:

## 7. Maps

```JAVA
Intent mapIntent = new Intent(Intent.ACTION_VIEW);
                mapIntent.setPackage("com.google.android.apps.maps");
```
Membuka aplikasi Google Maps dengan memanggil aplikasi sistem (Implicit intent).

```JAVA
 if (mapIntent.resolveActivity(getPackageManager()) != null) {
                    Uri gmmIntentUri = Uri.parse( "geo:0,0?q=" + Uri.encode( "Universitas Pelita Bangsa" ) );
```
Lalu mengarahkan kita ke target lokasi yang telah di setting.

###  Capture hasil:

## 8. Splash
###  Capture hasil:

## 9. Fragment
###  Capture hasil:

## 10. Trailer
###  Capture hasil:
