untuk melakukan pengambilan data dari file excell pertama kita harus mendownload phpspreadsheet dengan composer

  ```composer require phpoffice/phpspreadsheet```
  
apabila gagal dalam melakukan download library, biasanya extensi php-gd tidak terinstall atau dalam keadaan tidak aktif. untuk mengaktifkannya ada beberapa cara sesuai dengan tipe web server yang kita gunakan

**untuk linux debian/ubuntu**

  ```sudo apt-get update```
  
  ```sudo apt-get install php-gd```
  
setelah itu restart apache2 atau nginx


untuk XAMPP, WAMP, MAMP
  buka file php.ini (biasanya ada di C:\xampp\php\php.ini)
  aktifkan extension=gd dengan menghapus tanda semicolon (;) didepannya
  restart apache

**cara menggunakannya di php**

  <?php
require 'modul-php-excell/vendor/autoload.php';

use PhpOffice\PhpSpreadsheet\IOFactory;
use PhpOffice\PhpSpreadsheet\Spreadsheet;

$filePath = 'rekening-koran.xlsx'; // Ganti dengan jalur file Excel Anda

// Membaca file Excel
$spreadsheet = IOFactory::load($filePath);

// Mendapatkan sheet aktif
$sheet = $spreadsheet->getActiveSheet();

// Mendapatkan data dari sheet
$data = $sheet->toArray();

for($i=1; $i < count($data);$i++){
  echo $data[$i][0]. '    '.$data[$i][1]. '    ' .$data[$i][2];
  echo '<br>'; 
}

**================================================**
