[← Daftar level](README.md) · [Level 1 →](level-01.md)

# Bandit — Level 0

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

[← Daftar level](README.md) · [Level 1 →](level-01.md)
