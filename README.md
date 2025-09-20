# OTT Manager Bot

Bot Telegram untuk menguruskan ID OTT (Over-The-Top) dengan sistem pengesahan dan pengurusan yang mudah.

## 📋 Gambaran Keseluruhan

Bot ini membolehkan admin untuk mencipta, memadam, dan menguruskan ID OTT untuk pengguna. Pengguna boleh menuntut ID OTT mereka melalui pautan yang dijana dan menerima maklumat tentang tarikh tamat tempoh mereka. Bot ini juga menghantar peringatan automatik kepada pengguna sebelum ID mereka tamat tempoh.

## 🚀 Ciri-ciri Utama

- **Pengurusan Admin**: Cipta, padam dan senaraikan ID OTT
- **Sistem Tuntutan**: Pengguna boleh menuntut ID OTT mereka melalui pautan
- **Peringatan Automatik**: Bot menghantar peringatan 1, 3 dan 7 hari sebelum tamat tempoh
- **Statistik**: Lihat statistik penggunaan dan tuntutan
- **Sistem Keselamatan**: Hanya admin yang dibenarkan melakukan operasi pengurusan

## 🛠️ Keperluan Sistem

- Python 3.7+
- Telegram Bot Token (dapatkan dari [@BotFather](https://t.me/BotFather))

## 📦 Pemasangan

1. **Klonkan repositori ini**:
   ```bash
   git clone <url-repositori-anda>
   cd <nama-folder>
   ```

2. **Pasang keperluan**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Konfigurasi bot**:
   - Dapatkan token bot dari [@BotFather](https://t.me/BotFather)
   - Gantikan token dalam fail `bot.py` di baris:
   ```python
   updater = Updater("TOKEN_BOT_ANDA_DI_SINI", use_context=True)
   ```

4. **Konfigurasi admin**:
   - Dalam fail `bot.py`, tambahkan ID Telegram anda dalam senarai `ADMIN_IDS`
   - Tambahkan pemetaan nama pengguna dalam `ADMIN_USERNAMES`

5. **Jalankan bot**:
   ```bash
   python bot.py
   ```

## 📖 Penggunaan

### Untuk Admin

Bot menyediakan menu khas untuk pengguna admin. Setelah memulakan bot dengan `/start`, admin akan melihat menu berikut:

**Perintah Admin:**
- `/create <ott_id> <tempoh>` - Cipta entri OTT baru
  - Contoh: `/create rtm-41806 90days`
- `/delete <ott_id>` - Padam entri OTT
  - Contoh: `/delete rtm-41806`
- `/list` - Senaraikan semua entri OTT
- `/stats` - Papar statistik

### Untuk Pengguna Biasa

Pengguna biasa boleh menuntut ID OTT mereka melalui pautan yang dijana oleh admin. Setelah menuntut, mereka akan menerima maklumat tentang:

- URL OTT
- Had peranti
- Jenis senarai main
- Tarikh tamat tempoh

## 📁 Struktur Projek

```
├── bot.py              # Fail utama bot
├── requirements.txt    # Senarai pakej Python yang diperlukan
├── database/           # Direktori untuk menyimpan data OTT
├── users/              # Direktori untuk menyimpan data pengguna
└── README.md           # Dokumentasi ini
```

## ⚙️ Konfigurasi

### Menambah Admin

Untuk menambah admin baru, edit fail `bot.py`:

```python
# Admin IDs (tambah ID baru di sini)
ADMIN_IDS = ["126354368", "872342168", "ID_BARU"] 

# Admin username mapping
ADMIN_USERNAMES = {
    "126354368": "cikgusuraya",
    "872342168": "NRTHWT",
    "ID_BARU": "USERNAME_BARU"
}
```

### Menyesuaikan Zon Masa

Bot menggunakan zon masa Malaysia (Asia/Kuala_Lumpur). Untuk menukar zon masa:

```python
malaysia_tz = pytz.timezone('Asia/Kuala_Lumpur')  # Tukar kepada zon masa anda
```

## 📊 Statistik

Admin boleh melihat statistik dengan perintah `/stats` yang menunjukkan:
- Jumlah entri OTT
- Jumlah pengguna berdaftar
- Jumlah tuntutan keseluruhan

## 🔒 Keselamatan

- Hanya pengguna dalam senarai `ADMIN_IDS` yang boleh melakukan operasi pengurusan
- Semua data disimpan secara tempatan dalam fail JSON
- Bot token mestilah dirahsiakan dan tidak dikongsi secara awam

## 🤝 Sokongan

Untuk pertanyaan atau bantuan, hubungi admin melalui:

👨‍💼 *Admin Contacts*:
• [@cikgusuraya](https://t.me/cikgusuraya)
• [@NRTHWT](https://t.me/NRTHWT)

## 📄 Lesen

Projek ini adalah perisian sumber terbuka. Sila pastikan pematuhan dengan syarat perkhidmatan Telegram dan undang-undang tempatan semasa penggunaan.