<h2 align=center>Instalasi Privasea Privanetix Node menggunakan windows 10/11 ( tanpa vps )</h2>

## Instalasi Awal
- Install [Docker Desktop](https://docs.docker.com/desktop/setup/install/windows-install/) dan [Ubuntu terminal](https://apps.microsoft.com/detail/9pdxgncfsczv?rtc=1&hl=id-ID&gl=ID)
- Buka Ubuntu terminal, lalu ketik kode berikut:
```
sudo docker pull privasea/acceleration-node-beta:latest
```
- Masuk sebagai root user, lalu ketik kode berikut:
```
sudo su
```
- Buat direktori dan navigasi ke direktori tersebut
```
mkdir -p ~/privasea/config && cd ~/privasea
```
- Ambil keystore file dengan membuat passowrd kunci ( simpan password untuk menjalankan node )
```
sudo docker run -it -v "/privasea/config:/app/config"  \
privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
- Simpan alamat node yang nanti akan digunakan pada dashboard privasea, contoh:
```
node address: 0xf07c3eF23ae7BEb8CD8bA5fF546E35Fd4b332B34
```
## Dashboard Privasea
- Buka [Dashboard Privasea](https://deepsea-beta.privasea.ai/privanetixNode), lalu hubungkan wallet
- Tambahkan node baru dengan membuat nama, komisi, dan masukan alamat node
- Konfirmasi transaksi di wallet dengan membayar fee Arbitrum Sepolia

## Intalasi Akhir
- Untuk menjalankan node, ketik kode berikut:
```
cd /privasea/
sudo docker run  -d   -v "/privasea/config:/app/config" \
-e KEYSTORE_PASSWORD=123456 \
privasea/acceleration-node-beta:latest
```
Ubah password "123456" di KEYSTORE_PASSWORD=123456 sesuai dengan password kunci yang tadi sudah dibuat
- Untuk menhentikan node, ketik kode berikut:
```
sudo docker ps -q --filter "ancestor=privasea/acceleration-node-beta:latest" | xargs --no-run-if-empty docker stop
```
