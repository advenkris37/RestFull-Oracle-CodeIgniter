# RestFull Oracle With CodeIgniter

#### Prepare :
- Oracle 11G atau versi lainnya
- CodeIgniter (yang sudah terintegrasi dengan OVA)

#### Referensi :
- Youtube [Link](https://www.youtube.com/watch?v=ZAUJmiW1w2Y).
- Oracle Documentation [Link](https://www.oracle.com/webfolder/technetwork/tutorials/obe/db/apex/r51/restful_web_services/restful_web_services.html#overview).
----------------

#### Setting di CodeIgniter
Anda dapat merubah koneksi CI yang terubung dengan API dari Oracle di **application/libraries/Api.php**

```
$this->client = new Client(['base_uri' => 'http://192.168.43.75:8888/apex/obe/']);
```

Lokasi: 

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/1.png)

Anda dapat merubah variable berdasarkan kebutuhan anda  sesuai dengan variable pada Database pada **application/js/app.js**

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/2.png)
----------------

### Table Database

- Database Barang

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/3.png)

- Database Customer

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/4.png)

- Database Pembelian

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/5.png)

- Database Penjualan

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/6.png)

- Database Supplier

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/7.png)
----------------

# RestFull

```
Setiap bagian pada action, disesuaikan dengan Method yang ada
```

Semua menggunakan metode 
- Post
- Put
- Get
- Delete

```
Untuk server local atau tidak menggunakan SSL setting Require Secure Access : NO
```

```
Untuk server yang sudah menggunakan HTTPS setting Require Secure Access : YES
```

- Kebutuhan RestAPI pada program ini, ubah sesuai kebutuhan kalian dengan method yang kalian butuhkan

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/8.png)
