# EMUPINDAHSERVER
# Transfer Folder Antar Server Debian dengan rsync

Panduan ini menjelaskan langkah-langkah untuk memindahkan folder dari satu server Debian ke server Debian lain menggunakan `rsync` melalui SSH. Contoh ini menggunakan dua server:
- **Server Sumber**: IP `170.64.165.72`, folder `/var/www/html/`
- **Server Tujuan**: IP `167.71.39.118`, folder `/var/www/html/`

Panduan ini dimulai dari asumsi bahwa kedua server adalah instalasi Debian baru tanpa konfigurasi sebelumnya.

---

## Prasyarat
- Dua server Debian (baru diinstal).
- Akses root atau pengguna dengan hak sudo di kedua server.
- Koneksi jaringan antar kedua server (bisa LAN atau internet).

---

## Langkah-langkah

### 1. Instalasi Dasar di Kedua Server
```bash
sudo apt update && sudo apt install rsync

```
### 2. Instalasi di server tujuan
```bash 
sudo apt install apache2 -y

```
### 3. Perintah di Server Sumber (Sesuaikan IP dan Letak Folder)
Perintah berikut ini akan menimpa file di server tujuan jika nama filenya sama 
```bash
rsync -avz --progress --delete /var/www/html/ root@167.71.39.118:/var/www/html/

```
Perintah Berikut ini akan menampilkan apa yang akan ditransfer tanpa benar-benar melakukannya. --dry-run
```bash 
rsync -avz --dry-run /var/www/html/ root@167.71.39.118:/var/www/html/

```
Perintah Berikut ini akan menghapus file di tujuan yang tidak ada di sumber. --delete (Sinkronisasi Penuh)
```bash 
rsync -avz --progress --delete /var/www/html/ root@167.71.39.118:/var/www/html/

```
## Atau langsung main download pakai SCP untuk memindahkan data 1 Folder misalkan
```bash
scp -r root@server_asal:/root/ess/videos /root/StreamHib/

```
## Lisensi
Dokumentasi ini bebas digunakan di bawah lisensi MIT.
