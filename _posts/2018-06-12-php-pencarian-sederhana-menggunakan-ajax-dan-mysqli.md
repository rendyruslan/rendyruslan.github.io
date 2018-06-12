---
title:  "PHP - Pencarian Sederhana Menggunakan Ajax dan MySQLi"
last_modified_at: 2018-05-20T16:01:04-04:00
categories: 
  - Jekyll
tags:
  - update
toc: true
toc_label: "Getting Started"
---

Dalam tutorial ini kita akan membuat Pencarian Sederhana Menggunakan Ajax & MySQLi menggunakan PHP.

PHP adalah bahasa skrip sisi server yang dirancang terutama untuk pengembangan web. Dengan menggunakan PHP, Anda dapat membiarkan pengguna Anda langsung berinteraksi dengan skrip dan dengan mudah mempelajari sintaksnya. Ajax adalah script sisi klien yang berkomunikasi ke dan dari server / database tanpa perlu postback atau penyegaran halaman lengkap. Ini sebagian besar digunakan oleh seorang pengkode baru untuk lingkungan yang ramah penggunanya. Jadi, mari kita lakukan pengkodean.

## Sebelum kita mulai:
Pertama Anda harus mengunduh & menginstal XAMPP atau server lokal apa pun yang menjalankan skrip PHP. Berikut tautan untuk server XAMPP [`https://www.apachefriends.org/index.html`](https://www.apachefriends.org/index.html).

Dan ini [`https://jquery.com/`](https://jquery.com/) adalah tautan untuk jquery yang saya gunakan dalam tutorial ini .

Terakhir, ini adalah tautan untuk bootstrap yang saya gunakan untuk desain layout ['https://getbootstrap.com/'] (https://getbootstrap.com/).

## Membuat Database
Buka database web server Anda kemudian buat nama database di dalamnya 'db_search', setelah itu klik Import kemudian cari file database di dalam folder aplikasi kemudian klik ok.

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/pict/php-simple-search-using-ajax-mysqli_creating-database.png" alt="Membuat Database">
</figure> 

## Menciptakan koneksi database
Buka segala jenis editor teks Anda (notepad ++, dll.). Kemudian cukup salin / tempelkan kode di bawah lalu beri nama 'conn.php'.

{% highlight javascript linenos %}
<?php
	$conn = new mysqli('localhost', 'root', '', 'db_search');
 
	if(!$conn){
		die("Error: Can't connect to the database!");
	}
?>
{% endhighlight %}

## Menciptakan Tampilan Antarmuka
Di sinilah kita akan menciptakan penampilan aplikasi. Untuk membuat ini cukup salin dan tulis blok kode ini di dalam editor teks, lalu simpan sebagai 'index.php'.

{% highlight javascript linenos %}
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" name="viewport" content="width=device-width, initial-scale=1" />
		<link rel="stylesheet" type="text/css" href="css/bootstrap.css"/>
	</head>
<body>
	<nav class="navbar navbar-default">
		<div class="container-fluid">
			<a class="navbar-brand" href="<a href="https://sourcecodester.com">Sourcecodester</a>
" rel="nofollow">https://sourcecodester.com">Sourcecodester</a>
</a>		</div>
	</nav>
	<div class="col-md-3"></div>
	<div class="col-md-6 well">
		<h3 class="text-primary">PHP - Simple Search Using Ajax/MySQLi</h3>
		<hr style="border-top:1px dotted #ccc;"/>
		<form method="POST">
			<div class="form-inline">
				<input type="text" id="search_data" class="form-control" placeholder="Search here..."/>
				<button type="button" id="search" class="btn btn-primary"><span class="glyphicon glyphicon-search"></span> Search</button>
				<button type="button" id="refresh" class="btn btn-success"><span class="glyphicon glyphicon-refresh"></span></button>
			</div>
		</form>
		<br /><br />
		<table class="table table-bordered">
			<thead class="alert-success">
				<tr>
					<th>Firstname</th>
					<th>Lastname</th>
					<th>Address</th>
					<th>Gender</th>
					<th>Age</th>
				</tr>
			</thead>
			<tbody class="alert-warning" id="data"></tbody>
		</table>
	</div>
</body>
<script src="js/jquery-3.2.1.min.js"></script>
<script type="text/javascript">
	$(document).ready(function(){
		DisplayData();
 
		$('#search').on('click', function(){
			if($('#search_data').val() == ""){
				alert("Please enter something first!");
			}else{
				var search = $('#search_data').val();
				var loader = $('<tr ><td colspan = "5"><center>Searching....</center></td></tr>');
				$('#data').empty();
				loader.appendTo('#data');
 
				setTimeout(function(){
					loader.remove();
					$.ajax({
						url: 'search.php',
						type: 'POST',
						data: {
							search: search
						},
						success: function(data){
							$('#data').html(data);
						}
					});
 
				}, 3000);	
			}
		});
 
		$('#refresh').on('click', function(){
			DisplayData();
		});
 
 
		function DisplayData(){
			$.ajax({
				url: 'data.php',
				type: 'POST',
				data: {
					res: 1
				},
				success: function(data){
					$('#data').html(data);
				}
			});
		}
	});
</script>
</html>
{% endhighlight %}

## Membuat fungsi PHP
Kode ini berisi fungsi utama aplikasi. Kode ini akan mengirim permintaan ke server database dengan menggunakan ajax, kemudian mengembalikan string yang telah dicari melalui permintaan php. Untuk melakukan copy itu dan tulis blok kode ini di dalam editor teks Anda, lalu simpan seperti yang ditunjukkan di bawah ini.

'data.php'
{% highlight javascript linenos %}
<?php
	require_once 'conn.php';
 
	if(ISSET($_POST['res'])){
		$query = $conn->query("SELECT * FROM `member` ORDER BY `lastname` ASC");
		while($fetch = $query->fetch_array()){
			echo "
				<tr>
					<td>".$fetch['firstname']."</td>
					<td>".$fetch['lastname']."</td>
					<td>".$fetch['address']."</td>
					<td>".$fetch['gender']."</td>
					<td>".$fetch['age']."</td>
				</tr>
			";
		}
	}
?>
{% endhighlight %}

'search.php'
{% highlight javascript linenos %}
<?php
	require_once 'conn.php';
 
	if(ISSET($_POST['search'])){
		$search = $_POST['search'];
		$query = $conn->query("SELECT * FROM `member` WHERE (`lastname` LIKE '%".$search."%') OR (`address` LIKE '%".$search."%') ORDER BY `lastname` ASC");
		$rows = $query->num_rows;
 
		if($rows > 0){
			while($fetch = $query->fetch_array()){
				echo "
					<tr>
						<td>".$fetch['firstname']."</td>
						<td>".$fetch['lastname']."</td>
						<td>".$fetch['address']."</td>
						<td>".$fetch['gender']."</td>
						<td>".$fetch['age']."</td>
					</tr>
				";
			}
		}else{
			echo "
				<tr>
					<td colspan='5'><center>No Search Found!</center></td>
				</tr>
			";
		}
	}
?> 
{% endhighlight %}

## Membuat fungsi Ajax
Di sinilah kode yang menggunakan skrip ajax. Kode ini berisi beberapa fungsi yang perlu mengirim permintaan ke server php. Untuk melakukannya, cukup salin dan tulis blok kode ini di dalam editor teks, lalu simpan sebagai 'script.js' di dalam folder js.

{% highlight javascript linenos %}
$(document).ready(function(){
	DisplayData();
 
	$('#search').on('click', function(){
		if($('#search_data').val() == ""){
			alert("Please enter something first!");
		}else{
			var search = $('#search_data').val();
			var loader = $('<tr ><td colspan = "5"><center>Searching....</center></td></tr>');
			$('#data').empty();
			loader.appendTo('#data');
 
			setTimeout(function(){
				loader.remove();
				$.ajax({
					url: 'search.php',
					type: 'POST',
					data: {
						search: search
					},
					success: function(data){
						$('#data').html(data);
					}
				});
 
			}, 3000);	
		}
	});
 
	$('#refresh').on('click', function(){
		DisplayData();
	});
 
 
	function DisplayData(){
		$.ajax({
			url: 'data.php',
			type: 'POST',
			data: {
				res: 1
			},
			success: function(data){
				$('#data').html(data);
			}
		});
	}
});
{% endhighlight %}

Sekarang anda berhasil membuat Pencarian Sederhana Menggunakan Ajax & MySQLi menggunakan PHP. Saya harap tutorial sederhana ini membantu Anda untuk apa yang Anda cari. Untuk lebih banyak pembaruan dan tutorial, silakan kunjungi situs ini. Happy Coding !!!

