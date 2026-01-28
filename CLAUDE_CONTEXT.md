# ARNBEL Psikoloji Platformu - Claude Context

> **Son Guncelleme:** 28 Ocak 2026
> **Bu dosya Claude'un projeyi her seferinde dogru anlamasi icin tutulur.**

---

## 1. Stratejik Amac

**ARNBEL** - Arnavutkoy Belediyesi Kurumsal Psikolojik Danismanlik Sistemi

> Psikolog belediyenin **"psikolojik fotografini"** cekiyor.
> Amac: Baskan ve IK Muduru'ne **kanit temelli risk analizi** sunmak.

### Makro → Mikro Stratejisi

| Asama | Arac | Kapsam | Cikti |
|-------|------|--------|-------|
| 1. ANKET | Anonim anket | 30 mudurluk | **Kurumsal fotograf** |
| 2. SCL-90 | Semptom tarama | Gorusme oncesi | **Bireysel fotograf** |
| 3. SEANS | Klinik gorusme | 20-30 dk | **Klinik degerlendirme** |
| 4. TRIYAJ | Veri birlestirme | Tum kaynaklar | **Kanit temelli risk raporu** |

### Sunum Hedefi

**Hedef Kitle:**
- Belediye Baskani
- IK Muduru

**Sunum Icerigi:**
- Mudurluk bazli risk haritasi
- Kisi bazli kritik vakalar (anonim)
- Sistemik sorun tespitleri
- Oneri ve mudahale planlari

---

## 2. Proje Tanimi

Kurumsal psikologun **2.080 belediye personelini** Notion benzeri kullanici dostu bir arayuzle takip etmesini saglayan, anket+test+seans verilerini birlestiren klinik yonetim sistemi.

### Gorusme Sistemi

| Ozellik | Aciklama |
|---------|----------|
| Ilk gorusme | **ZORUNLU** - 2.080 kisinin tamami |
| Ikinci gorusme | **GONULLU** - Kisi isterse |
| Siralama | **KARISIK** - Mudurluk sirasina gore degil, musaitlige gore |

### Kullanim Senaryolari
1. **Klinik Gorusme** - 20-30 dk standart protokol, ses kaydi, AI analiz
2. **Tarama** - SCL-90 + anket verileri ile risk tespiti
3. **Analiz** - Kisi ve mudurluk bazli triyaj hesaplama
4. **Takip** - Randevu, ilerleme, tekrar eden temalar

### Temel Islevler
- Islevsel seans sayfasi (20-30 dk gorusmeler)
- Standart protokol (tum personele ayni uygulama)
- Dinamik triyaj (veri ekledikce guncellenir)
- Kisi ve mudurluk bazli analiz
- AI destekli supervizyon (transkript analizi)

---

## 3. Veri Katmanlari

### 3.1 ANKET VERILERI (Mudurluk Bazli)
**Kaynak:** `rapor_verileri.js` + `survey_data` tablosu

| Metrik | Aciklama | Belediye Geneli |
|--------|----------|-----------------|
| Genel Memnuniyet | Kurumda calismaktan memnuniyet | %90.8 |
| Is Stresi/Yuku | Gorev yuku, vatandas yogunlugu, duygusal zorlayicilik, zaman sikisikligi | %69.1 |
| Kurum Destegi | Yonetici iliskileri, ekip uyumu, rol netligi, kurumsal iletisim, egitim, calisma kosullari | %82.3 |
| Denge | Kurum Destegi - Is Stresi (pozitif = iyi) | +13.2 |
| Ruh Sagligi Riski | 4 soruya olumsuz yanit orani | %52.2 |

**4 Ruh Sagligi Sorusu:**
1. Keyif alamama (anhedoni)
2. Uzgun/cokkun hissetme (depresif mood)
3. Gerginlik/kaygi (anksiyete)
4. Endiseleri kontrol edememe

**Her Mudurluk Raporu Iceriyor:**
- **Sonuc Ozeti** - Basliktan hemen sonra, tek paragraf degerlendirme
- **Guclu Yonler** - Ortalama ustu performans alanlari
- **Gelistirilmesi Gereken Alanlar** - Iyilestirme gereken noktalar
- **Dikkat Ceken Bulgular** - Ozel durumlar
- **Tema Bazli Performans Tablosu** - 10 tema karsilastirma
- **Acik Uclu Yorumlar** - Personel geri bildirimleri

### 3.2 SCL-90 SONUCLARI (Kisi Bazli)
**Kaynak:** Excel import → `personeller` tablosu

