# ✅ Rebase Best Practices

Dokumen ini membahas praktik terbaik dalam penggunaan `git rebase` dalam tim dan
proyek nyata agar penggunaannya aman, efisien, dan menghasilkan riwayat commit yang
bersih.

---

## 🚦 Kapan Waktu Tepat untuk Rebase

- Saat bekerja di **branch pribadi atau fitur** sebelum di-push
- Sebelum membuka pull request (supaya riwayat lebih bersih)
- Saat ingin menyelaraskan branch dengan `main` tanpa membuat merge commit
- Ketika membersihkan riwayat commit (misalnya gabungkan commit kecil)

---

## 🔐 Hindari Rebase Dalam Situasi Ini

- Jika branch sudah di-push dan digunakan orang lain (mengubah history bisa
  membingungkan)
- Saat branch sedang dalam review aktif (lebih baik diskusikan dulu)
- Jika belum paham cara menyelesaikan konflik saat rebase

---

## 🧪 Contoh Rebase Workflow di Branch Fitur

Misal kamu sedang mengerjakan branch `feature/123-fix-login`, sebelum push ke remote:

```bash
git fetch origin
# Rebase dengan branch utama terbaru
git rebase origin/main

# (Opsional) Rapikan riwayat
git rebase -i HEAD~4

# Push hasil rebase
git push origin feature/123-fix-login --force-with-lease
```

> Gunakan `--force-with-lease` agar aman dari overwrite jika ada update dari orang
> lain.

---

## 🧼 Tips Membersihkan Commit

Gunakan **interactive rebase**:

```bash
git rebase -i HEAD~n
```

Lalu ubah `pick` jadi:

- `reword` untuk ubah pesan commit
- `squash` untuk gabung dengan commit sebelumnya
- `drop` untuk buang commit

---

## 👥 Praktik dalam Kolaborasi Tim

- Diskusikan di tim: kapan gunakan merge, kapan gunakan rebase
- Terapkan konvensi seperti rebase saat sebelum PR, merge saat integrasi ke `main`
- Buat dokumentasi / skrip bantu agar rebase tidak membingungkan
- Edukasi anggota tim baru tentang risiko rebase dan kapan aman digunakan

---

## 🔄 Alternatif: Git Merge

Jika tidak yakin, gunakan `merge` saja karena aman dan tidak mengubah history. Rebase
lebih cocok untuk tim yang terbiasa dan nyaman dengan alur git yang lebih "rapi".

---

## 🔁 Flow Diagram: Rebase di Branch Fitur

```text
[Fitur] feature/123
    |
    | git fetch origin
    v
[Sinkron] rebase origin/main
    |
    | git rebase -i
    v
[Bersih] push --force-with-lease
    |
    v
[PR] Buat Pull Request
```

> Diagram alur sederhana ini menunjukkan langkah ideal saat menggunakan rebase di
> branch fitur.

---

## 📋 Checklist Rebase Sebelum PR

✅ Sudah fetch branch `main` terbaru  
✅ Sudah rebase dan konflik diselesaikan  
✅ Commit sudah dirapikan (opsional: squash/reword)  
✅ Push menggunakan `--force-with-lease`  
✅ Sudah diuji ulang setelah rebase

---

## 📚 Referensi

- [Git Rebase Documentation](https://git-scm.com/docs/git-rebase)
- [Rebase vs Merge in Teams – Atlassian](https://www.atlassian.com/git/articles/git-team-workflows-merge-vs-rebase)
- [Visual Interactive Rebase Guide](https://www.git-tower.com/learn/git/faq/git-rebase-vs-merge)
