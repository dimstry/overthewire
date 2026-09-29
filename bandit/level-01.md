[← Level 0](level-00.md) · [← Daftar level](README.md) · [Level 2 →](level-02.md)

# Bandit — Level 0 → Level 1

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

[← Level 0](level-00.md) · [← Daftar level](README.md) · [Level 2 →](level-02.md)
