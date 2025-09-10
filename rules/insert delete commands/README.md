# Insert/Delete Commands

Insert/Delete Commands adalah perintah di John the Ripper Rules yang digunakan untuk menyisipkan atau menghapus karakter pada kata sandi.

Perintah ini memungkinkan modifikasi kata sandi yang lebih spesifik karena dapat menargetkan posisi tertentu dalam kata. Dengan Insert/Delete Commands, kamu bisa membuat variasi kata sandi yang lebih kompleks, misalnya menambahkan huruf/simbol di tengah kata atau menghapus karakter tertentu untuk menguji kemungkinan kombinasi password.

## Jenis-Jenis Rules

### 1. `[`

Simbol `[` dalam John the Ripper Rules berarti menghapus karakter pertama dari kata sandi input. Kata yang dimodifikasi akan kehilangan huruf pertama.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
\[
```

Output:

```
dmin
oot
assword
```

### 2. `]`

Simbol `]` dalam John the Ripper Rules berarti menghapus karakter terakhir dari kata sandi input. Kata yang dimodifikasi akan kehilangan huruf terakhir.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
\]
```

Output:

```
admi
roo
passwor
```

### 3. `DN`

Simbol `DN` dalam John the Ripper Rules berarti menghapus karakter di posisi `N` (posisi dihitung mulai dari `0`).

Wordlist dasar:

```
admin
root
password
```

Rules:

```
D2
```

Output:

```
adin      (hapus karakter di posisi 2 -> 'm')
rot       (hapus karakter di posisi 2 -> 'o')
pasword   (hapus karakter di posisi 2 -> 's')
```

### 4. `xNM`

Simbol `xNM` dalam John the Ripper Rules berarti mengambil substring dari posisi `N` sepanjang `M` karakter.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
x13
```

Output:

```
dmi      (mulai posisi 1, ambil 3 karakter)
oo       (mulai posisi 1, ambil 3 karakter -> tapi hanya 2 tersisa)
ass      (mulai posisi 1, ambil 3 karakter)
```

### 5. `iNX`

Simbol `iNX` dalam John the Ripper Rules berarti menyisipkan karakter `X` di posisi `N`, dan karakter lain digeser ke kanan.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
i1a
```

Output:

```
aadmin   (sisipkan 'a' di posisi 1)
raoot    (sisipkan 'a' di posisi 1)
paassword (sisipkan 'a' di posisi 1)
```

### 6. `oNX`

Simbol `oNX` dalam John the Ripper Rules berarti mengganti karakter di posisi `N` dengan karakter `X` (overstrike).

Wordlist dasar:

```
admin
root
password
```

Rules:

```
o2x
```

Output:

```
adxin    (ganti posisi 2 dengan 'x')
rox      (ganti posisi 2 dengan 'x')
paxswrd  (ganti posisi 2 dengan 'x')
```

> [!NOTE]
> **Catatan:**
>
> - Tanda kurung siku `[` dan `]` adalah karakter khusus bagi preprocessor JTR.
> - Jika ingin menggunakan perintah ini secara literal, harus di-escape dengan backslash `\[` atau `\]`.
> - Beberapa perintah, seperti `xNM` untuk extract/insert substring, juga termasuk dalam kategori Memory Access Commands.
