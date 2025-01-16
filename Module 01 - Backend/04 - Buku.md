## Buku
`Buku yang bisa ditambakan oleh staff dan bisa dipinjam oleh peminjam`

`Semua request pada fitur ini akan merespon error 401 ketika user belum terautentikasi`

- Error [401]
    ```json
    {
        "message": "Anda belum terautentikasi"
    }
    ```

### Get Semua Buku

- Endpoint : `/api/v1/books`
- Method : `GET`
- Description : `mengambil semua data buku`
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
            "message": "Data buku berhasil diambil",
            "books": [
                {
                    "title": "Judul Buku",
                    "book_cover": "path/to/cover.jpg",
                    "published_year": 2020,
                    "author": "Candra",
                    "publisher": "Candra Juga",
                    "qty": 10
                }, ...
            ]
        }
        ```

### Tambah Data Buku

- Endpoint : `/api/v1/books`
- Method : `POST`
- Description : `menambahkan buku`
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
            "title": "required, min 2 char",
            "book_cover": "required, image, max 1 mb",
            "author": "required",
            "publisher": "required",
            "published_year": "required, number",
            "qty": "required, number",
            "summary": "required"
        }
        ```
- Response
    - Success [200]
        ```json
        {
            "message": "Data buku berhasil ditambahkan"
        }
        ```
    - Error [400]
        ```json
        {
            "message": "Kesalahan dalam input",
            "errors": {
                "book_cover": [
                    "The book cover field is required."
                ], ...
            }
        }
        ```


### Get Detail Buku

- Endpoint : `/api/v1/books/{book_id}`
- Method : `GET`
- Description : `mengambil detail buku`
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
            "message": "Data buku berhasil diambil",
            "book": {
                "title": "Judul Buku",
                "book_cover": "path/to/cover.jpg",
                "published_year": 2020,
                "author": "Candra",
                "publisher": "Candra Juga",
                "qty": 10,
                "summary": "Ringkasan / sinopsis dari buku",
                "borrowing_count": 100
            }
        }
        ```
    - Error [404]
        ```json
        {
            "message": "Data buku tidak ditemukan",
        }
        ```
