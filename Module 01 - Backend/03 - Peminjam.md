## Peminjam
`Peminjam adalah orang / member yang bisa meminjam buku di perpustakaan`

`Semua request pada fitur ini akan merespon error 401 ketika user belum terautentikasi`

- Error [401]
    ```json
    {
        "message": "Anda belum terautentikasi"
    }
    ```

### Get Semua Peminjam

- Endpoint : `/api/v1/borrowers`
- Method : `GET`
- Description : `mengambil semua data peminjam`
- Request : 
    - Headers
        ```json
        {
            "Authorization": "Bearer {token}"
        }
        ```
- Response
    - Success [200]
        ```json
        {
            "message": "Data peminjam berhasil diambil",
            "borrowers": [
                {
                    "member_id": 2024010001,
                    "name": "Nama Peminjam",
                    "gender": "l",
                    "age": 18
                }, ...
            ]
        }
        ```

### Get Detail Peminjam

- Endpoint : `/api/v1/borrowers/{member_id}`
- Method : `GET`
- Description : `mengambil data detail peminjam berdasarkan member_id`
- Request : 
    - Headers
        ```json
        {
            "Authorization": "Bearer {token}"
        }
        ```
- Response
    - Success [200]
        ```json
        {
            "message": "Detail peminjam berhasil didapatkan",
            "borrower": {
                "member_id": 2024010001,
                "name": "Nama Peminjam",
                "gender": "l",
                "age": 18,
                "address": null,
                "borrowing_books_count": 1,
                "borrowing_books": [
                    {
                        "title": "Judul Buku",
                        "published_year": 2020,
                        "author": "Candra",
                        "publisher": "Candra Juga",
                    }, ...
                ]
            }
        }
        ```
    - Error [404]
        ```json
        {
            "message": "Data peminjam tidak ditemukan"
        }
        ```
