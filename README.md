<div align="center">

# Language Flashcards — EN ↔ DE

**Sıfır bağımlılık, çift tıkla açılan, telefon-uyumlu İngilizce ↔ Almanca cümle ezber kartı.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Dependencies: none](https://img.shields.io/badge/dependencies-0-success)](#tech-stack)
[![Single file](https://img.shields.io/badge/single--file-index.html-orange)](index.html)
[![PWA-ready](https://img.shields.io/badge/mobile-friendly-blueviolet)](#)

[Özellikler](#özellikler) · [Kullanım](#kullanım) · [Veri Modeli](#veri-modeli) · [Deploy](#deploy)

</div>

---

## Özellikler

| | |
|---|---|
| 🔁 **EN ↔ DE her iki yön** | Hedef dili tek tıkla değiştir; "öğrendim" listesi her dil için ayrı tutulur |
| 🎴 **Kart çevirme animasyonu** | Ön yüzde hedef dil, arka yüzde çeviri |
| 🏷️ **Etiketler** | Her cümleye `food`, `study`, `navigation`, `admin` gibi etiketler — kategori bazlı çalışma için |
| ✅ **Öğrenildi izleme** | Doğru bildiğin kartlar `localStorage`'a yazılır; "Öğrenilenleri gizle" filtresi ile elini tut |
| 🌓 **Tema + ölçek** | Karanlık / aydınlık / sistem ile uyumlu; ekran ölçeği slider'ı görme/dokunma erişebilirliği için (`--scale`) |
| 📱 **Telefon-uyumlu** | 48 px minimum dokunma hedefi, responsive 1-kolon mizanpaj <1024 px |
| ⚡ **Tek dosya, sıfır bağımlılık** | `index.html` — framework yok, build yok, CDN yok |

## Kullanım

### Yerel kullanım (önerilir)

`index.html` dosyasına çift tıklayın. Hepsi bu. Tarayıcı offline da çalışır — bağımlılık yok.

### Yerel sunucu (mobil testte daha iyi)

Aynı Wi-Fi'deki telefondan açmak isterseniz basit bir HTTP sunucusu:

```bash
# Python 3
python -m http.server 8080
# tarayıcı: http://localhost:8080

# Node
npx serve .
```

## Veri modeli

Tüm cümleler `index.html` içinde `PHRASES` adlı sabitte tutulur:

```js
const PHRASES = [
  { en: "Where is the pharmacy?", de: "Wo ist die Apotheke?", tags: ['health', 'city'] },
  // …
];
```

Yeni cümle eklemek için diziye satır eklemek yeterli — string anahtarları korumaya gerek yok, indeks sırayla kullanılır.

`localStorage` anahtarları:

| Anahtar | Ne tutar |
|---|---|
| `learned-en` | İngilizce hedefte öğrenilen cümlelerin `PHRASES` indeks listesi |
| `learned-de` | Almanca hedefte öğrenilen cümlelerin `PHRASES` indeks listesi |
| `fc-theme` | Tema seçimi (`auto` / `dark` / `light`) |
| `fc-scale` | UI ölçeği (0.85 – 1.4) |

## Tech stack

- **HTML5** — semantik tek sayfa
- **CSS3** — CSS variables ile tema + scale; radial gradient + glassmorphism panel
- **Vanilla JavaScript** — sınıf yok, framework yok, derleyici yok
- **`localStorage`** — kalıcılık katmanı

Toplam ~537 satır. Hiçbir CDN yüklemiyor; tamamen offline çalışır.

## Deploy

### Vercel / Netlify

Tek dosya statik site — repoyu bağlayın, build komutu boş, output `.` (kök).

### GitHub Pages

`main` branch'i Settings → Pages'den serve edin. `index.html` zaten kökte.

### USB / OneDrive / mail eki

`index.html` dosyasını kopyalayın, çift tıklayın. Bunun için tasarlandı.

## Proje yapısı

```
en-de-flashcards-app/
├── index.html       # Tek dosya — HTML + CSS + JS + cümle listesi
├── LICENSE          # MIT
├── README.md
└── .gitignore
```

## Sınırlamalar (dürüstçe)

- Cümle listesi `index.html` içinde gömülü — yeni cümle eklemek için kodu açmak gerekiyor (öneri: ileride `phrases.json` ayrı dosya)
- TTS (yüksek sesle okuma) yok — `SpeechSynthesisUtterance` ile eklenebilir, şu an yok
- Spaced-repetition (Anki tarzı) yok — sadece "öğrendim/öğrenmedim" ikili durum

## Yazar

**Uğur Ersöz** — [@ugrersoz](https://github.com/ugrersoz)

## Lisans

**MIT Lisansı**. Tam metin için [LICENSE](LICENSE).
