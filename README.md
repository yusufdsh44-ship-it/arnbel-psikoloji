# ARNBEL - Kurumsal Psikoloji Platformu

> 2.080 belediye personelinin psikolojik sagligini tek bir psikologun etkin sekilde takip edebilmesi icin tasarlanmis klinik yonetim sistemi.

## Hizli Baslangic

```bash
# Bagimliliklari yukle
pip install -r requirements.txt

# Uygulamayi baslat
python main.py

# Tarayicida ac
http://localhost:5000/psikoloji/
```

## Ne Yapar?

- **Seans Yonetimi** - 20-30 dk standart protokol, ses kaydi, AI analiz
- **Tarama** - SCL-90 + anket verileri ile risk tespiti
- **Dinamik Triyaj** - Veri ekledikce otomatik guncellenen risk skoru
- **Mudurluk Analizi** - Kurumsal duzey sorun tespiti

## Veri Kaynaklari

| Kaynak | Bazli | Aciklama |
|--------|-------|----------|
| Anket | Mudurluk | Denge puani, ruh sagligi riski, guclu/zayif yonler |
| SCL-90 | Kisi | Semptom tarama (GSI skoru) |
| Seans | Kisi | Klinik gozlemler, MSE, risk puani |
| AI Analiz | Kisi | Transkript bazli supervizyon |

## Sayfalar

| URL | Aciklama |
|-----|----------|
| `/psikoloji/dashboard` | Genel bakis, istatistikler |
| `/psikoloji/triyaj` | Personel listesi, risk siralama |
| `/psikoloji/seans/<id>` | Gorusme kayit sayfasi |
| `/psikoloji/takvim` | Randevu yonetimi |
| `/psikoloji/analiz` | Mudurluk analizleri |

## Triyaj Hesaplama

```
Kisi Triyaji = SCL-90 + Seans Risk + Mudurluk Risk
Mudurluk Triyaji = Anket Denge + Ruh Sagligi + Klinik Ortalamalar
```

Detaylar icin: **`CLAUDE_CONTEXT.md`**

## Teknik

- **Backend:** Flask 3.x + SQLAlchemy
- **Frontend:** Tailwind CSS + Jinja2
- **Veritabani:** SQLite
- **Grafikler:** Chart.js

---

Arnavutkoy Belediyesi - 2026
