# RestFull Oracle With CodeIgniter

#### Prepare :
- Oracle 11G atau versi lainnya
- CodeIgniter (yang sudah terintegrasi dengan OVA)

#### Referensi :
- Youtube [Link](https://www.youtube.com/watch?v=ZAUJmiW1w2Y).
- Oracle Documentation [Link](https://www.oracle.com/webfolder/technetwork/tutorials/obe/db/apex/r51/restful_web_services/restful_web_services.html#overview).
----------------

#### Setting di CodeIgniter
Anda dapat merubah koneksi CI yang terubung dengan API dari Oracle di application/libraries/Api.php
>$this->client = new Client(['base_uri' => 'http://192.168.43.75:8888/apex/obe/']);

Lokasi: 

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/1.png)
