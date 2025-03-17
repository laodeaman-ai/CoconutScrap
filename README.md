# Coconut Data Processing

## Deskripsi
Modul ini digunakan untuk mengunduh, mengekstrak, membersihkan, dan memfilter data dari Coconut Database. Data yang diolah berupa file CSV yang berisi informasi tentang senyawa alami, termasuk *SMILES*, *IUPAC name*, dan organisme terkait.

## Fitur Utama
- **Mengunduh file ZIP** dari URL yang diberikan.
- **Mengekstrak file CSV** dari dalam file ZIP.
- **Membersihkan data**, dengan memilih kolom yang relevan dan menghapus baris yang memiliki nilai kosong.
- **Memfilter data** berdasarkan daftar organisme yang diinginkan.

## Instalasi
Pastikan Anda telah menginstal dependensi berikut sebelum menjalankan skrip:

```bash
pip install requests pandas
```

## Penggunaan

### 1. Mengunduh dan Mengekstrak File
Gunakan fungsi `download_file(url, filename)` untuk mengunduh file ZIP dari sumber Coconut Database, lalu ekstrak file CSV dengan `extract_zip(zip_file, csv_file_name)`. Contoh:

```python
coconut_url = 'https://coconut.s3.uni-jena.de/prod/downloads/2024-10/coconut_complete-10-2024.csv.zip'
zip_file_name = 'data_coconut.csv.zip'
csv_file_name = 'data_coconut.csv'

download_file(coconut_url, zip_file_name)
extract_zip(zip_file_name, csv_file_name)
```

### 2. Membersihkan Data
Gunakan fungsi `clean_data(csv_file)` untuk menyaring hanya kolom yang diperlukan dan menghapus baris dengan nilai kosong.

```python
df_cleaned = clean_data(csv_file_name)
```

File hasil pembersihan akan disimpan sebagai `data_coconut_cleaned.csv`.

### 3. Memfilter Data Berdasarkan Organisme
Gunakan fungsi `coconut(df, list_organism)` untuk mendapatkan data berdasarkan organisme tertentu.

```python
list_organism = ['Escherichia coli', 'Homo sapiens']
coconut(df_cleaned, list_organism)
```

File hasil penyaringan akan disimpan sebagai `data_coconut_filtered.csv`.

## Struktur File Output
- `data_coconut_cleaned.csv` : Data yang telah difilter berdasarkan kolom yang relevan.
- `data_coconut_filtered.csv` : Data yang telah difilter berdasarkan daftar organisme tertentu.

## Catatan
- Pastikan koneksi internet stabil saat mengunduh file.
- File yang diekstrak harus mengandung setidaknya satu file CSV, jika tidak, akan terjadi kesalahan.

## Lisensi
Proyek ini dirilis di bawah lisensi MIT.

