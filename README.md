# ⚽ EA FC 26 Turnuva Yönetim Sistemi

Arkadaşlarla oynadığımız EA FC 26 turnuvasını takip etmek için oluşturulmuş modern bir web uygulaması.

## 🎯 Özellikler

- **📊 Canlı Puan Durumu**: Maç sonuçlarına göre otomatik hesaplanan puan tablosu
- **📅 Fikstür Takibi**: Tüm maçları ve skorları görüntüleme
- **🎲 Kura Sistemi**: Oyuncu-takım eşleşmeleri
- **📱 Mobil Uyumlu**: Telefon, tablet ve masaüstünde sorunsuz çalışır
- **⚡ Real-time Güncellemeler**: Skorlar girildiğinde anında güncellenir
- **🔒 Güvenli Admin Paneli**: Sadece yetkili kişi skor girebilir

## 🚀 Canlı Demo

- **Ana Sayfa**: [https://bedircangul.github.io/fc26dcsuperleague/](https://bedircangul.github.io/fc26dcsuperleague/)
- **Admin Panel**: [https://bedircangul.github.io/fc26dcsuperleague/admin.html](https://bedircangul.github.io/fc26dcsuperleague/admin.html)

## 🏆 Turnuva Bilgileri

### Katılımcılar
- 10 oyuncu
- 10 farklı takım (Arsenal, Liverpool, PSG, Barcelona, Real Madrid, Manchester City, Bayern Munich, Inter, Atletico Madrid, Chelsea)

### Format
- Tek devre lig usulü
- Her takım birbiriyle 1 kez karşılaşır
- Toplam 45 maç

### Puan Sistemi
- **Galibiyet**: 3 puan
- **Beraberlik**: 1 puan
- **Mağlubiyet**: 0 puan

### Sıralama Kriterleri
1. Toplam Puan
2. İkili Averaj
3. Genel Averaj (Atılan - Yenilen)
4. Atılan Gol
5. Alfabetik Sıralama

## 🛠️ Teknolojiler

- **Frontend**: Vanilla JavaScript, HTML5, CSS3
- **Backend**: Supabase (PostgreSQL)
- **Hosting**: GitHub Pages
- **Real-time**: Supabase Real-time Subscriptions

## 📦 Kurulum

Bu proje tamamen hazır ve canlı! Kuruluma gerek yok, sadece linke tıkla ve kullanmaya başla.

### Kendi Versiyonunu Oluşturmak İstersen:

1. Bu repository'yi fork'la
2. Supabase hesabı oluştur (ücretsiz)
3. Gerekli tabloları oluştur (SQL kodları aşağıda)
4. `index.html` ve `admin.html` dosyalarındaki Supabase bilgilerini güncelle
5. GitHub Pages'i aktifleştir

### Supabase Tabloları

```sql
-- Kura tablosu
CREATE TABLE draw (
  id SERIAL PRIMARY KEY,
  player_name TEXT NOT NULL UNIQUE,
  team_name TEXT NOT NULL UNIQUE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Maçlar tablosu
CREATE TABLE matches (
  id SERIAL PRIMARY KEY,
  home_team TEXT NOT NULL,
  away_team TEXT NOT NULL,
  home_score INTEGER,
  away_score INTEGER,
  match_date TIMESTAMPTZ DEFAULT NOW(),
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- RLS politikaları
ALTER TABLE draw ENABLE ROW LEVEL SECURITY;
ALTER TABLE matches ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Public read draw" ON draw FOR SELECT USING (true);
CREATE POLICY "Public read matches" ON matches FOR SELECT USING (true);
CREATE POLICY "Service role can do everything on matches" ON matches FOR ALL USING (true) WITH CHECK (true);
```

## 🎮 Kullanım

### Herkese Açık Sayfa
- Kura, Fikstür ve Puan Durumu sekmelerini gez
- Maç sonuçlarını takip et
- Puan tablosunu kontrol et

### Admin Paneli (Sadece Yetkili)
1. Admin sayfasına git
2. Şifreyi gir
3. Maç skorlarını gir ve kaydet
4. Sonuçlar anında public sayfaya yansır

## 📱 Ekran Görüntüleri

Mobil uyumlu tasarım sayesinde her cihazda mükemmel görünür!

## 🤝 Katkıda Bulunma

Bu proje arkadaş grubu için özel olarak yapıldı, ancak fikirlerinizi issues bölümünde paylaşabilirsiniz.

## 📝 Lisans

MIT License - İstediğiniz gibi kullanabilirsiniz!

## 👨‍💻 Geliştirici

**Bedircan Gül**
- GitHub: [@bedircangul](https://github.com/bedircangul)

---

⚽ **Hadi bakalım, şampiyon kim olacak?** 🏆
