## Base URL
Semua *endpoint* dalam dokumentasi ini menggunakan *base URL* berikut:
`http://localhost:8080/api/users`

---

## 1. Menambahkan User Baru (Create)

Menyimpan data pengguna baru ke dalam *database*. Sistem akan menghasilkan ID secara otomatis (UUID).

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3628f042-d163-4f2b-bfd4-5587e2214d8c" />


* **Endpoint:** `/api/users`
* **Method:** `POST`
* **Content-Type:** `application/json`

**Request Body:**
```json
{
  "name": "TestUser",
  "age": 25
}

```

**Responses:**

* **201 Created (Success)**
```json
{
    "status": "success",
    "data": {
        "age": 25,
        "id": "4dc46633-c59d-4526-b2b7-63154c0eda46",
        "name": "TestUser"
    }
}

```


* **400 Bad Request**
Terjadi jika *request body* ada yang kosong, format JSON salah, atau gagal melewati validasi.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f3afb461-198f-4ca3-abd4-5750cc3bcd10" />

---

## 2. Mengambil Semua Data User (Read All)

Mengembalikan daftar semua pengguna yang ada di dalam sistem.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2c0b97d1-5585-4b7a-ba36-6327af44668d" />


* **Endpoint:** `/api/users`
* **Method:** `GET`
* **Content-Type:** `application/json` (Response)

**Request Body:** `Kosong`

**Responses:**

* **200 OK (Success)**
```json
{
    "status": "success",
    "data": [
        {
            "age": 25,
            "id": "4dc46633-c59d-4526-b2b7-63154c0eda46",
            "name": "TestUser"
        },
        {
            "age": 15,
            "id": "db7884d0-338f-46a9-b6a8-ed21c47e1397",
            "name": "Test"
        }
    ]
}

```


*(Akan mengembalikan array `data` kosong `[]` jika belum ada user).*

---

## 3. Mengambil Data User Berdasarkan ID (Read One)

Mencari dan mengembalikan data satu pengguna secara spesifik berdasarkan ID.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/29aee150-749e-4403-9746-a25acb45ed2c" />


* **Endpoint:** `/api/users/{id}`
* **Method:** `GET`
* **Content-Type:** `application/json` (Response)

**Path Variable:**

* `id`: ID unik pengguna (UUID format string).

**Request Body:** `Kosong`

**Responses:**

* **200 OK (Success)**
```json
{
    "status": "success",
    "data": {
        "age": 15,
        "id": "db7884d0-338f-46a9-b6a8-ed21c47e1397",
        "name": "Test"
    }
}

```


* **500 Internal Server Error (Not Found - *Catatan: Error handling default Spring Boot*)**
Terjadi jika ID tidak ditemukan di *database*.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/188528bf-2363-412c-91c5-36bce6cf6544" />


---

## 4. Memperbarui Data User (Update)

Memperbarui informasi `name` dan `age` dari pengguna yang sudah ada berdasarkan ID.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9a9f6580-59f5-40d2-9b60-ad938b3a5e35" />


* **Endpoint:** `/api/users/{id}`
* **Method:** `PUT`
* **Content-Type:** `application/json`

**Path Variable:**

* `id`: ID unik pengguna yang ingin diubah.

**Request Body:**

```json
{
  "name": "Test Update",
  "age": 50
}


```

**Responses:**

* **200 OK (Success)**
```json
{
    "status": "success",
    "data": {
        "age": 50,
        "id": "db7884d0-338f-46a9-b6a8-ed21c47e1397",
        "name": "Test Update"
    }
}

```


* **500 Internal Server Error (Not Found)**
Terjadi jika ID yang ingin di-*update* tidak ditemukan.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/37210978-557b-4bbc-af41-5c1c76a3a0cf" />


---

## 5. Menghapus Data User (Delete)

Menghapus data pengguna dari *database* secara permanen.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/34c3cc5b-8fcb-4850-bd8a-d2e739694d07" />


* **Endpoint:** `/api/users/{id}`
* **Method:** `DELETE`
* **Content-Type:** `application/json` (Response)

**Path Variable:**

* `id`: ID unik pengguna yang ingin dihapus.

**Request Body:** `Kosong`

**Responses:**

* **200 OK (Success)**
```json
{
    "status": "success delete user with id db7884d0-338f-46a9-b6a8-ed21c47e1397"
}

```


* **500 Internal Server Error (Not Found)**
Terjadi jika ID yang ingin dihapus tidak ditemukan di *database*.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ca1a6eee-c09b-48b3-a5f9-efb943764b04" />

Testing pada Tampilan website:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ddaf9833-142a-463d-9d3a-4d3937ea4aa2" />

Pop up data berhasil dikirim:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6a3e52e1-6aa1-47a1-beef-9e14724262c9" />

Setelah add data:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c054fb8a-aae1-48e8-8411-e994b5fdad1d" />

Tampilan MySQL database spring:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6ad13627-e241-46d5-be0c-31eaa122ed92" />

