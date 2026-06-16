# Enchant Database

Website statis buat nampilin database Advanced Enchantments — search, filter by rarity, filter by tipe item. Gak butuh backend, server, atau build step. Tinggal upload ke GitHub, langsung jalan.

## Struktur file

```
index.html        -> halaman utama
css/style.css      -> semua styling
js/data.js          -> data enchant (auto-generate dari excel)
js/app.js           -> logic search & filter
```

## Cara deploy ke GitHub Pages (gratis, gak perlu domain)

1. Bikin repo baru di GitHub (public), misal nama `enchant-db`.
2. Upload semua file & folder di sini (index.html, css/, js/) ke root repo itu. Bisa drag-drop lewat web GitHub, atau lewat git:
   ```
   git init
   git add .
   git commit -m "init enchant db"
   git remote add origin https://github.com/USERNAME/enchant-db.git
   git push -u origin main
   ```
3. Di repo GitHub, masuk ke **Settings > Pages**.
4. Di bagian "Build and deployment", pilih source **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
5. Tunggu 1-2 menit, link nya bakal muncul di atas, formatnya:
   `https://USERNAME.github.io/enchant-db/`

Selesai, websitenya udah live dan bisa diakses siapa aja.

## Cara update data enchant

Edit langsung file `js/data.js`. Formatnya array of object:

```js
{ "no": 1, "name": "Abiding", "desc": "...", "appliesRaw": "Weapons", "tags": ["Weapon"], "rarity": "Legendary", "maxLevel": 1 }
```

- `tags` dipakai buat filter "ITEM", isinya bisa lebih dari satu (misal `["Sword","Axe"]`).
- `rarity` harus salah satu dari: Simple, Unique, Elite, Legendary, Fabled, Ultimate (kalau nambah rarity baru, tambahin juga di `RARITY_ORDER` dan `RARITY_COLOR` pada `js/app.js`).
- `appliesRaw` cuma buat ditampilin di pojok kanan bawah card, gak dipakai buat filter.

Tinggal save file, push ke GitHub, otomatis update — gak perlu rebuild apa-apa.

## Edit tampilan/warna

Semua warna ada di bagian atas `css/style.css` (`:root { ... }`), termasuk warna tiap rarity. Tinggal ganti hex code-nya kalau mau ubah skema warna.
