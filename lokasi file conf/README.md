# Lokasi File `john.conf`

File konfigurasi utama John the Ripper biasanya bernama `john.conf`. Lokasinya tergantung versi JTR dan cara instalasi:

## Versi Linux (apt / package manager)

Lokasi umum:

```
/etc/john/john.conf
/usr/share/john/john.conf
```

Bisa dicek pakai:

```
updatedb
locate john.conf
```

## Versi dari Source / GitHub

Jika kamu compile sendiri dari source, biasanya berada di folder `run/`:

```
john/run/john.conf
```
