# 🤖 Otomasi Release dengan GitHub Actions

GitHub Actions memungkinkan kamu membuat _workflow_ otomatis untuk men-_deploy_,
_build_, dan _release_ proyek kamu. Kita bisa otomatis membuat release setiap kali
tag baru dibuat.

---

## 📦 Tujuan Otomasi Release

- Membuat GitHub Release saat push tag
- Menambahkan changelog otomatis
- (Opsional) Upload asset build

---

## 🔧 Contoh Workflow: release.yml

Buat file `.github/workflows/release.yml`:

```yaml
name: Release on Tag

on:
  push:
    tags:
      - "v[0-9]+.[0-9]+.[0-9]+" # hanya tag versi vX.Y.Z
  workflow_dispatch: # ✋ untuk manual trigger

jobs:
  release:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Install dependencies
        run: npm install

      - name: Build project
        run: npm run build

      - name: Create GitHub Release
        uses: softprops/action-gh-release@v1
        with:
          generate_release_notes: true
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: Upload build file (opsional)
        uses: softprops/action-gh-release@v1
        with:
          files: dist/*.zip
```

---

## ✏️ Penjelasan:

- `on.push.tags`: hanya jalan saat push tag versi seperti `v1.0.0`
- `workflow_dispatch`: bisa jalankan workflow secara manual
- `build project`: pastikan hasil build tersedia sebelum diupload
- `softprops/action-gh-release`: membuat GitHub Release dari tag secara otomatis
- `generate_release_notes`: membuat catatan rilis dari commit

---

## 📂 Tambahkan Aset (Build File)

Pastikan file `.zip` atau hasil build kamu sudah dibuat sebelum step upload:

```yaml
- name: Upload build file
  uses: softprops/action-gh-release@v1
  with:
    files: dist/*.zip
```

---

## 🔐 Token Akses

GitHub sudah menyediakan `GITHUB_TOKEN` otomatis, cukup aman digunakan untuk
keperluan rilis.

---

## 💡 Tips Lanjutan

- Gunakan `conventional commits` untuk changelog lebih rapi
- Tambahkan _workflow dispatch_ untuk rilis manual
- Integrasikan dengan notifikasi Slack/Discord/email
- Gunakan [actions/upload-artifact](https://github.com/actions/upload-artifact) jika
  ingin simpan hasil build antar job

---

## 🌐 Contoh Repo Nyata

Berikut beberapa contoh implementasi GitHub Actions untuk release:

- [vercel/next.js](https://github.com/vercel/next.js/tree/canary/.github/workflows)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [semantic-release/semantic-release](https://github.com/semantic-release/semantic-release)

Kamu bisa pelajari bagaimana mereka menyusun workflow lengkap termasuk release
automation.

---

## 📚 Referensi

- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Create Releases using Actions](https://docs.github.com/en/actions/publishing-packages/publishing-releases)
