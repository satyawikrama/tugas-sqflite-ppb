# tugas-sqflite-ppb

Referensi : https://github.com/thisissandipp/flutter-sqflite-example/

## Tahapan Cara Membuat Aplikasi Flutter dengan SQFlite

Berikut adalah langkah-langkah membuat aplikasi Flutter sederhana menggunakan SQLite (SQFlite) seperti pada project ini:

### 1. Inisialisasi Project Flutter
Buat project Flutter baru sesuai dengan tutorial pertemuan 1

### 2. Menambahkan Depedency
Tambahkan dependencies berikut pada pubspec.yaml:
```
dependencies:
  flutter:
    sdk: flutter
  sqflite: ^2.3.0
  path: ^1.9.0
```

### 3. Membuat Model Data Note
Buat file baru note_model.dart di folder lib/model/ untuk merepresentasikan cnote dalam bentuk class Dart yang dapat dikonversi ke format Map untuk keperluan database.
```
class Note {
  final int? id;
  final String title;

  Note({this.id, required this.title});

  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'title': title,
    };
  }

  factory Note.fromMap(Map<String, dynamic> map) {
    return Note(
      id: map['id'],
      title: map['title'],
    );
  }
}
```

### 4. Membuat Helper SQLite
Buat file database_helper.dart di dalam folder lib/db/.
Isi file dengan class DatabaseHelper yang berfungsi untuk:

1. Membuat dan membuka database

2. Membuat tabel

3. Menyimpan data (insertNote)

4. Mengambil data (getNotes)

5. Menghapus data (deleteNote)

### 5. Membuat UI Halaman Utama
Buat file home_page.dart di folder lib/pages/.
Halaman ini berisi:

1. TextField untuk input catatan

2. Tombol tambah catatan

3. ListView untuk menampilkan catatan

4. Tombol hapus di setiap item catatan

### 6. Menghubungkan UI dengan Database
Pada home_page.dart, hubungkan event seperti menambahkan atau menghapus catatan dengan method dari DatabaseHelper, seperti:

1. insertNote() untuk menyimpan data

2. getNotes() untuk mengambil data

3. deleteNote() untuk menghapus data

### 7. Menyiapkan Entry Point
Atur tampilan awal dan tema aplikasi di file main.dart.
