# String Commands

String Commands adalah perintah di John the Ripper Rules yang digunakan untuk menyisipkan string tertentu ke dalam kata sandi pada posisi yang diinginkan.

Perintah ini memungkinkan kamu membuat variasi kata sandi yang lebih panjang atau menambahkan pola tertentu, misalnya menambahkan kata, angka, atau simbol di awal, di tengah, atau di akhir kata sandi.

## Jenis-Jenis Rules

### 1. `AN"STR"`

Simbol `AN"STR"` dalam John the Ripper Rules digunakan untuk menyisipkan string `STR` ke dalam kata sandi pada posisi `N`.

- `N = 0` -> menambahkan string di awal kata (prefix)
- `N = z` -> menambahkan string di akhir kata (suffix)
- `N = angka` -> menambahkan string mulai posisi tertentu

Kamu bisa menggunakan tanda double-quote (`"`) untuk memudahkan membaca string, tapi jika string mengandung tanda `"`, kamu bisa memakai karakter lain sebagai delimiter, misalnya `/` atau `,`.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
A0"123"   # prefix
Az"xyz"   # suffix
A2"AB"    # insert di posisi 2
```

Output:

```
123admin   (prefix string "123")
rootxyz    (suffix string "xyz")
adABmin    (insert string "AB" mulai posisi 2)
```

> [!NOTE]
> **Catatan:**
> - Tidak ada cara untuk escape karakter delimiter di dalam string; solusi alternatif adalah menggunakan beberapa perintah berurutan.
> - Rules ini sangat berguna untuk menambahkan pola tertentu yang sering digunakan dalam password, misal angka di akhir, awalan khusus, atau kombinasi kata.
