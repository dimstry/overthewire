# Bandit

← [Kembali ke daftar game](../README.md) · Sumber: https://overthewire.org/wargames/bandit/

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
| [0](level-00.md) | Login SSH | `ssh` | ✅ Masuk sebagai bandit0 |
| [0 → 1](level-01.md) | Baca file `readme` | `cat` | ✅ Password bandit1 |
| [1 → 2](level-02.md) | Baca file bernama `-` | `cat ./-` | ✅ Password bandit2 |
| [2 → 3](level-03.md) | Baca file dengan spasi & diawali `--` | `cat "./--spaces in this filename--"` | ✅ Password bandit3 |
| [3 → 4](level-04.md) | Cari file tersembunyi | `ls -la` | ✅ Password bandit4 |
| [4 → 5](level-05.md) | Cari satu-satunya file yang bisa dibaca manusia | `file ./*` | ✅ Password bandit5 |

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
