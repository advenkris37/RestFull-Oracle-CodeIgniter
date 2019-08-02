# RestFull Oracle With CodeIgniter

#### Fungsi Melalui RestFull
- Tambah Data
- Hapus Data
- Edit Data
- Tampil Data

#### Prepare :
- Oracle 11G atau versi lainnya
- CodeIgniter (yang sudah terintegrasi dengan OVA)

### Referensi :
- Youtube [Link](https://www.youtube.com/watch?v=ZAUJmiW1w2Y).
- Oracle Documentation [Link](https://www.oracle.com/webfolder/technetwork/tutorials/obe/db/apex/r51/restful_web_services/restful_web_services.html#overview).
----------------

### Setting di CodeIgniter
Anda dapat merubah koneksi CI yang terubung dengan API dari Oracle di **application/libraries/Api.php**

```
$this->client = new Client(['base_uri' => 'http://192.168.43.75:8888/apex/obe/']);
```

Lokasi: 

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/1.png)

Anda dapat merubah variable berdasarkan kebutuhan anda  sesuai dengan variable pada Database pada **application/js/app.js**

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/2.png)

----------------

### Fungsi RestFull 

- Fungsi semua ini terletak di **Application/controlers** 

Pada Barang ada **Post, Get, Put, Delete** terletak pada **Application/controlers/Barang** 

Untuk menampilkan keseluruhan data di barang:

**Get

```sql
	function index()
	{
		//list barang
		$data = json_decode($this->api->request('get', 'barang'), TRUE);
		$data['barang'] = $data['items'];

		$this->load->view('header/header');
		$this->load->view('barang/list', $data);
		$this->load->view('footer/footer');
	}
```

```sql
	function detil($id = null)
	{
		$data = json_decode($this->api->request('get', 'barang'), TRUE);
		$dataDetail = $this->arr_search($data['items'], "kd_barang", $id);

		if ($id === null) {
			echo "Error";
		} elseif (is_array($dataDetail) === false) {
			echo "Data tidak ditemukan";
		} else {
			$data['dtl'] = $dataDetail[0];
			$this->load->view('header/header');
			$this->load->view('barang/detil', $data);
			$this->load->view('footer/footer');
		}
	}
```

**Post

```sql
	function tambah($d = null)
	{
		if ($d === null) {
			//echo "Form tambah";
			$this->load->view('header/header');
			$this->load->view('barang/tambah');
			$this->load->view('footer/footer');
		} elseif ($d === 'proses') {

			$data = array(
				'nm_barang'		=> $this->input->post('nm_barang'),
				'harga'		=> $this->input->post('harga'),
				'jml_barang' => $this->input->post('jml_barang'),
			);

			$this->api->request('post', 'barang', $data);
			echo '<script language="javascript">';
			echo 'alert("Data Berhasil Ditambah")';
			echo '</script>';
			redirect('barang', 'refresh');
		}
	}
```

**Put

```sql
	function aksiedit()
	{
		$data = array(
			'nm_barang'		=> $this->input->post('nm_barang'),
			'harga'		=> $this->input->post('harga'),
			'jml_barang' => $this->input->post('jml_barang'),
		);
		$this->api->request('PUT', 'barang/' . $this->input->post('kd_barang'), $data);

		echo '<script language="javascript">';
		echo 'alert("Data Berhasil Diubah")';
		echo '</script>';
		redirect('barang', 'refresh');
	}
```

**Delete

```sql
	function hapus($id = null)
	{
		if (!empty($id)) {
			$a = $this->api->request('delete', 'barang/' . $id);
			if ($a) {
				echo '<script language="javascript">';
				echo 'alert("Data Berhasil Dihapus")';
				echo '</script>';
				redirect('barang', 'refresh');
				// echo '<script language="javascript">';
				// echo 'alert("Data Berhasil Dihapus")';
				// echo '</script>';
				// redirect('barang', 'refresh');
			}
		}
	}
```





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

---------------


- Kebutuhan RestAPI pada program ini, ubah sesuai kebutuhan kalian dengan method yang kalian butuhkan

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/8.png)

### 1. Template

- Pada template ini untuk mengambil hasil JSON dengan Variable bind, sesuai Tutorial dari Oracle diatas.

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/9.png)

**Tetapkan URI Template untuk mengakses**

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/10.png)

### 2. Handle

Di tahap ini bisa untuk tahap pengetesan terhadap settingan yang kita buat, Jika berhasil maka akan ada data keluaran berupa **JSON**

Query yang digunaka juga seperti query sql, contoh:

```sql
select * from barang where id=1;
```

Maka hasil keluaran berupa **JSON** yang didalamnya ada data di Databae


![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/11.png)

-----------------

# Query Pada RestFull 

Query ini digunakan untuk menghasilkan data yang kita mau dari Database

#### Table Barang

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/q1.png)

#### Table Customer

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/q2.png)

#### Table Pembelian

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/q3.png)

#### Table Penjualan

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/q4.png)

#### Table Supplier

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/q5.png)

-----------------

# Tampilan UI dari Hasil Pengambilan data API

#### Tampilan Barang

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/t1.png)

#### Tampilan Customer

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/t2.png)

#### Tampilan Supplier

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/t3.png)

#### Tampilan Penjualan

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/t4.png)

#### Tampilan Pembelian 

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter/blob/master/assets/t4.png)

-------------------