| Alan | Aralik | Aciklama |
|------|--------|----------|
| GSI (Global Severity Index) | 0-4 | Genel belirti siddeti |
| Somatizasyon | 0-4 | Bedensel yakinmalar |
| Obsesif-Kompulsif | 0-4 | Takintili dusunceler |
| Kisilerarasi Duyarlilik | 0-4 | Sosyal rahatsizlik |
| Depresyon | 0-4 | Cokkunluk belirtileri |
| Anksiyete | 0-4 | Kaygi belirtileri |
| Ofke-Dusmanlik | 0-4 | Ofke kontrolu |
| Fobik Anksiyete | 0-4 | Korkular |
| Paranoid Dusunce | 0-4 | Suphecilik |
| Psikotizm | 0-4 | Gerceklik algilama |

**Kritik Maddeler (Otomatik Acil):**
- Madde 15: Intihar dusuncesi
- Madde 16: Sesler duyma
- Madde 35: Baskalarinin dusuncelerini bilme
- Madde 62: Kontrol disi dusunceler

### 3.3 SEANS VERILERI (Kisi Bazli)
**Kaynak:** Seans sayfasi girisi → `seanslar` tablosu

| Alan | Icerik |
|------|--------|
| MSE | 5 bilesen: gorunum, konusma, mood, dusunce, bilis |
| Hizli Tarama | PHQ-4 + psikoz kirmizi bayraklar |
| Ana Sorun | Kategori (is/aile/saglik/maddi/iliski) + serbest not |
| Klinik Notlar | SOAP/DAP/BIRP formatinda |
| Seans Risk Puani | 1-5 arasi (1=iyi, 5=kritik) |
| Tedavi Plani | Hedefler, ev odevi |
| Ses Kaydi | Referans path |
| Transkript | Whisper API ciktisi |

### 3.4 AI ANALIZI (Psikologa Yardimci Oneri Sistemi)
**Kaynak:** Transkript + context → AI ciktisi

> **NOT:** AI Analizi triyaj hesaplamasina **DAHİL DEĞİL**.
> Sadece psikologa yardimci oneri ureten bir sistemdir.
> Psikolog onerileri gorur, degerlendirir ve kabul/reddet/duzenle secenekleriyle kullanir.

| Cikti | Aciklama |
|-------|----------|
| Kacirilan Noktalar | Psikologun fark etmemis olabilecegi konular |
| Risk Degerlendirmesi | Oneri niteliginde (triyaja etki etmez) |
| Tani Izlenimi Onerisi | DSM-5 uyumlu oneri |
| Tedavi Plani Onerisi | Mudahale onerileri |
| Mudurluk Baglantisi | Sistemik sorunlarla iliski |

---

## 4. Seans Protokolu (20-30 Dakika)

### Seans Oncesi (Hazirlik)
Psikolog seans baslamadan once su verileri gorur:
- Kunye bilgileri (yas, cinsiyet, kidem, gorev)
- Mudurluk ozeti (anketten - sonuc metni, denge, risk)
- SCL-90 sonuclari (varsa - GSI, kritik maddeler)
- Onceki seanslar (varsa - ozet, hedefler, ev odevi)

### Seans Sirasinda (Ses Kaydi Acik)

```
0-3 dk   : HIZLI TARAMA
           - PHQ-4 (4 soru: kaygi, endise, keyif, umutsuzluk)
           - Psikoz kirmizi bayraklar (2 soru: goruntuler, sesler)
           - Otomatik risk hesaplama

3-7 dk   : KISA MSE
           - Gorunum & Davranis (giyim, hijyen, goz temasi)
           - Konusma (hiz, ton, tutarlilik)
           - Duygudurum (mood slider 1-10)
           - Dusunce (icerik, surec, psikotik belirti?)
           - Bilis & Yargi (yonelim, icgoru)

7-15 dk  : ANA GORUSME
           - "Sizi buraya getiren nedir?"
           - Sorun kategorisi secimi
           - Mudurluk baglamiyla karsilastirma
           - Serbest not

15-22 dk : COZUM ODAKLI (SFBT)
           - "Ne ise yariyor?" (guclu yonler)
           - "Bu hafta ne yapabilirsiniz?" (kucuk hedef)
           - Ev odevi / gorev belirleme

22-28 dk : PLANLAMA
           - Takip gerekli mi? (Evet/Hayir)
           - Oncelik (Rutin/Yakin/Acil)
           - Yonlendirme (Yok/Psikiyatri/Dis Terapi/IK)
           - Sonraki randevu tarihi

28-30 dk : KAPANIS
           - Ozet (birlikte)
           - Sorular?
```

