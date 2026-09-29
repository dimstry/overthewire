# Bandit

← [Kembali ke daftar game](README.md) · Sumber: https://overthewire.org/wargames/bandit/

## Aturan Main

Bandit ditujukan untuk **pemula total**. Game ini mengajarkan dasar-dasar yang dibutuhkan untuk memainkan wargame lain.

- Game dibagi per **level**, mulai dari **Level 0**.
- Menyelesaikan satu level = mendapatkan **password** untuk login ke level berikutnya.
- Halaman "Level X" di website berisi petunjuk cara masuk ke level X dari level sebelumnya (contoh: halaman Level 1 menjelaskan cara dari Level 0 ke Level 1).
- Login ke server menggunakan **SSH**:
  - Host: `bandit.labs.overthewire.org`
  - Port: `2220`
  - Username: `banditX` (X = nomor level)
- Password **tidak disimpan otomatis**. Catat sendiri, kalau tidak harus mulai lagi dari bandit0. Password juga **sesekali diganti** oleh pengelola.

**Kalau bingung, website menyarankan:**
1. Baca manual: `man <command>` (contoh `man ls`, tekan `q` untuk keluar).
2. Kalau tidak ada man page, coba `help <command>` (untuk perintah bawaan shell, contoh `help cd`).
3. Cari di search engine.
4. Masih buntu? Tanya di chat komunitas.

## Ringkasan Progres

| Level | Tujuan | Command kunci | Hasil |
|-------|--------|---------------|-------|
| 0 | Login SSH | `ssh` | ✅ Masuk sebagai bandit0 |
| 0 → 1 | Baca file `readme` | `cat` | ✅ Password bandit1 |
| 1 → 2 | Baca file bernama `-` | `cat ./-` | ✅ Password bandit2 |
| 2 → 3 | Baca file dengan spasi & diawali `--` | `cat "./--spaces in this filename--"` | ✅ Password bandit3 |
| 3 → 4 | Cari file tersembunyi | `ls -la` | ✅ Password bandit4 |
| 4 → 5 | Cari satu-satunya file yang bisa dibaca manusia | `file ./*` | ✅ Password bandit5 |

---

## Level 0

**Perintah dari website:**
> The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0.

**Artinya:** Login ke server game menggunakan SSH ke `bandit.labs.overthewire.org` port `2220`, username `bandit0`, password `bandit0`.

**Yang saya lakukan:**
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# masukkan password: bandit0
```
- `-p 2220` → karena server tidak memakai port SSH standar (22).

**Hasil:** ✅ Berhasil login sebagai `bandit0`.

---

## Level 0 → Level 1

**Perintah dari website:**
> The password for the next level is stored in a file called **readme** located in the home directory.

**Artinya:** Password level berikutnya ada di file `readme` di folder home.

**Yang saya lakukan:**
```bash
ls          # lihat isi folder home → ada file "readme"
cat readme  # tampilkan isi file
```

**Hasil:** ✅ Password `bandit1` didapat → `[DISENSOR]`

Login ke level berikutnya:
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

---

## Level 1 → Level 2

**Perintah dari website:**
> The password for the next level is stored in a file called **-** located in the home directory.

**Artinya:** Password ada di file yang namanya hanya tanda strip `-`.

**Yang saya lakukan:**
```bash
ls
cat ./-
```
- Kenapa tidak `cat -` saja? Karena bagi banyak command, `-` berarti "baca dari input keyboard (stdin)", bukan nama file. Dengan `./-` kita tegaskan bahwa itu **file di folder ini**.

**Hasil:** ✅ Password `bandit2` didapat → `[DISENSOR]`

---

## Level 2 → Level 3

**Perintah dari website:**
> The password for the next level is stored in a file called **--spaces in this filename--** located in the home directory.

**Artinya:** Password ada di file bernama `--spaces in this filename--` (ada spasi dan diawali `--`).

**Yang saya lakukan:**
```bash
ls
cat "./--spaces in this filename--"
```
- **Tanda kutip** → supaya spasi dianggap bagian dari nama file, bukan pemisah argumen.
- **`./` di depan** → supaya `--` tidak dianggap sebagai opsi command.

**Hasil:** ✅ Password `bandit3` didapat → `[DISENSOR]`

---

## Level 3 → Level 4

**Perintah dari website:**
> The password for the next level is stored in a **hidden file** in the **inhere** directory.

**Artinya:** Password ada di file tersembunyi di dalam folder `inhere`.

**Yang saya lakukan:**
```bash
cd inhere
ls        # kosong, karena file tersembunyi tidak ditampilkan
ls -la    # -a menampilkan file tersembunyi (nama diawali titik)
cat ...Hiding-From-You
```
- Di Linux, file yang namanya diawali titik `.` adalah file tersembunyi.

**Hasil:** ✅ Password `bandit4` didapat → `[DISENSOR]`

---

## Level 4 → Level 5

**Perintah dari website:**
> The password for the next level is stored in the **only human-readable file** in the **inhere** directory. Tip: if your terminal is messed up, try the "reset" command.

**Artinya:** Di folder `inhere` ada banyak file, tapi hanya satu yang berisi teks yang bisa dibaca manusia. Password ada di situ.

**Yang saya lakukan:**
```bash
cd inhere
ls            # -file00 sampai -file09
file ./*      # cek jenis tiap file
```
Output `file` menunjukkan hampir semua file berjenis `data` (biner), hanya satu yang `ASCII text`:
```
./-file07: ASCII text
```
```bash
cat ./-file07
```
- `file` → mendeteksi jenis isi file tanpa perlu membukanya satu per satu.
- Kalau terminal jadi berantakan karena tidak sengaja `cat` file biner, ketik `reset`.

**Hasil:** ✅ Password `bandit5` didapat → `[DISENSOR]`

---

## Pelajaran yang Didapat (Level 0–5)

| Command | Fungsi |
|---------|--------|
| `ssh user@host -p port` | Login ke server remote |
| `ls` / `ls -la` | Lihat isi folder / termasuk file tersembunyi |
| `cd` | Pindah folder |
| `cat` | Tampilkan isi file |
| `file` | Cek jenis isi file |
| `./nama` | Menegaskan nama file (berguna untuk nama aneh seperti `-` atau `--...`) |
| `"..."` | Membungkus nama file yang mengandung spasi |
