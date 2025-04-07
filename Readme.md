# 🛠️ GIT

## 1. Cara Menghubungkan Git dengan GitHub

```bash
git remote add origin <link>
# contoh:
git remote add origin https://github.com/username/repo.git
```

## 2. Cek Remote yang Sudah Terhubung

```bash
git remote -v
```

## 3. Clone Repository

```bash
git clone <link>
# contoh:
git clone https://github.com/username/repo.git
```

## 4. Menambahkan Perubahan ke Staging

```bash
git add .
# atau hanya file tertentu:
git add nama_file.txt
```

## 5. Commit Perubahan

```bash
git commit -m "pesan commit"
```

## 6. Push ke Remote

```bash
git push origin <nama-branch>
# contoh:
git push origin main
```

## 7. Pull Perubahan dari Remote

```bash
git pull origin <nama-branch>
# contoh:
git pull origin main
```

## 8. Membuat Branch Baru dan Pindah Sekaligus

```bash
git checkout -b nama-branch
```

## 9. Ganti ke Branch Lain

```bash
git checkout nama-branch
```

## 10. Merge Branch

```bash
git checkout main
git merge nama-branch
```

## 11. Cek Status dan Branch Saat Ini

```bash
git status
git branch
```

## 12. Hapus Branch

```bash
# local
git branch -d nama-branch
# remote
git push origin --delete nama-branch
```

## 13. Menyimpan Perubahan Sementara (Stash)

```bash
git stash
# untuk lihat daftar stash:
git stash list
# ambil stash terakhir:
git stash pop
```

## 14. Ganti URL Remote

```bash
git remote set-url origin <url-baru>
```

---

## 🐛 Kendala Umum dan Solusinya

### 1. Push Ditolak (non-fast-forward)

```bash
# Masalah:
# error: failed to push some refs to ...

# Solusi:
git pull origin <branch> --rebase
# lalu push ulang:
git push origin <branch>
```

### 2. Terjadi Conflict saat Pull atau Merge

```bash
# Buka file yang konflik (ada tanda <<<<<<< HEAD)
# Edit secara manual, lalu:

git add .
git commit -m "resolve conflict"
```

### 3. Commit di Branch yang Salah

```bash
# Buat branch baru dari commit tersebut
git branch nama-baru
git checkout nama-baru

# atau pindahkan commit pakai cherry-pick:
git checkout branch-yang-benar
git cherry-pick <commit-hash>
```

### 4. Lupa Tambah File ke .gitignore

```bash
# Tambah file ke .gitignore
nano .gitignore

# Hapus file dari git tapi tetap ada secara lokal
git rm --cached nama_file
```

---

## 💡 Tips Penggunaan Git dalam Tim

- Selalu `git pull origin <branch>` sebelum mulai kerja.
- Buat branch baru untuk setiap fitur/bugfix.
- Commit sering dengan pesan yang jelas dan singkat.
- Gunakan `.gitignore` untuk menghindari file tidak penting ikut ke repo.
- Review sebelum push (`git diff`, `git status`).
- Gunakan pull request dan code review sebelum merge ke `main`.

---

## ⚙️ Git Alias (Tambah ke .gitconfig)

Untuk mempermudah penggunaan Git, bisa menambahkan alias berikut ke file
`~/.gitconfig`:

```ini
[alias]
  st = status
  co = checkout
  br = branch
  cm = commit -m
  aa = add .
  lg = log --oneline --graph --all --decorate
  last = log -1 HEAD
  undo = reset --soft HEAD~1
```

> 💡 Cara edit:

```bash
nano ~/.gitconfig
```

Setelah itu, kamu bisa jalankan Git dengan cara singkat seperti:

```bash
git st        # git status
git co main   # git checkout main
git lg        # log ringkas dengan graph
```

## 📁 .gitignore

File `.gitignore` digunakan untuk mengabaikan file/folder yang tidak perlu dimasukkan
ke repo Git. Contoh: `node_modules/`, `.env`, `*.log`, dll. Ini penting agar repo
tetap bersih dan ringan.

---

## 📚 Navigasi Lanjutan

Untuk topik lanjutan, contoh kasus, dan panduan tambahan:

- 📁 [examples/](./examples)

  - [branching.md](./examples/branching.md)
  - [merge-conflict.md](./examples/merge-conflict.md)
  - [gitignore-explained.md](./examples/gitignore-explained.md)

- 📁 [concepts/](./concepts)
  - [branch-naming.md](./concepts/branch-naming.md)
  - [rebase-vs-merge.md](./concepts/rebase-vs-merge.md)
  - [rebase-best-practices.md](./concepts/rebase-best-practices.md)
