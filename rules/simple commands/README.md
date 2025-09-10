# Simple Commands

Simple Commands adalah perintah dasar di John the Ripper Rules yang digunakan untuk memodifikasi kata sandi dengan cara sederhana, cepat, dan langsung.

Mereka biasanya berupa satu karakter saja, dan masing-masing punya fungsi spesifik, misalnya mengubah huruf, menambah karakter, menghapus, atau membalik kata.

## Jenis-Jenis Rules

### 1. `:`

Simbol `:` dalam John the Ripper Rules adalah perintah no-op yang berarti tidak melakukan perubahan apa pun terhadap kata sandi input. Kata yang masuk akan tetap sama persis tanpa modifikasi. Rule ini biasanya digunakan untuk menjaga kata asli tetap diuji, sebagai placeholder dalam sebuah ruleset, atau untuk memastikan wordlist dasar tetap dipakai bersama variasi lain.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
:
```

Output:

```
admin
root
password
```

### 2. `l`

Simbol `l` dalam John the Ripper Rules digunakan untuk mengubah seluruh huruf dalam kata sandi menjadi huruf kecil (lowercase). Jika input berisi huruf kapital, semuanya akan dikonversi menjadi huruf kecil. Rule ini berguna karena banyak pengguna password menulis kata sandi hanya dengan huruf kecil agar lebih sederhana.

Wordlist dasar:

```
Admin
ROot
PASSWORD
```

Rules:

```
l
```

Output:

```
admin
root
password
```

### 3. `u`

Simbol `u` dalam John the Ripper Rules digunakan untuk mengubah seluruh huruf dalam kata sandi menjadi huruf besar (uppercase). Semua huruf kecil dalam kata akan dikonversi ke huruf kapital. Rule ini penting karena banyak pengguna memilih menulis password dengan huruf kapital penuh agar terlihat lebih kuat atau formal.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
u
```

Output:

```
ADMIN
ROOT
PASSWORD
```

### 4. `c`

Simbol `c` dalam John the Ripper Rules digunakan untuk mengubah huruf pertama kata sandi menjadi huruf kapital (uppercase), sementara huruf lainnya tetap dibiarkan seperti semula. Rule ini meniru pola umum pengguna password yang sering membuat kata dengan huruf kapital di awal, misalnya nama atau kata biasa.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
c
```

Output:

```
Admin
Root
Password
```

### 5. `C` 

Simbol `C` dalam John the Ripper Rules digunakan untuk mengubah huruf pertama kata sandi menjadi huruf kecil (lowercase), sedangkan seluruh huruf setelahnya diubah menjadi huruf kapital (uppercase). Rule ini meniru pola penulisan yang jarang tetapi kadang digunakan pengguna untuk variasi gaya penulisan password.

Wordlist dasar:

```
Admin
Root
Password
```

Rules:

```
C
```

Output:

```
aDMIN
rOOT
pASSWORD
```

### 6. `t`

Simbol `t` dalam John the Ripper Rules digunakan untuk membalikkan (toggle) bentuk huruf dari setiap karakter dalam kata sandi. Huruf kecil akan diubah menjadi huruf besar, dan huruf besar akan diubah menjadi huruf kecil. Rule ini berguna untuk mencoba variasi penulisan password dengan pola campuran huruf besar-kecil yang sering dipakai pengguna.

Wordlist dasar:

```
AdmiN
PaSSworD
RooT
```

Rules:

```
t
```

Output:

```
aDMIn
pAssWORd
rOOt
```

### 7. `TN` 

Simbol `TN` dalam John the Ripper Rules digunakan untuk membalikkan (toggle) bentuk huruf pada karakter tertentu sesuai posisi `N` dalam kata sandi.

- Jika huruf di posisi `N` adalah huruf kecil -> diubah jadi huruf besar.
- Jika huruf di posisi `N` adalah huruf besar -> diubah jadi huruf kecil.
- Posisi `N` dihitung mulai dari `0 (nol)` untuk huruf pertama.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
T0
T1
T2
```

Output:

```
Admin
rOot
paSsword
```

### 8. `r`

Simbol `r` dalam John the Ripper Rules digunakan untuk membalikkan urutan seluruh karakter dalam kata sandi. Karakter pertama menjadi terakhir, karakter terakhir menjadi pertama, dan seterusnya. Rule ini meniru kebiasaan sebagian pengguna yang membuat variasi password dengan cara menulis kata secara terbalik.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
r
```

Output:

```
nimda
toor
drowssap
```

### 9. `d`

Simbol `d` dalam John the Ripper Rules digunakan untuk menduplikat kata sandi secara penuh, sehingga hasilnya adalah kata asli yang ditulis dua kali berurutan. Rule ini bermanfaat karena sebagian pengguna membuat password dengan pola pengulangan kata agar mudah diingat.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
d
```

Output:

```
adminadmin
rootroot
passwordpassword
```

### 10. `f`

Simbol `f` dalam John the Ripper Rules digunakan untuk mencerminkan (reflect) kata sandi, yaitu dengan menambahkan versi terbalik (reversed) dari kata tersebut ke bagian belakangnya.

Dengan rule ini, sebuah kata akan menjadi gabungan antara kata asli + kata yang dibalik.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
f
```

Output:

```
adminnimda
roottoor
passworddrowssap
```

### 11. `{`

Simbol `{` dalam John the Ripper Rules digunakan untuk memutar (rotate) kata sandi satu karakter ke kiri. Karakter pertama akan dipindahkan ke posisi terakhir, sementara karakter lainnya bergeser satu posisi ke depan.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
{
```

Output:

```
dmina
ootr
asswordp
```

### 12. `}`

Simbol `}` dalam John the Ripper Rules digunakan untuk memutar (rotate) kata sandi satu karakter ke kanan. Karakter terakhir akan dipindahkan ke posisi pertama, sementara karakter lainnya bergeser satu posisi ke kanan.

Wordlist dasar:

```
dmina
ootr
asswordp
```

Rules:

```
}
```

Output:

```
admin
root
password
```

### 13. `$X`

Simbol `$X` dalam John the Ripper Rules digunakan untuk menambahkan (append) karakter `X` di akhir kata sandi. Karakter `X` bisa berupa huruf, angka, atau simbol apa pun.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
$1$2$3
```

Output:

```
admin123
root123
password123
```

### 14. `^X`

Simbol `^X` dalam John the Ripper Rules digunakan untuk menambahkan (prepend) karakter `X` di awal kata sandi. Karakter `X` bisa berupa huruf, angka, atau simbol apa pun.

Wordlist dasar:

```
admin
root
password
```

Rules:

```
^3^2^1
```

Output:

```
123admin
123root
123password
```
