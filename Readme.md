# 🧰 Git Documentation

> 📚 Dokumentasi Git dari dasar hingga kolaborasi tim.  
> 💡 Langsung ke: [Quick Reference](#-quick-reference) |
> [Navigasi Topik](#-navigasi-topik)

---

## 📁 Quick Reference

### 1. Hubungkan Git ke GitHub

```bash
git remote add origin <url>
# contoh:
git remote add origin https://github.com/username/repo.git
```

### 2. Clone Repository

```bash
git clone <url>
```

### 3. Tambah dan Commit Perubahan

```bash
git add .
git commit -m "pesan"
```

### 4. Push dan Pull

```bash
git push origin main
git pull origin main
```

### 5. Cek Status dan Branch

```bash
git status
git branch
```

### 6. Buat dan Pindah Branch

```bash
git checkout -b fitur-baru
git checkout main
```

### 7. Merge Branch

```bash
git checkout main
git merge fitur-baru
```

### 8. Hapus Branch

```bash
git branch -d fitur-baru
git push origin --delete fitur-baru
```

### 9. Git Stash

```bash
git stash          # simpan sementara
git stash list     # lihat daftar
git stash pop      # kembalikan
```

### 10. Ganti URL Remote

```bash
git remote set-url origin <url-baru>
```

---

### 🐛 Masalah Umum

#### ❌ Push Ditolak

```bash
git pull origin main --rebase
git push origin main
```

#### ❌ Konflik Saat Merge / Pull

```bash
# Edit manual file konflik
git add .
git commit -m "resolve conflict"
```

#### ❌ Commit di Branch yang Salah

```bash
git branch fitur-baru
git checkout fitur-baru
# atau:
git checkout branch-benar
git cherry-pick <hash>
```

#### ❌ File Tertinggal di Git Ignore

```bash
nano .gitignore
git rm --cached nama_file
```

---

### 💡 Tips Kerja Tim

- Tarik dulu perubahan: `git pull origin <branch>`
- Buat branch untuk setiap fitur
- Gunakan pesan commit yang jelas
- Jangan commit `.env`, `node_modules/`, dll
- Gunakan Pull Request sebelum merge ke `main`

---

### ⚙️ Alias Git

Tambahkan ke `~/.gitconfig`:

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

---

## 🧭 Navigasi Topik

### 📘 Git Dasar

- [Pengenalan Git](concepts/introduction.md)
- [Konfigurasi Git](concepts/configuration.md)
- [Staging & Commit](concepts/staging.md)
- [Membatalkan Perubahan](concepts/undo-changes.md)
- [Log & Hash](concepts/commit-log.md)
- [Blame & Versi Sebelumnya](concepts/blame.md)
- [Git Ignore](examples/gitignore-explained.md)
- [Alias Git](concepts/alias.md)

### 🌿 Branching

- [Pengenalan Branch](concepts/branching-intro.md)
- [Merge vs Rebase](concepts/rebase.md)
- [Squash Commit](concepts/squash.md)
- [Stash](concepts/stash.md)
- [Cherry Pick](concepts/cherry-pick.md)
- [Strategi Penamaan Branch](concepts/branch-naming.md)

### ☁️ Git Remote

- [Pengenalan Remote](concepts/remote-intro.md)
- [Push, Pull, Clone](concepts/push-pull-clone.md)
- [Fork dan Pull Request](concepts/fork.md)
- [Submodule](concepts/submodule.md)
- [Tag dan Rilis](concepts/tag.md)

### 🧪 Studi Kasus

- [Merge Conflict](examples/merge-conflict.md)
- [Cherry Pick Demo](examples/cherry-pick-demo.md)
- [Tag Penggunaan](examples/tag-usage.md)
- [Stash di Dunia Nyata](concepts/stash.md)

### 📦 Workflow Tim

- [Gitflow Workflow](workflows/gitflow.md)
- [Strategi Rebase](workflows/rebase-best-practices.md)
- [Trunk Based Development](workflows/trunk-based.md)
- [Forking Workflow](workflows/forking.md)
- [Otomatisasi Rilis](workflows/release-automation.md)

---

```sh
git-guide/
├── README.md                      # Panduan utama & navigasi
├── .gitignore                     # Contoh ignore file
├── .gitconfig                     # Contoh alias Git
├── cheatsheet.md                 # Ringkasan perintah cepat

├── concepts/                     # 📘 Konsep dasar & teori Git
│   ├── introduction.md                   # Pengenalan Git
│   ├── configuration.md                  # Konfigurasi Git
│   ├── repository.md                     # Inisialisasi repo Git
│   ├── hash.md                           # Hash pada Git
│   ├── staging.md                        # Menambah, mengubah, menghapus file
│   ├── undo-changes.md                   # Membatalkan perubahan
│   ├── commit-log.md                     # Commit log & histori
│   ├── compare.md                        # Banding commit
│   ├── rename.md                         # Rename file
│   ├── reset.md                          # Reset commit
│   ├── amend.md                          # Amend commit
│   ├── snapshot.md                       # Revert & versi sebelumnya
│   ├── ignore.md                         # .gitignore dan penjelasannya
│   ├── blame.md                          # Git blame
│   ├── alias.md                          # Git alias

│   ├── branching-intro.md                # Pengenalan branching
│   ├── multiple-branches.md              # Bekerja dengan banyak branch
│   ├── merge.md                          # Merge branch
│   ├── cherry-pick.md                    # Cherry pick
│   ├── rebase.md                         # Rebase vs merge
│   ├── squash.md                         # Squash commit
│   ├── tag.md                            # Tag & versi
│   ├── stash.md                          # Git stash

│   ├── remote-intro.md                   # Pengenalan Git remote
│   ├── git-server.md                     # Apa itu Git server
│   ├── git-server-repo.md                # Remote Git server repository
│   ├── ssh.md                            # Autentikasi SSH
│   ├── remote-repo.md                    # Remote repo: push, fetch, pull
│   ├── push-pull-clone.md                # Push, Pull, Clone, Fetch
│   ├── remote-branch.md                  # Remote branch & tracking
│   ├── pull-request.md                   # Pull request dan kolaborasi
│   ├── submodule.md                      # Git submodule
│   ├── fork.md                           # Forking repo

├── examples/                     # 🧪 Studi kasus & praktik langsung
│   ├── branching.md                      # Workflow dasar branching
│   ├── merge-conflict.md                 # Skenario dan solusi konflik
│   ├── cherry-pick-demo.md               # Contoh cherry-pick nyata
│   ├── rebase-squash-demo.md             # Contoh rebase + squash
│   ├── tag-usage.md                      # Praktik penggunaan tag

├── workflows/                    # 📂 Strategi & kolaborasi tim
│   ├── branch-naming.md                 # Penamaan branch
│   ├── gitflow.md                       # Gitflow Workflow
│   ├── trunk-based.md                   # Trunk Based Development
│   ├── forking-workflow.md              # Forking Workflow
│   ├── rebase-best-practices.md         # Best practice rebase
│   ├── release-automation.md            # CI/CD rilis otomatis (GitHub Actions)
```
