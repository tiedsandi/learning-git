# 🔀 Git Rebase vs Merge

Dalam Git, baik `rebase` maupun `merge` digunakan untuk menggabungkan perubahan dari
satu branch ke branch lain. Namun, keduanya memiliki perilaku yang berbeda dan cocok
untuk situasi yang berbeda pula.

---

## 📌 Tujuan Utama

- **`git merge`**: Menggabungkan riwayat _sebagaimana adanya_, menciptakan commit
  baru yang merepresentasikan gabungan dari dua branch.
- **`git rebase`**: Memindahkan _basis_ dari commit di branch saat ini agar tampak
  seperti dibangun di atas branch target.

---

## 🔁 Perbandingan Singkat

| Aspek          | `merge`                             | `rebase`                        |
| -------------- | ----------------------------------- | ------------------------------- |
| Riwayat commit | Cabang bercabang                    | Riwayat linear                  |
| Commit baru    | Membuat commit gabungan             | Memodifikasi commit yang ada    |
| Konflik        | Bisa terjadi saat merge             | Bisa terjadi saat rebase        |
| Aman dipakai   | Sangat aman, tidak mengubah riwayat | Aman jika commit belum dipush   |
| Cocok untuk    | Riwayat kolaboratif dan audit       | Riwayat bersih dan mudah dibaca |

---

## 🧪 Contoh Kasus

Misal kita punya struktur branch seperti ini:

```text
A---B---C main
         \
          D---E feature
```

### `git merge main` (dari `feature`)

```bash
git checkout feature
git merge main
```

Hasil:

```text
A---B---C main
         \
          D---E---M feature
```

- M = commit merge
- Riwayat tetap bercabang

### `git rebase main` (dari `feature`)

```bash
git checkout feature
git rebase main
```

Hasil:

```text
A---B---C main
             \
              D'--E' feature
```

- D' dan E' = commit baru hasil rebase
- Riwayat jadi linear

---

## 🧭 Diagram Alur Rebase vs Merge

```
[main] --- A --- B --- C
                     \
[feature]             D --- E

# Setelah git merge main (di feature):
[feature]             D --- E --- M
                     /
[main] --- A --- B --- C

# Setelah git rebase main (di feature):
[main] --- A --- B --- C
                         \
[feature]                 D' --- E'
```

> Diagram ini menunjukkan visual sederhana bagaimana `merge` menciptakan node
> tambahan, sementara `rebase` membuat ulang commit di atas branch target.

---

## ⚠️ Kapan Menggunakan Rebase

Gunakan `rebase` saat:

- Ingin menjaga riwayat commit tetap linear
- Belum mem-push perubahan ke remote
- Dalam tahap pengembangan pribadi

> **Jangan rebase branch yang sudah dibagikan ke orang lain**

---

## 🔧 Tips Praktis

- Gunakan `git pull --rebase` daripada `git pull` biasa untuk menghindari commit
  merge yang tidak perlu.
- Jika terjadi konflik saat rebase:

```bash
git status         # lihat file konflik
git add <file>     # setelah konflik diselesaikan
git rebase --continue
```

- Jika ingin batalkan rebase:

```bash
git rebase --abort
```

---

## 📚 Referensi Tambahan

- [Atlassian Git Rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)
- [Git Merge vs Rebase](https://www.git-scm.com/book/en/v2/Git-Branching-Rebasing)
- [Visualisasi Rebase vs Merge](https://www.git-tower.com/learn/git/faq/git-rebase-vs-merge)
