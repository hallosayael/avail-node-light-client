
<p align="center">
  <img width="auto" height="auto" src="https://miro.medium.com/v2/resize:fit:1400/0*KCb_CCSoSeis6uy2.jpeg">
</p>

# AVAIL NODE (LIGHT CLIENT)

## 1. Membuat wallet

Kamu bisa membuat wallet di:

* SubWallet
* Polkadot.js
* Talisman

Faucet: https://faucet.avail.tools/

Register: https://lightclient.availproject.org/
* Untuk Challenges no. 4 Complete Light-client Lift-Off challenge, harus jalankan dulu node nya (lanjut ke step run node dulu)

## 2. Spesifiksi Minimal

Berikut adalah persyaratan **minimum** untuk menjalankan node AVAIL:

 -  **CPU**     : 2 core
 -  **RAM**     : Memori 4GB
 -  **STORAGE** : 200GB

## Instal Otomatis

```
apt update && apt upgrade -y
```

Biarkan Instalisasi Selesai, Agak Lama


```
apt install -y build-essential
```
```
apt install -y curl
```

## Instal Screen

```
sudo apt install screen
```

- Membuat screen dengan nama avail 

```
screen -Rd avail
```

## Run node

```
curl -sL1 avail.sh | bash
```

- Save Address wallet dan Public key, lalu copy private key ke register yang nomor 4 tadi di atas, kemudian mint nft nya

- Done

- Kamu bisa menggunakan keyboard **CTRL+A+D** untuk keluar dari screen nya tanpa membuat node kamu berhenti

---------------------------------------------------------------------------------------------------------------
## AUTO CONNECT

- Ketika sudah membuat screen, lanjutkan dengan command dibawah ini agar re-run / auto connect ketika ada kegagalan rpc
```
sudo tee /etc/systemd/system/avail.service > /dev/null <<EOF
[Unit]
Description=avail Daemon
After=network-online.target
[Service]
User=$USER
ExecStart=/root/.avail/bin/avail-light --config /root/.avail/config/config.yml --app-id 0 --identity /root/.avail/identity/identity.toml --network goldberg
Restart=always
RestartSec=3
LimitNOFILE=65535
[Install]
WantedBy=multi-user.target
EOF
```
```
sudo systemctl enable avail
```
```
sudo systemctl start avail
```
```
sudo systemctl status avail
```
## Tekan dengan keyboard CTRL+C, lalu copas command dibawah ini
```
journalctl -f -u avail
```
## DONE
- Silahkan tekan CTRL+A+D, untuk keluar dari screen (program tetap berjalan)
---------------------------------------------------------------------------------------------------------------

## Melihat daftar screen yang kita punya
```
screen -ls
```

## Membuka log screen
```
screen -r <namascreen>
```

## Remove screen
```
Screen -X -S <namascreen> kill
```

## Cek Latest Block
```
curl "http://localhost:7000/v1/latest_block"
```

## Health Check
```
curl -I "localhost:7000/health"
```
