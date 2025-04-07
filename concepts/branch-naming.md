# 📛 Konvensi Penamaan Branch

Penamaan branch yang konsisten sangat penting dalam kolaborasi tim agar alur kerja
lebih jelas, mudah dipahami, dan dapat dilacak. Di bawah ini beberapa konvensi yang
umum digunakan:

---

## 🌱 Struktur Umum

```text
<tipe>/<deskripsi-singkat>
```

Contoh:

```text
feature/login-page
bugfix/login-error
hotfix/crash-on-startup
release/v1.2.0
```

Jika tim kamu menggunakan task management seperti Jira atau Notion, kamu bisa
tambahkan ID task:

```text
feature/1234-login-ui      # ID dari task
bugfix/BUG-89-form-error   # ID dari sistem issue tracking
```

---

## 📌 Tipe Branch yang Umum Digunakan

### `feature/`

Digunakan untuk pengembangan fitur baru.

> Contoh:
>
> - `feature/user-profile`
> - `feature/dashboard-redesign`

### `bugfix/`

Untuk memperbaiki bug non-kritis atau di tahap pengembangan.

> Contoh:
>
> - `bugfix/form-validation`
> - `bugfix/navbar-overlap`

### `hotfix/`

Untuk perbaikan cepat terhadap bug kritis di production.

> Contoh:
>
> - `hotfix/login-crash`
> - `hotfix/missing-assets`

### `release/`

Untuk persiapan rilis aplikasi. Biasanya dipakai untuk testing dan perbaikan minor.

> Contoh:
>
> - `release/v1.0.0`
> - `release/v2.1.3`

### `experiment/`

Dipakai jika ingin melakukan percobaan atau proof-of-concept yang belum tentu
digabungkan.

> Contoh:
>
> - `experiment/ai-autosuggest`

### `refactor/`

Branch untuk perubahan internal seperti penataan ulang kode tanpa mengubah
fungsionalitas.

> Contoh:
>
> - `refactor/api-service`

---

## ✅ Tips Penamaan

- Gunakan `kebab-case` (huruf kecil dan tanda hubung)
- Singkat, tapi cukup deskriptif
- Bisa tambahkan ID task/jira jika ada, contoh: `feature/123-login-ui`
- Hindari karakter spesial dan spasi

---

## 🔄 Alur Umum

```text
main       → branch utama produksi
feature/*  → dikembangkan dari main/develop
bugfix/*   → dikembangkan dari main atau release branch
release/*  → dari main/develop, sebelum digabung ke main
hotfix/*   → langsung dari main, digabung kembali ke main dan develop
```

---

## 📚 Referensi Lanjutan

- [Git Flow oleh Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)
