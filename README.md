# 生活会話 — Seikatsu Kaiwa

Kartu latihan **keigo & percakapan sehari-hari di Jepang** — yang benar-benar
dipakai di konbini, kereta, klinik, kantor kota, asrama, dan tempat kerja magang.
Saudara dari 敬語会話 (Keigo-Kaiwa) dengan konsep visual yang sama:
kertas *washi*, tinta *sumi*, stempel *hanko* (朱).

**469 kartu · 18 kategori · 292 kalimat untuk diucapkan (話) · 177 kalimat yang akan kamu dengar (聞)**

## Menjalankan

Tidak perlu server — buka `index.html` di browser (klik dua kali), atau publikasikan
lewat GitHub Pages. Data dimuat lewat `<script>`, jadi tidak ada masalah CORS di `file://`.

## Fitur

- **聞く / 話す** — filter kalimat yang akan kamu *dengar* (staf, petugas, atasan,
  pengumuman) vs yang kamu *ucapkan*. Kartu 聞 dilengkapi **contoh jawaban (返事)**.
- **Suara** (tombol 音声 / `A`) memakai suara Jepang bawaan browser; opsi *Suara lambat*.
  Terbaik di Chrome (Google 日本語) atau Edge (Microsoft Nanami).
- **Mode dengar** — teks disembunyikan, suara diputar otomatis; tebak artinya lalu balik kartu.
- **Pencarian** kanji / kana / romaji / bahasa Indonesia (`/` untuk fokus, `Esc` untuk hapus).
- Furigana di semua kanji (termasuk catatan), bisa disembunyikan untuk uji-diri. Toggle romaji.
- 18 kategori + chip **注意 (Jebakan)** berisi kesalahan umum orang asing
  (「大丈夫です」 = tidak, 「ちょっと…」 = tidak bisa, rekening dijual = kriminal, dll).
- Tandai **覚えた** (dikuasai) + **未習のみ** untuk menyembunyikan kartu yang sudah hafal.
  Progres & preferensi tersimpan di `localStorage` (key `kaiwa.*`, tidak bentrok dengan 敬語会話).
- Hitung mundur keberangkatan (ubah `DEPARTURE` di `script.js`).
- 3 tema: 和紙 · 藍 · 抹茶. Responsif (chip kategori bisa digeser di HP).
- Pintasan: `Spasi/Enter` balik · `←/→` navigasi · `A` suara · `L` kuasai · `H` 未習のみ · `S` acak · `/` cari.

## Kategori

| Chip | Isi | | Chip | Isi |
|---|---|---|---|---|
| 基本 | Frasa bertahan hidup | | 銀行 | Bank, ATM, kirim uang |
| 挨拶 | Salam & perkenalan | | 郵便 | Pos, paket, kiriman ulang |
| 職場 | Tempat kerja magang | | 携帯 | Kontrak HP, SIM, internet |
| コンビニ | Minimarket | | 住まい | Asrama, tetangga, sampah |
| 買い物 | Supermarket, toko, 100均 | | 美容院 | Potong rambut |
| 飲食店 | Restoran, ramen, izakaya | | 電話 | Telepon & reservasi |
| 電車 | Kereta & pengumuman stasiun | | 緊急 | Darurat, polisi, gempa |
| 交通 | Tanya jalan, bus, taksi, sepeda | | 交流 | Pergaulan, nomikai, menolak halus |
| 病院 | Klinik, dokter gigi, apotek | | 注意 | (semua kartu jebakan) |
| 役所 | Kantor kota, imigrasi, pensiun | | | |

## Struktur berkas

| Berkas | Peran |
|---|---|
| `index.html` | Markup + urutan pemuatan data |
| `style.css` | Token warna, tema, kartu 3D, ruby furigana |
| `script.js` | Filter, pencarian, suara, progres, tema, papan ketik |
| `data/init.js` | `KAIWA_DATA`, daftar kategori `KAIWA_CATS`, fungsi `addCards()` |
| `data/<kategori>.js` | Materi per kategori (satu-satunya tempat mengedit isi) |
| `tools/validate-data.js` | Pemeriksa data (furigana, romaji, duplikat, field wajib) |

## Menambah materi

Tambahkan objek ke berkas kategori yang sesuai di `data/`:

```js
{
  jp:     "お{弁当:べんとう}、{温:あたた}めますか",  // furigana: {漢字:よみ}
  romaji: "obentou, atatamemasu ka",             // Hepburn, ou/ii, を = wo
  id:     "Bentonya mau dihangatkan?",
  type:   "丁寧語",   // 尊敬語 | 謙譲語 | 丁寧語 | 定型 | 普通 | 注意
  role:   "聞",       // 聞 = kamu dengar · 話 = kamu ucapkan
  reply:  "はい、お{願:ねが}いします",               // opsional, contoh jawaban
  note:   "Catatan pemakaian (boleh pakai furigana)"
}
```

Bacaan kana (`yomi`) dibuat otomatis dari furigana. Lalu jalankan:

```bash
node tools/validate-data.js
```

Validator menolak kanji tanpa furigana, kurung `{}` yang rusak, romaji yang tidak cocok
dengan bacaan kana, dan kartu ganda. Kategori baru: tambahkan ke `KAIWA_CATS`
di `data/init.js`, buat berkas `data/<nama>.js`, lalu daftarkan di `index.html`.

## Catatan isi

- Fokus pada bahasa yang **benar-benar terdengar** di kehidupan nyata: 「温めますか」,
  「袋はご利用ですか」, 「人身事故の影響で…」, 「これ、やっといて」, dialek Kansai, dll.
  Tipe **普通** dipakai untuk bahasa santai yang akan kamu dengar dari senpai/atasan.
- Informasi aturan (tarif pos Okt 2024, kartu asuransi kertas berhenti Des 2024,
  denda sepeda mulai Apr 2026, 育成就労 mulai 2027) ditulis sesuai kondisi saat dibuat
  (Oktober 2026) — cek ulang ke perusahaan/kumiai karena aturan bisa berubah.
- Bacaan furigana sudah dicek silang dengan kamus morfologi (kuromoji/IPADIC).
