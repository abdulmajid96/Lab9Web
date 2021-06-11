# Praktikum 9: PHP Modular
# Mata Kuliah Pemrograman WEB
```
Nama  : Abdul Majid
NIM   : 311810693
Kelas : TI.19.C.1
Universitas Pelita Bangsa
```
## Langkah Praktikum
Buat file baru dengan nama header.php
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/stylesheet" media="screen" />
</head>
<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="about.php">Tentang</a>
            <a href="kontak.php">Kontak</a>
        </nav>
```
Buat file baru dengan nama footer.php
```php
        <footer>
            <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html
```
Buat file baru dengan nama home.php
```php
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman Home</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
```
![1](https://github.com/abdulmajid96/Lab9Web/blob/main/SS/1.PNG)

Buat file baru dengan nama about.php
```php
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman About</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
```
![2](https://github.com/abdulmajid96/Lab9Web/blob/main/SS/2.PNG)

## Pertanyaan dan Tugas
Implementasikan konsep modularisasi pada kode program praktikum 8 tentang
database, sehingga setiap halamannya memiliki template tampilan yang sama.

## Jawab
Buat file baru dengan nama header.php
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<body>
```
Buat file baru dengan nama footer.php
```php
        <footer>
            <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html
```
Memanggil modul di halaman index.php
```php
<?php
include("koneksi.php");

// query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);

?>
<?php require('header.php'); ?>

    <div class="container">
        <h1>Data Barang</h1>
        <a href="tambah.php"><button type="button" style="margin-bottom:1%; margin-top:0%; color: blue;">+ Tambah Barang</button></a>
        <div class="main">
            <table border="1" cellpadding="6" cellspacing="0">
                <tr>
                    <th>Gambar</th>
                    <th>Nama Barang</th>
                    <th>Katagori</th>
                    <th>Harga Jual</th>
                    <th>Harga Beli</th>
                    <th>Stok</th>
                    <th>Aksi</th>
                </tr>
                <?php if($result): ?>
                <?php while($row = mysqli_fetch_array($result)): ?>
                <tr>
                    <td><img src="gambar/<?= $row['gambar'];?>" alt="<?=
                    $row['nama'];?>"></td>
                    <td><?= $row['nama'];?></td>
                    <td><?= $row['kategori'];?></td>
                    <td><?= $row['harga_beli'];?></td>
                    <td><?= $row['harga_jual'];?></td>
                    <td><?= $row['stok'];?></td>
                    <td><a href="ubah.php?id=<?php echo $row['id_barang']?>"><button type="button" style="color: green;" title="Edit">Ubah</button></a>
                        <a href="hapus.php?id=<?php echo $row['id_barang']; ?>" onclick="deleted()"><button type="button" style="color: red;" title="Delete">Hapus</button></a></td>
                </tr>
                <?php endwhile; else: ?>
                <tr>
                    <td colspan="7">Belum ada data</td>
                </tr>
                <?php endif; ?>
            </table>
        </div>
    </div>
    
<?php require('footer.php'); ?>
```
![3](https://github.com/abdulmajid96/Lab9Web/blob/main/SS/3.PNG)