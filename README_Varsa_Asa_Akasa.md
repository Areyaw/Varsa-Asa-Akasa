# Varsa Asa: Akasa — Multiplayer Edition

Versi ini melanjutkan prototype RIFT COLOSSEUM dengan nama baru **Varsa Asa: Akasa** dan menambahkan karakter playable kedua, **Zey**.

## Karakter playable

- **Areyaw — Fighter seimbang**: HP 100, ATK 14, AGI 12, DEF 3. Memakai dua set skill API dan DAUN.
- **Zey — Mage**: HP 85, ATK 18, AGI 11, DEF 2. Memakai dua set sihir ARCANA dan VOID dengan skill seperti Arcane Bolt, Mana Burst, Hex Chain, Moon Shard, dan ultimate Astral Cataclysm / Eclipse Tempest.

Untuk berganti karakter, buka menu **Karakter** saat berada di eksplorasi, lalu tekan tombol **Ganti ke Zey / Ganti ke Areyaw**. Level, XP, dan poin stat tetap dibawa saat berganti; statistik dasar dan skill mengikuti karakter yang dipilih. Sprite Zey menggunakan gambar yang diberikan.

## Multiplayer

Lapisan multiplayer Firebase tetap tersedia:
- Buat room dan bagikan kode enam karakter.
- Pemain kedua masuk menggunakan kode tersebut.
- Kedua pemain memilih dua skill dan satu pertahanan per ronde.
- Karakter yang dipilih beserta statistiknya dibawa ke room. Pilihan skill Zey juga dikirim sebagai data skill agar lawan dapat memprosesnya.

## Konfigurasi Firebase

Multiplayer belum dapat tersambung sampai konfigurasi Firebase milikmu dimasukkan.

1. Buat project di Firebase Console.
2. Tambahkan aplikasi Web dan salin konfigurasi Web App.
3. Aktifkan **Authentication → Anonymous**.
4. Buat **Realtime Database**.
5. Ganti nilai placeholder di bagian `MP_FIREBASE_CONFIG` pada HTML:
   - `apiKey`
   - `authDomain`
   - `databaseURL`
   - `projectId`
   - `appId`
6. Terapkan rules dari `Varsa_Asa_Akasa_database.rules.json` untuk pengujian.
7. Hosting file HTML melalui HTTPS (misalnya GitHub Pages).

> **Catatan keamanan:** rules contoh masih mengizinkan semua pengguna yang sudah login untuk membaca/menulis data room. Itu hanya cocok untuk pengujian. Untuk rilis publik, validasi giliran, damage, dan hasil duel sebaiknya dipindahkan ke backend tepercaya/Cloud Functions dan rules diperketat.

## Batasan prototype

- Belum diuji dengan dua perangkat yang benar-benar terhubung ke Firebase karena konfigurasi Firebase belum tersedia.
- Multiplayer membutuhkan internet. Hotspot tanpa koneksi internet tidak cukup.
- Belum ada reconnect otomatis setelah refresh, matchmaking, timeout pemain, pembersihan room otomatis, atau anti-cheat server-side.
- Dalam duel online, karakter lawan masih memakai representasi visual lawan generik pada arena; karakter pilihan tetap memengaruhi statistik dan skill.

## File

- `Varsa_Asa_Akasa_Multiplayer.html` — game utama.
- `Varsa_Asa_Akasa_database.rules.json` — rules Firebase untuk testing.
