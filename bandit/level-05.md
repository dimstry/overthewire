[← Level 4](level-04.md) · [← Daftar level](README.md)

# Bandit — Level 4 → Level 5

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

[← Level 4](level-04.md) · [← Daftar level](README.md)
