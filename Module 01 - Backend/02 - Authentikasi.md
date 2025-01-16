## Autentikasi
`Gunakan sanctum / bearer token untuk melakukan autentikasi`

### Login

- Endpoint : `/api/v1/auth/login`
- Method : `POST`
- Description : `Agar staff / admin terautentikasi`
- Request : 
    - Body
        ```json
        {
            "username": "required",
            "password": "required"
        }
        ```
- Response
    - Success [201]
        ```json
        {
            "message": "Login Berhasil",
            "token": "{token}",
            "user": {
                "name": "Arif Doank",
                "username": "arif_gans123"
            }
        }
        ```
    - Error [401]
        ```json
        {
            "message": "Username / password salah"
        }
        ```


### Logout

- Endpoint : `/api/v1/auth/logout`
- Method : `POST`
- Description : `Agar pengguna dapat keluar dari akun`
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
            "message": "Berhasil logout"
        }
        ```
    - Error [401]
        ```json
        {
            "message": "Anda belum terautentikasi"
        }
        ```
