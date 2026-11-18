# sample-super-store-business-analysis
Analisis bisnis dataset Sample Superstore (2014-2017): 6 pertanyaan bisnis dijawab dengan Google Sheets (Pivot Table, QUERY) dan dashboard Looker Studio 3 halaman. Temuan utama: yang paling laku belum tentu paling untung.

| [Buka Dashboard Looker Studio](https://datastudio.google.com/reporting/bab61a4c-6302-45ae-9219-67a9c8e5382c) | [Lihat Spreadsheet](https://docs.google.com/spreadsheets/d/1TqJDSmsc-Rd_ykwGQoR-7yScp8fsuTBaYyWGc-kaeFY/edit?usp=sharing) |

## Ringkasan dataset
| Item | Nilai |
| :--- | :---: |
| Periode | Januari 2014 sampai Desember 2017 |
| Baris transaksi | 9994 |
| Kolom | 21 |
| Sumber data | [Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) |

## Pertanyaan bisnis

| # | Pertanyaan | Halaman dashboard |
|---|---|---|
| 1 | Produk apa yang paling sering dibeli, dan apakah menguntungkan? | 1.Produk dan Kategori |
| 2 | Kategori dan sub-kategori mana yang paling banyak dibeli dan paling menguntungkan? | 1.Produk dan Kategori |
| 3 | Dari wilayah mana pembeli terbanyak, dan apakah wilayah itu menguntungkan? | 2.Wilayah dan Diskon |
| 4 | Produk mana yang merugi, dan apakah diskon berkaitan dengan kerugian itu? | 2.Wilayah dan Diskon |
| 5 | Bagaimana tren Sales dan Profit dari waktu ke waktu? | 3.Trend dan Segment |
| 6 | Segmen pelanggan mana yang paling ramai dan paling efisien? | 3.Trend dan Segment |

## Temuan utama

### [Halaman 1: Produk dan kategori](<./1. Produk dan Kategori Terlaris vs Paling Menguntungkan.pdf>)

- 10 produk terlaris menurut jumlah unit menyumbang 2,7% dari seluruh unit, tetapi hanya 0,7% dari Sales dan 0,9% dari Profit.
- Satu dari 10 produk terlaris merugi: KI Adjustable-Height Table (74 unit, margin -5,46%).
- Office Supplies paling banyak dibeli (60,5% unit, 22.906 unit), tetapi margin tertinggi ada di Technology (17,40%), disusul Office Supplies (17,04%). Furniture hanya 2,49%.
- Sub-kategori dengan margin terbesar: Labels (44,42%), Paper (43,39%), dan Envelopes (42,27%). Tables (-8,56%), Bookcases (-3,02%), dan Supplies (-2,55%) merugi.

### [Halaman 2: Wilayah dan diskon](<./2. Wilayah dan Diskon Ramai Belum Tentu Untung.pdf>)

- California punya pelanggan terbanyak (577). Wyoming paling sedikit (1).
- Dari 10 state dengan pelanggan terbanyak, 6 merugi: Texas, Pennsylvania, Illinois, Ohio, Florida, dan North Carolina, dengan margin dari -3,80% sampai -21,69%. California (16,69%) dan New York (23,82%) ramai dan menguntungkan.
- Sepuluh kombinasi produk dan state dengan kerugian terbesar semuanya memakai diskon 40% sampai 80%. Contoh terbesar: Cubify CubeX 3D Printer di Ohio, diskon 70%, profit -$9.239,97.

### [Halaman 3: Waktu dan segmen](<./3. Trend dan Segment Ramai dan efisien tidak berjalan lurus.pdf>)

- Penjualan naik di bulan Maret, September, dan November pada setiap tahun, dan kuartal 4 menyumbang 38,2% dari total Sales.
- Profit bergerak naik-turun tiap bulan, tetapi total profit tahunan terus naik: $49,5 ribu (2014), $61,6 ribu (2015), $81,8 ribu (2016), $93,4 ribu (2017).
- Consumer punya order terbanyak (2.586 order, 51,6%) dengan margin 11,55%. Home Office punya order paling sedikit (909) tetapi margin tertinggi (14,03%) dan rata-rata nilai order terbesar ($472,67, dibanding Corporate $466,41 dan Consumer $449,11).

## Cara kerja analisis

```
DataAsli  ->  DataBersih  ->  Pivot Table / QUERY / SUMIF  ->  Looker Studio
```

| Sheet | Isi |
|---|---|
| `Objektif` | Enam pertanyaan bisnis, metrik, metode, prioritas, dan status pengerjaan |
| `DataAsli` | Data mentah Sample Superstore |
| `DataBersih` | Salinan `DataAsli` yang dipakai untuk semua analisis dan sudah dibersihkan |
| `PivotObjektif1` | Pivot sub-kategori dan produk (unit, Sales, Profit, order unik) dan `QUERY` 10 produk terlaris menurut unit |
| `Objektif2` | Sales, Profit, dan margin per kategori dan sub-kategori (rumus `SUMIF`) |
| `PivotObjektif2` | Total unit per kategori, dan rinciannya untuk sub-kategori Technology |
| `PivotObjektif3` | Pelanggan unik, Sales, dan margin per region, state, dan kota |
| `Objektif4` | Produk diurutkan dari total profit terendah beserta total unit dan rata-rata diskon (`QUERY`), plus hitungan baris berdiskon 30% ke atas |
| `PivotObjektif5` | Sales, Profit, dan margin per bulan (48 bulan) |
| `PivotObjektif6` | Order, pelanggan, Sales, Profit, dan margin per segmen |

## Validasi dan kualitas data

- Kolom Profit: 9.994 sel, semuanya berupa angka, tanpa sel kosong atau teks.
- Row ID unik di semua 9.994 baris, dan tidak ada Order ID dengan spasi atau huruf berbeda.
- Angka kunci di dashboard dicocokkan ulang terhadap `DataBersih`: margin kategori, jumlah pelanggan per state, profit tahunan, dan nilai per segmen.

## Kontak

Bilal | [LinkedIn](https://www.linkedin.com/in/bilal-al-kindi-work-4-life/) | [Email](mailto:bilalalkindi22@gmail.com)
