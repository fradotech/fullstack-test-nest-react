
# Fullstack Assignment: Aplikasi dengan NestJS & ReactJS

## Deskripsi Proyek
Buatlah sebuah aplikasi fullstack yang terdiri dari **backend** dan **frontend**.  
- **Backend:** Menggunakan NestJS, TypeScript, dan PostgreSQL.  
- **Frontend:** Menggunakan React (Vite) dan Ant Design.

Aplikasi ini memiliki dua modul utama, yaitu **Auth** dan **User**, serta tambahan modul **Product** pada Stage 2. Pastikan struktur arsitektur mengikuti pola layer yang jelas dan terpisah, serta pisahkan repository backend dan frontend.

---

## STAGE 1

### A. Modul Auth

1. **Authentication**
   - **Login:** Implementasikan fitur login sesuai dengan panduan [NestJS Authentication](https://docs.nestjs.com/security/authentication).
   - **Logout:** Implementasikan fitur logout sesuai referensi yang sama.

2. **Authorization**
   - Gunakan **Guard** agar hanya user yang telah login yang dapat mengakses halaman internal (misalnya: `/dashboard`). Lihat panduan [NestJS Guards](https://docs.nestjs.com/guards).
   - Jika user belum login, akses ke halaman seperti `/dashboard` harus diblokir.
   - Jika user sudah login, ia tidak boleh mengakses halaman login; lakukan redirect ke `/dashboard`.

### B. Modul User

Implementasikan operasi CRUD untuk user dengan spesifikasi berikut:

1. **Create:** Menambahkan data user baru.  
2. **Read:**  
   - Menampilkan daftar user.  
   - Menampilkan detail masing-masing user.
3. **Update:** Memperbarui data user.  
4. **Delete:** Menghapus user.

---

## Aturan Umum

### Struktur Repositori
- **Pisahkan Repository:** Buat repository terpisah untuk backend dan frontend.
- **Penamaan File:** Gunakan awalan nama modul untuk file, contohnya:
  - Untuk modul user: `UserController`, `UserService`, `UserRepository`  
  (hindari penamaan seperti `CreateUser.tsx` atau `UpdateUser.tsx` agar pencarian file menjadi lebih mudah).

---

## Aturan Backend

- **Framework & Bahasa:** Gunakan NestJS dengan TypeScript.
- **Database:** Gunakan PostgreSQL.
- **Modularisasi:** Setiap modul (misalnya, `UserModule`) harus memiliki struktur file yang terpisah:
  - **Controller:** Sebagai presenter yang menangani request dan menentukan format response.
  - **Service:** Berisi logika bisnis.
  - **Repository:** Menjadi penghubung antara aplikasi dan database.

  Lihat referensi:  
  - [NestJS Modules](https://docs.nestjs.com/modules)  
  - [Controller-Service-Repository Pattern](https://www.linkedin.com/pulse/controller-service-repository-pattern-comprehensive-guide-shikder-azicc/)

- **Format API:** Request dan response API harus menggunakan format `snake_case`.

---

## Aturan Frontend

- **Bundler & Framework:** Gunakan React dengan Vite (lihat [Vite Guide](https://vite.dev/guide/)).
- **UI Framework:** Gunakan Ant Design untuk:
  - Komponen UI.
  - Form (lihat [Ant Design Form](https://ant.design/components/form)).
  - Tabel (lihat [Ant Design Table](https://ant.design/components/table)).
- **API Layer:**
  - Buat file `api.service.ts` untuk konfigurasi dan pengaturan koneksi menggunakan Axios.
  - Buat file API khusus, misalnya `user.api.ts`, yang berisi method untuk menghubungkan ke endpoint backend (contoh: `user.create()`, `user.update()`, dll).
- **Custom Hooks:**
  - Pisahkan logika dan tampilan UI dengan membuat custom hook. Contoh:
    - Komponen UI: `UserCreate`
    - Form dan logika: `UserCreateForm.tsx` yang menggunakan hook seperti `useUserForm()`  
      (lihat referensi: [Creating Custom Hooks](https://dev.to/rowsanali/creating-custom-hooks-in-react-for-reusable-logic-ne4)).

---

## STAGE 2

### A. Pagination, Filter, Sort, dan Search (Untuk Modul User)

Pada modul user, lengkapi fitur-fitur berikut:
- **Pagination:** Buat pagination untuk daftar user.  
  Referensi: [API Pagination in NestJS: A Comprehensive Guide](https://medium.com/@solomoncodes/api-pagination-in-nestjs-a-comprehensive-guide-25a212f45f08)
- **Filter:** Tambahkan fitur filter untuk menampilkan user berdasarkan role (misalnya: admin atau user).  
  Referensi: [Tutorial YouTube - Filter](https://www.youtube.com/watch?v=OeWqt7677Kw)
- **Sort:** Implementasikan fitur sorting, misalnya berdasarkan nama atau tanggal pembuatan user.  
  Referensi: [Tutorial YouTube - Sorting](https://www.youtube.com/watch?v=OeWqt7677Kw)
- **Search:** Buat fitur pencarian untuk mencari user berdasarkan nama, role, email, dll.  
  Referensi: [Tutorial YouTube - Search](https://www.youtube.com/watch?v=OeWqt7677Kw)

### B. Modul Product

Implementasikan operasi CRUD untuk produk dengan fitur serupa seperti modul user, dengan tambahan relasi:
1. **Create:** Menambahkan data produk baru.
2. **Read:**  
   - Menampilkan daftar produk dengan fitur pagination, sort, filter, dan search.
3. **Update:** Memperbarui data produk.
4. **Delete:** Menghapus produk.
5. **Relasi:**  
   - **created_by:** Menunjukkan siapa yang membuat produk.  
   - **product_owner:** Menunjukkan siapa Product Owner dari produk tersebut.
