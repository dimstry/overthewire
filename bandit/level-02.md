[← Level 1](level-01.md) · [← Daftar level](README.md) · [Level 3 →](level-03.md)

# Bandit — Level 1 → Level 2

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

[← Level 1](level-01.md) · [← Daftar level](README.md) · [Level 3 →](level-03.md)