### Seans Sonrasi
1. Transkript olustur (Whisper API)
2. AI analizi al (context ile birlikte)
3. Psikolog degerlendirmesi (AI onerisini kabul/reddet/duzenle)
4. Nihai klinik sentez kaydet

---

## 5. Dinamik Triyaj Hesaplama

### Triyaj Nedir?
Triyaj = Kisinin veya mudurlukun **final risk durumu**. Gorusme onceliklendirmesi icin degil, analiz sonucu olarak kullanilir.

### Kisi Triyaji (0-100 puan)

**Asama 1: Sadece Anket Verisi**
```
TRIYAJ = (Mud.Denge × 0.50) + (Mud.RuhSag × 0.50)
```

**Asama 2: + SCL-90**
```
TRIYAJ = (SCL-90 × 0.60) + (Mud.Denge × 0.20) + (Mud.RuhSag × 0.20)
```

**Asama 3: + Seans (FİNAL)**
```
TRIYAJ = (SCL-90 × 0.40) + (Seans × 0.40) + (Mudurluk × 0.20)
```

### Mudurluk Triyaji

**Gorusme oncesi:**
```
MUD.TRIYAJ = (Denge × 0.50) + (RuhSag × 0.50)
```

**Gorusmeler basladiktan sonra:**
```
MUD.TRIYAJ = (Denge × 0.25) + (RuhSag × 0.25) + (Ort.SCL × 0.25) + (Ort.Seans × 0.25)
+ Sistemik sorun bonusu (ayni tema 3+ kiside → +10)
```

### Puan Donusumleri
| Ham Deger | Formul | Sonuc |
|-----------|--------|-------|
| Mudurluk Denge (-3.5 ile +35) | `50 - (denge × 1.5)` | 0-100 |
| SCL-90 GSI (0-4) | `GSI × 25` | 0-100 |
| Seans Risk (1-5) | `(puan - 1) × 25` | 0-100 |

### Triyaj Kategorileri
| Puan | Kategori | Renk | Aksiyon |
|------|----------|------|---------|
| 85-100 | Kritik | Kirmizi | Acil mudahale + psikiyatri |
| 70-84 | Yuksek | Turuncu | 1 hafta icinde takip |
| 50-69 | Orta | Sari | 2-4 hafta icinde takip |
| 30-49 | Dusuk | Yesil | Rutin takip (aylik) |
| 0-29 | Minimal | Beyaz | Ihtiyac halinde |

---

## 6. Sayfa Yapilari

### 6.1 Seans Sayfasi
**Sol Panel (Referans - Salt Okunur):**
- Kunye (ad, yas, gorev, kidem)
- Mudurluk ozeti (sonuc metni + denge + risk)
- SCL-90 sonuclari (GSI + kritik maddeler)
- Onceki seanslar (tarih, ozet, risk)

**Sag Panel (Giris):**
- Tab 1: Hizli Tarama (PHQ-4, psikoz bayraklari)
- Tab 2: MSE + Gorusme (5 bilesen, ana sorun)
- Tab 3: Plan + Takip (hedef, ev odevi, randevu)
- Tab 4: Sentez + AI (transkript, AI analiz, final not)

### 6.2 Dashboard
- Oncelikli takip listesi (yuksek riskli kisiler)
- Mudurluk ozet tablosu:
  - Mudurluk adi
  - Denge puani
  - Ruh sagligi riski
  - Gorusme sayisi / toplam
  - Ortalama SCL-90
  - Ortalama seans riski
- Ilerleme gostergesi (gorusulen/toplam)

### 6.3 Triyaj Listesi
- Filtreler: Mudurluk, risk kategorisi, SCL-90 durumu, gorusme durumu
- Tablo: Kisi, mudurluk, SCL-90, seans sayisi, triyaj puani, kategori
- Dinamik siralama

### 6.4 Mudurluk Analiz
**Anket Bolumu:**
- Sonuc ozeti
- Guclu yonler
- Gelistirilmesi gereken alanlar
- Tema bazli performans

**Klinik Bolumu:**
- Gorulen kisi listesi
- Ortalama SCL-90 ve seans riski
- Tekrar eden temalar (otomatik + manuel)
- Mudurluk klinik notu (psikolog yazar)

### 6.5 Takvim
- Haftalik gorunum
- Randevu ekleme/duzenleme
- Mudurluk takibi (hangi mudurlukle ne kadar gorusulmus)

