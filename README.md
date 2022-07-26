###### Nama : Esa Alliant.
###### Kelas : RPL 1.
###### No Absen : 25

# Modul 1 

Soal Nomor 1
Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing

```
composer create-project laravel/laravel penjualan
```


# Modul 2
Soal nomor 1 
Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam
modul ini.

Langkah pertama 
```
php artisan make:migration create_produk_table>
```

Langkah kedua
isikan kode dibawah ini kedalam file yang dibuat 
```
  <?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
    ```
    
    Langkah ke 3
    Untuk mengeksekusinya, jalankan perintah berikut 
    ```
    php artisan migrate
    ```
    Isi kode di bawah ke dalam file
    ```
    <?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Kategori extends Model
{
    use HasFactory;

    protected $table = 'kategori';
}
```
soal ke 2

Langkah ke 1.
Pembuatan seeder Untuk membuat seeder gunakan artisan berikut pada cmd visual studio code.
```
php artisan make:seeder kategoriTableSeeder
 ```
 selanjutnya buka file 
 KategoriTableSeeder yang telah dibuat dan di tambahkan script pada method run().
 lalu tulis code berikut.
 ```
 <?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table ('kategori')->insert(array(
            [
                'nama' => 'Perlengkapan Sekolah'
            ],
            [
                'nama' => 'Komputer'
            ],
            [
                'nama' => 'Sabun'
            ],
            [
                'nama' => 'Accesories'
            ],
            [
                'nama' => 'Attack'
            ]
        ));
    }
}
   ```
   
   langkah ke 2.
   
   buka file bagian data base dan kode isi bagian publicfunction run()
   ```
   &this->call(kategoriTableSeeder::class
   ```
   dengan tujuan untuk memanggil bagian kelas kategoriTableSeeder untuk bekerja pada database seeder
   
   langkah ke 3.
   
   sekarang kita dapat menjalankan perintah artisan pada cmd untuk garis seeder yang telah dibuatdengan perintah sebagai berikut.
   ```
   php artisan db:seed
   ```
    untuk hasil dari seeder yang telah dibuat bukalah localhost/phpmyAdmin pada browser lalu pilih database penjualan dan label produk makahasil nya ada 2 data yang baru yang dihasilkan dari pembuatan seeder itu.
   
