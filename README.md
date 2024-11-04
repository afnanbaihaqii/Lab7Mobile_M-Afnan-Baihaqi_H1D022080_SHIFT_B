Nama : M Afnan Baihaqi
Nim : H1D022080
Shift : B

### Screenshot 
![Screenshot 2024-11-04 133937](https://github.com/user-attachments/assets/e919ce8a-a91d-483d-97ab-15c8a980a6fa)
![Screenshot 2024-11-04 134046](https://github.com/user-attachments/assets/f4d7f812-9e42-41c9-82e4-efe26e3c9bde)

### Penjelasan 

Pengguna Memasukkan Kredensial:

Pengguna memasukkan username dan password di halaman login dan menekan tombol login untuk mengirimkan data.
Validasi Input di Aplikasi:

Fungsi login() dalam komponen LoginPage memeriksa apakah username dan password tidak kosong.
Jika salah satu kosong, aplikasi akan menampilkan notifikasi dengan pesan “Username atau Password Tidak Boleh Kosong” tanpa melanjutkan ke proses berikutnya.
Mengirim Permintaan ke Server:

Jika username dan password sudah terisi, data tersebut dikemas dalam sebuah objek data.
Fungsi postMethod pada AuthenticationService kemudian dipanggil untuk mengirimkan data ke server menggunakan HTTP POST pada endpoint yang disediakan (login.php dalam contoh ini).
Proses Validasi di Server:

Server menerima permintaan, membaca username dan password, lalu memverifikasi apakah informasi tersebut cocok dengan data yang ada di basis data.
Jika kredensial sesuai, server akan mengembalikan respons yang menunjukkan bahwa login berhasil (status_login bernilai “berhasil”), serta mengirimkan token autentikasi dan username pengguna.
Jika kredensial tidak cocok, server mengembalikan respons bahwa login gagal (misalnya, dengan status_login bukan “berhasil”).
Pengolahan Respons di Aplikasi:

Aplikasi menerima respons server.
Jika status_login bernilai "berhasil", aplikasi akan memanggil fungsi saveData pada AuthenticationService, menyimpan token dan username secara lokal menggunakan Preferences dari Capacitor.
Setelah data tersimpan, username dan password pada halaman login akan direset ke kosong untuk keamanan, dan pengguna dialihkan ke halaman utama (/home) menggunakan router.navigateByUrl('/home').
Menampilkan Notifikasi Jika Login Gagal:

Jika status_login tidak sesuai atau ada masalah koneksi, aplikasi akan memanggil metode notifikasi() untuk menampilkan pesan kesalahan.
Pesan yang muncul bisa berupa “Username atau Password Salah” jika server mengembalikan status gagal, atau “Login Gagal Periksa Koneksi Internet Anda” jika terjadi masalah koneksi.
Status Autentikasi dan Penggunaan Token:

Setelah login berhasil, status autentikasi diset ke true dalam AuthenticationService.
Status autentikasi ini dapat digunakan oleh komponen lain atau route guard untuk memastikan bahwa pengguna telah login sebelum mengakses halaman tertentu.

