# 🔥 Contoh & Penyelesaian Merge Conflict

Merge conflict bisa terjadi saat dua branch mengubah baris kode yang sama, dan Git
tidak tahu mana yang harus dipilih.

## 💡 Contoh Kasus

Misalnya:

- Kamu punya `main` branch
- Temanmu kerja di `fitur-a` dan kamu kerja di `fitur-b`
- Keduanya mengubah baris yang sama di file `hello.txt`

```
main:       Halo dunia!
fitur-a:    Halo dunia dari A!
fitur-b:    Halo dunia dari B!
```

Lalu kamu merge `fitur-b` ke `main`:

```bash
git checkout main
git merge fitur-b
```

Berhasil. Tapi saat merge `fitur-a`, akan muncul konflik:

```bash
git merge fitur-a
```

## 🚨 Tanda Merge Conflict di File

Git akan menandai konflik di file seperti ini:

```txt
<<<<<<< HEAD
Halo dunia dari B!
=======
Halo dunia dari A!
>>>>>>> fitur-a
```

## ✅ Cara Menyelesaikan

1. Buka file konflik (misal: `hello.txt`)
2. Pilih baris yang ingin dipertahankan, edit manual
3. Hapus tanda `<<<<<<<`, `=======`, dan `>>>>>>>`
4. Simpan file
5. Tambahkan dan commit ulang:

```bash
git add hello.txt
git commit -m "Selesaikan conflict dari fitur-a"
```

## 🧠 Tips

- Selalu `pull` terbaru sebelum mulai kerja
- Gunakan `git status` untuk melihat file konflik
- Gunakan editor dengan fitur visual merge (VSCode, GitKraken, dll)

## 🔗 Referensi

- [Git Official Docs: Resolving Conflicts](https://git-scm.com/docs/git-merge#_how_conflicts_are_presented)