---

## 7. Veritabani Semasi

### Tablolar
| Tablo | Aciklama |
|-------|----------|
| `mudurlukler` | 30 mudurluk, anket metrikleri |
| `personeller` | 2080 personel, kunye, SCL-90, triyaj |
| `seanslar` | Gorusme kayitlari |
| `randevular` | Randevu planlama |
| `triyaj_gecmisi` | Triyaj degisim loglari |
| `survey_data` | Anket JSON verisi |

### Onemli Iliskiler
- Personel → Mudurluk (N:1)
- Personel → Seanslar (1:N)
- Personel → Randevular (1:N)
- Seans → AI Analiz (1:1)

---

## 8. Teknik Bilgiler

### Teknoloji Stack
- **Backend:** Flask 3.x
- **Veritabani:** SQLite
- **Frontend:** Tailwind CSS + Jinja2
- **Grafikler:** Chart.js
- **Ses Transkript:** Whisper API (planli)

### Dosya Yapisi
```
anket-1--2/
├── main.py              # Flask uygulamasi, tum route'lar
├── models.py            # SQLAlchemy modelleri
├── utils.py             # Triyaj hesaplama, yardimci fonksiyonlar
├── importers.py         # Excel import fonksiyonlari
├── rapor_verileri.js    # Anket verileri (HTML formatinda)
├── templates/
│   ├── base.html
│   ├── _sidebar.html
│   └── psikoloji/
│       ├── dashboard.html
│       ├── triyaj.html
│       ├── seans.html      # 4 tab, MSE, protokol
│       ├── takvim.html
│       ├── analiz.html
│       ├── mudurluk_analiz.html
│       └── personel_detail.html
└── CLAUDE_CONTEXT.md    # Bu dosya
```

### Onemli Route'lar
| URL | Aciklama |
|-----|----------|
| `/psikoloji/dashboard` | Ana sayfa |
| `/psikoloji/triyaj` | Personel listesi |
| `/psikoloji/seans/<id>` | Seans sayfasi |
| `/psikoloji/takvim` | Randevu takvimi |
| `/psikoloji/analiz` | Mudurluk analizi |
| `/psikoloji/analiz/<id>` | Tek mudurluk detay |
| `/psikoloji/personel/<id>` | Personel detay |

---

## 9. Onemli Kurallar

1. **Gorusmeler karisik** - Mudurluk veya risk sirasina gore degil, musaitlige gore
2. **Triyaj dinamik** - Her veri eklendikce otomatik guncellenir
3. **Standart protokol** - 2080 kisinin hepsine ayni uygulama
4. **Ses kaydi zorunlu** - Supervizyon icin AI analizi yapilacak
5. **Mudurluk baglami** - Her gorusmede mudurluk verileri gorunur olmali
6. **Sistemik sorun tespiti** - Ayni temali 3+ kisi = mudurluk sorunu

---

## 10. Terminoloji

| Terim | Anlam |
|-------|-------|
| Kurumsal Fotograf | Anket verileriyle elde edilen mudurluk bazli genel resim |
| Bireysel Fotograf | SCL-90 ile elde edilen kisi bazli semptom profili |
| Kanit Temelli | Veri kaynaklarina dayali, olculebilir bulgular |
| Triyaj | Final risk skoru (0-100) |
| Denge | Kurum Destegi - Is Stresi |
| GSI | Global Severity Index (SCL-90) |
| MSE | Mental Status Examination |
| PHQ-4 | 4 soruluk depresyon/anksiyete tarama |
| SFBT | Solution Focused Brief Therapy |
| SOAP | Subjective-Objective-Assessment-Plan |

---

## 11. Degisiklik Gecmisi

| Tarih | Degisiklik |
|-------|------------|
| 2026-01-28 | Ilk versiyon olusturuldu |
| 2026-01-28 | Seans protokolu eklendi (20-30 dk) |
| 2026-01-28 | Dinamik triyaj hesaplama eklendi |
| 2026-01-28 | AI supervizyon analizi eklendi |
| 2026-01-28 | Stratejik perspektif eklendi (Makro→Mikro, Sunum Hedefi) |
| 2026-01-28 | Gorusme sistemi detaylari eklendi (zorunlu/gonullu) |
| 2026-01-28 | Terminolojiye kanit temelli kavramlar eklendi |
| 2026-01-28 | AI analizi triyajdan ayrildi (sadece oneri sistemi) |

---

*Bu dosya Claude'un projeyi her seansta dogru anlamasi icin referans dokumanidir.*
