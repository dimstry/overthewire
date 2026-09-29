[← Level 2](level-02.md) · [← Daftar level](README.md) · [Level 4 →](level-04.md)

# Bandit — Level 2 → Level 3

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

[← Level 2](level-02.md) · [← Daftar level](README.md) · [Level 4 →](level-04.md)
