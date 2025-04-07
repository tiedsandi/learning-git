# 🧳 Git Stash

`git stash` digunakan untuk menyimpan perubahan kerja (working directory) sementara
tanpa perlu commit, sehingga kamu bisa berpindah branch atau mengerjakan hal lain
tanpa kehilangan progres.

---

## 💡 Kapan Menggunakan Git Stash

- Saat sedang coding, tapi harus pindah ke branch lain dulu
- Ketika ada konflik saat `pull` dan kamu belum siap commit
- Untuk menyimpan eksperimen cepat tanpa harus commit

---

## 🔧 Perintah Dasar

### Simpan Semua Perubahan

```bash
git stash
```

### Simpan dengan Pesan

```bash
git stash save "work in progress login page"
```

### Lihat Daftar Stash

```bash
git stash list
```

### Kembalikan Perubahan dari Stash Terakhir

```bash
git stash pop
# atau
git stash apply
```

> `pop` akan menghapus stash dari daftar setelah diterapkan. `apply` tidak.

### Kembalikan Stash Tertentu

```bash
git stash apply stash@{1}
```

### Hapus Stash

```bash
git stash drop stash@{0}    # hapus satu
```

### Hapus Semua Stash

```bash
git stash clear
```

---

## 🚧 Tips dan Best Practice

- Selalu beri pesan stash agar tidak bingung nanti
- Jangan biarkan terlalu banyak stash menumpuk
- Hindari mengandalkan stash sebagai "penyimpan fitur jangka panjang"
- Gunakan `git stash pop` hanya setelah kamu yakin tidak akan menyebabkan konflik
- Jika banyak file berubah, gunakan `git stash -p` untuk memilih secara interaktif

---

## 📦 Gunakan Stash untuk Seleksi Perubahan (Parsial)

```bash
git stash -p
```

> Cocok untuk menyimpan hanya sebagian file atau bagian kode tertentu

---

## 🧩 Contoh Kasus Nyata

### 🧪 Kasus 1: Harus Pull Dulu Tapi Ada Perubahan Lokal

Kamu sedang kerja di `main`, lalu ingin `git pull`, tapi ada file yang belum
disimpan:

```bash
error: Your local changes to the following files would be overwritten by merge:
```

**Solusi:**

```bash
git stash
# lalu pull
git pull origin main
# lalu kembalikan perubahanmu
git stash pop
```

🧭 **Diagram Langkah-Langkah**:

```text
[Edit File] → [git stash] → [git pull origin main] → [git stash pop] → [Lanjut Kerja]
```

### 🧪 Kasus 2: Pindah Ke Branch Lain Tapi Belum Commit

```bash
git checkout feature-x
# error: Please commit your changes or stash them before you switch branches.
```

**Solusi:**

```bash
git stash
# lalu bisa checkout
git checkout feature-x
```

🧭 **Diagram Langkah-Langkah**:

```text
[Edit File] → [git stash] → [git checkout feature-x] → [git stash pop (opsional)]
```

### 🧪 Kasus 3: Stash Banyak Perubahan Tapi Hanya Mau Sebagian

```bash
git stash -p
# pilih perubahan yang ingin disimpan saja
```

🧭 **Diagram Langkah-Langkah**:

```text
[Edit Banyak File] → [git stash -p] → [Pilih Perubahan] → [stash tersimpan sebagian]
```

---

## 📚 Referensi

- [Git Stash Documentation](https://git-scm.com/docs/git-stash)
- [Using Git Stash Effectively – Atlassian](https://www.atlassian.com/git/tutorials/saving-changes/git-stash)
- [Advanced Git Stashing Techniques – StackOverflow](https://stackoverflow.com/questions/19675856/)
