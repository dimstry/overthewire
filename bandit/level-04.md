[← Level 3](level-03.md) · [← Daftar level](README.md) · [Level 5 →](level-05.md)

# Bandit — Level 3 → Level 4

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

[← Level 3](level-03.md) · [← Daftar level](README.md) · [Level 5 →](level-05.md)
