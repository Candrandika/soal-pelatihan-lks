## Transaksi
`Transaksi peminjaman buku oleh peminjam. Seorang peminjam hanya bisa meminjam 1 buku disaat yang bersamaan`

`Semua request pada fitur ini akan merespon error 401 ketika user belum terautentikasi`

- Error [401]
    ```json
    {
        "message": "Anda belum terautentikasi"
    }
    ```

### Get Semua Transaksi

- Endpoint : `/api/v1/transactions`
- Method : `GET`
- Description : `mengambil semua data transaksi`
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
            "message": "Data transaksi berhasil diambil",
            "transactions": [
                {
                    "borrower_name": "Nama Peminjam",
                    "staff_name": "Nama admin",
                    "book_title": "Judul buku",
                    "borrow_at": "2024-01-01 09:14:12",
                    "return_at": null
                }, ...
            ]
        }
        ```

### Tambah Data Transaksi

- Endpoint : `/api/v1/transactions`
- Method : `POST`
- Description : `menambahkan transaksi, stok buku akan berkurang`
- Request : 
    - Headers
        ```json
        {
            "Authorization": "Bearer {token}"
        }
        ```
    - Body
        ```json
        {
            "borrower_member_id": "required",
            "book_id": "required",
        }
        ```
- Response
    - Success [200]
        ```json
        {
            "message": "Data transaksi berhasil ditambahkan"
        }
        ```
    - Error [400]
        ```json
        {
            "message": "Kesalahan dalam input",
            "errors": {
                "book_cover": [
                    "The book id field is required."
                ], ...
            }
        }
        ```
    - Error [400]
        ```json
        {
            "message": "Stok buku kosong"
        }
        ```
    - Error [400]
        ```json
        {
            "message": "Peminjam masih memiliki buku yang belum dikembalikan"
        }
        ```
    - Error [404]
        ```json
        {
            "message": "Buku atau peminjam tidak ditemukan"
        }
        ```


### Update Status Transaksi

- Endpoint : `/api/v1/transactions/{id}`
- Method : `PUT`
- Description : `mengubah status transaksi menjadi buku telah dikembalikan, dan stok buku akan bertambah`
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
            "message": "Status buku diubah menjadi telah dikembalikan",
        }
        ```
    - Error [404]
        ```json
        {
            "message": "Data transaksi tidak ditemukan",
        }
        ```
