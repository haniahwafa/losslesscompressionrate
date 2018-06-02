Lossless Data Compression Rate
-------------------------------

Sekarang dalam kehidupan sehari-hari kita saling melakukan interaksi berupa pertukaran informasi dengan memanfaatkan teknologi. Kendala yang sering dihadapi dalam pengiriman maupun penyimpanan data yaitu terlalu besarnya kapasitas data sehingga dalam proses pengiriman data menjadi lambat dan membutuhkan storage yang besar untuk penyimpanannya. Oleh karena itu berkembanglah aplikasi-aplikasi kompresi data untuk mengkompress data agar ukurannya menjadi lebih kecil.

Kompresi data adalah sebuah cara untuk memadatkan data sehingga hanya memerlukan ruangan penyimpangan yang lebih kecil sehingga lebih efisien dalam menyimpannya atau mempersingkat waktu pertukaran data tersebut. Dalam pemampatan data atau kompresi data memiliki 2 jenis hasil kompresi yaitu

1.  Kompresi data tanpa kehilangan (lossless data compression)
2.  Kompresi data berkehilangan (lossy data compression)

Pada artikel kali ini kita akan membahas lebih lanjut tentang Kompresi data tanpa kehilangan atau Lossless data compression. Lossless data compression adalah teknik kompresi dimana data hasil kompresi dapat didekompres lagi dan menghasilkan hasil yang tepat sama dengan data sebelum dikompres. Contohnya yaitu ZIP, RAR, GZIP, 7-Zip. Teknik ini digunakan jika dibutuhkan data yang setelah di kompresi harus dapat diekstrak/ didekompres lagi tepat sama. Kadang kala ada data-data yang setelah dikompresi dengan Teknik ini ukurannya menjadi lebih besar atau sama.

# Run-length Encoding (RLE)

Run-length Encoding (RLE) adalah bentuk dari lossless data compression yang sangat sederhana. Algoritma ini menyimpan elemen data yang berurutan dan memiliki nilai yang sama, sebagai sebuah data tunggal yang terdiri dari nilai dan banyaknya. Contohnya, jika string masukkannya adalah “wwwwwaaadexxxxxx” maka algoritma run-length encoding akan mengembalikan “w4a3d1e1x6”. Hasil ini dapat diinterpretasikan sebagai empat buah w, tiga buah a, sebuah d, sebuah x dan enam buah x. Berikut adalah contoh perhitungan dari RLE compression rate dari sebuah citra.
 
## Kasus Pertama

| 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 |

Dalam bentuk aslinya, citra ini akan membutuhkan 49 bits. Jika kemudian kita mengeksekusi algoritma RLE dengan total 4 bit untuk tiap run-nya (1 bit untuk menyimpan nilainya dan 3 bit untuk menyimpan banyaknya). Maka akan memberi hasil sebagai berikut.

 Baris 1 : 07
 Baris 2 : 17
 Baris 3 : 17
 Baris 4 : 17
 Baris 5 : 1403
 Baris 6 : 1403
 Baris 7 : 07

Sehingga setelah dikompresi kita hanya akan membutuhkan 36 bit. Dengan kata lain, pada kasus ini algoritma RLE memiliki compression rate sebesar 49 : 36 atau sekitar 1.36 : 1.
 
## Kasus Kedua

| 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 1 | 1 | 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 1 | 1 | 1 |

Untuk kasus kedua, algoritma RLE akan memberikan hasil sebagai berikut.

 Baris 1 : 021302
 Baris 2 : 130411
 Baris 3 : 0314
 Baris 4 : 0215
 Baris 5 : 1403
 Baris 6 : 1205
 Baris 7 : 0413

Sehingga setelah dikompresi kita hanya membutuhkan 64 bit. Dengan kata lain, pada kasus ini algoritma RLE justru akan membuat ukuran data yang kita butuhkan untuk menyimpan data yang telah di-compress menjadi lebih besar daripada untuk menyimpan data aslinya.
Dari dua contoh kasus di atas, sangat jelas terlihat bahwa algoritma ini tidak cukup baik untuk mengkompresi data secara umum. Algoritma ini akan cocok untuk mengkompresi data yang banyak memiliki nilai yang sama pada elemen data yang berurutan. Namun akan menjadi tidak efektif untuk kasus data yang sebaliknya karena justru akan memberi ukuran data yang sama atau bahkan lebih besar dari ukuran data aslinya.


## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/haniahwafa/losslesscompressionrate/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/haniahwafa/losslesscompressionrate/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
