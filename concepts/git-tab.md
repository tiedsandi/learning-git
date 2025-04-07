# 🔖 Git Tag

Git Tag digunakan untuk memberi penanda (milestone) pada commit tertentu, biasanya
dipakai untuk merilis versi atau menandai titik penting.

---

## 🏷️ Jenis Tag

### 1. Lightweight Tag

Tag sederhana yang hanya penanda pada commit tertentu (tanpa metadata).

```bash
git tag v1.0.0
```

### 2. Annotated Tag

Berisi metadata seperti penulis, tanggal, dan pesan.

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
```

### Lihat Daftar Tag

```bash
git tag
```

### Lihat Detail Tag Tertentu

```bash
git show v1.0.0
```

---

## 🚀 Membagikan Tag ke Remote

Secara default, `git push` tidak mengirim tag. Gunakan:

```bash
git push origin v1.0.0
```

Untuk semua tag:

```bash
git push origin --tags
```

---

## ✏️ Mengedit Tag yang Salah

### Hapus Tag Lokal

```bash
git tag -d v1.0.0
```

### Hapus Tag di Remote

```bash
git push origin --delete v1.0.0
```

### Ganti dengan Tag Baru

```bash
git tag -a v1.0.1 -m "Fix typo"
git push origin v1.0.1
```

---

## 🏷️ Format Penamaan Tag

Agar konsisten dan mudah dilacak, gunakan pola penamaan tag yang jelas dan standar.
Beberapa contoh umum:

| Format            | Keterangan                                                         |
| ----------------- | ------------------------------------------------------------------ |
| `v1.0.0`          | Versi stabil (mengikuti [Semantic Versioning](https://semver.org)) |
| `v1.2.3-beta`     | Rilis beta (pre-release)                                           |
| `v2.1.0-featureX` | Tag rilis khusus fitur tertentu                                    |
| `v1.0.0+build123` | Tambahan info build (non-breaking info)                            |

📌 **Tips**:

- Gunakan prefix `v` agar mudah dibedakan dari nama branch
- Hindari spasi: pakai `-` atau `.`
- Gunakan [semver](https://semver.org) sebagai dasar: `MAJOR.MINOR.PATCH`

---

## 🚀 Hubungkan Tag dengan GitHub Releases

Setelah membuat tag, kamu bisa:

1. Buka halaman repo GitHub
2. Klik **Releases > Draft a new release**
3. Pilih tag yang sudah dibuat (atau buat baru)
4. Tambahkan changelog atau catatan
5. (Opsional) Upload file `.zip`, `.exe`, dll

---

## 💡 Tips dan Best Practice

- Gunakan tag hanya di commit yang benar-benar siap dirilis
- Tambahkan deskripsi/tag message agar jelas
- Gunakan annotated tag untuk produksi
- Hindari menghapus tag yang sudah dipakai orang lain (kecuali force re-tagging
  memang disetujui)
- Tandai rilis awal fitur besar dengan tag (misal: `v2.0.0-auth-feature`)

---

## 📚 Referensi

- [Git Tag Documentation](https://git-scm.com/docs/git-tag)
- [About Releases – GitHub Docs](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases)
- [Semantic Versioning](https://semver.org/)
