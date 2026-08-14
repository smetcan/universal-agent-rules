# AI Kodlama Ajanları İçin Kural ve İş Akışı Sistemi

[🇬🇧 English](https://gemini.google.com/app/README.md "null") | [🇹🇷 Türkçe](https://gemini.google.com/app/README_TR.md "null")

Farklı yazılım projelerimde yapay zeka ajanlarını (Gemini, Claude, Cursor, Copilot vb.) yönlendirmek ve disipline etmek için kendi ihtiyaçlarımdan yola çıkarak geliştirdiğim kural ve iş akışı dokümanları.

## Neden Böyle Bir Şey Yaptım?

Farklı projelerde çalışırken her repo için ayrı kural dosyaları (`AGENTS.md`, `RULES.md`, `GEMINI.md`) yazmak zamanla tam bir karmaşaya dönüştü. Bir projede denediğim iyi bir kuralı diğerine taşımayı unutuyordum ya da kural dosyaları kontrolsüzce büyüyordu.

Fark ettim ki:

- Bazı kurallar projeye özeldi (kullanılan diller, kütüphaneler, komutlar).

- Bazı kurallar ise hangi dili veya framework'ü kullanırsam kullanayım değişmeyen evrensel mühendislik disiplinlerimdi (Git kullanımı, güvenlik, insan onayı, hata yönetimi).

Bu dağınıklığı toplamak için oturup kendi yazdığım kural dosyalarını konsolide ettim. Ardından yapay zeka modelleriyle saatlerce tartışarak, deneme-yanılmalar yaparak ve pek çok iterasyondan geçirerek bu ikili kural mimarisini olgunlaştırdım. Ben de süreç içerisinde kendimi geliştirmeye çalışıyorum ve bu sistemi projelerimde aktif olarak kullanıyorum. Faydalı olabileceğini düşünerek açığa çıkarmak istedim.

## Sistem Nasıl Çalışıyor?

Sistem temel olarak görevleri birbirinden ayıran 3 ana dosyadan oluşuyor:

1. **`UNIVERSAL_RULES.md`:** Teknolojiden bağımsız anayasa. Ajanın nasıl davranacağını, insanla nasıl iletişim kuracağını, kod kalitesi standartlarını, Git dal (*branch*) kurallarını ve güvenlik ilkelerini belirler.

2. **`PROJECT_RULES.md`:** Projenin gerçeklik kartı. Projede hangi teknoloji var, hangi komutlar gerçek, mimari yapı nasıl? Ajan uydurma bilgi üretmesin diye projenin somut durumunu tutar.

3. **`DEVELOPMENT_LOG.md`:** Ajanın yaptığı anlamlı işleri kaydettiği günlük dosyası. Hem benim hem de sistemin yapılan işleri geriye dönük takip etmesini sağlar.

4. **`GEMINI.md` / `AGENTS.md`:** Editör istemine `@./UNIVERSAL_RULES.md` ve `@./PROJECT_RULES.md` referanslarını bağlayan giriş dosyası.

## Dokümanlarda Hangi Kurallar Var?

Göz atmak isteyenler için dokümanların özeti ve ajana koyduğu ana kısıtlamalar şunlar:

### 1. `UNIVERSAL_RULES.md` (Ajan Davranış Anayasası)

- **Sormadan İş Yapma (Ask First):** Paket ekleme, veritabanı şemasını değiştirme, UI/UX tasarım sistemine dokunma veya breaking-change yapma süreçlerinde benden onay almak zorunda.

- **Tahmin Etme (No Guessing):** Dosya yollarını, veri modellerini veya fonksiyon imzalarını ezbere tahmin edemez; kaynak dosyaları okumak zorundadır.

- **Semptom Yamalama Yasağı:** Hataları boş `try/catch` ile yutamaz, sahte verilerle geçiştiremez veya `@ts-ignore` / `any` kullanarak tipleri bastıramaz. Hatanın kök nedenini bulmak zorundadır.

- **Git ve Dal Disiplini:** Her iş için göreve uygun dal açar (`feat/`, `fix/` vb.). Kodu teste sunup benim onayımı almadan ana dala birleştiremez (*merge*).

- **Bağlam İzolasyonu:** Aktif bir dal henüz test edilip birleştirilmediyse, farklı bir isteğimde kodu karıştırmayıp proaktif olarak "Mevcut dalı tamamlayalım veya saklayalım, yeni konu için temiz dal açalım" uyarısı yapar.

- **Güvenlik:** Kod içine kesinlikle API anahtarı veya şifre yazamaz; `.env` kullanımını zorunlu kılar.

### 2. `PROJECT_RULES.md` (Projenin Teknik Gerçekliği)

- **Doğruluk Statüleri (`VERIFIED`, `OBSERVED`, `DECLARED`, `UNVERIFIED`):** Projedeki bilgileri güven seviyesine göre etiketler. Kanıtlayamadığı bilgiyi uyduramaz.

- **Komut Uydurmama:** Sadece projede tanımlı ve doğrulanmış komutları çalıştırır.

- **Keşif Protokolü (Discovery Protocol):** Projeye ilk kez girildiğinde manifest dosyalarını (`package.json`, `pubspec.yaml` vb.) inceleyerek teknik kimliği otomatik çıkarır.

### 3. `DEVELOPMENT_LOG.md` (Geliştirme Günlüğü)

- **Sabit Şema:** Tarih, işlem tipi, durum, dal, kaynak dal, commit hash ve özeti belirli bir formatta tutar.

- **Temiz Günlük:** Sadece anlamlı geliştirmeleri kaydeder; sıradan dosya okumalarını veya aramaları loga yazmaz.

## Dürüst Olmak Gerekirse: Kısıtlamaları ve Eksi Yönleri

Bu sistem her ne kadar işlerimi çok rahatlatsa da gümüş kurşun değil. Kullanırken yaşadığım bazı dezavantajları şunlar:

- **Bağlam (Token) Yükü:** Kural dosyaları detaylı olduğu için her sorguda belirli bir miktar bağlam harcıyor. Bu da çok uzun sohbetlerde token limitine daha hızlı ulaşılmasına sebep olabiliyor.

- **İlk Onboarding Süresi:** Yeni bir projeye girerken ajanın projeyi keşfetmesi ve `PROJECT_RULES.md` dosyasını doldurması birkaç dakika sürebiliyor.

- **Küçük Projelerde Bürokrasi:** Tek dosyalık hızlı bir script yazarken veya ufak bir deneme yaparken bu kadar kural takip etmek fazla bürokratik gelebilir.

- **Ajan Sapması (Agent Drift):** Yapay zeka modelleri ne kadar kural koyarsanız koyun bazen çok uzun oturumlarda kurallardan sapabiliyor. İnsan gözetimi ve kontrolü her zaman şart.

## Nasıl Kullanılır?

1. **`UNIVERSAL_RULES.md`** dosyasını projenizin kök dizinine kopyalayın.

2. **`PROJECT_RULES.md`** dosyasını projenize kök dizinine kopyalayın.

3. Kullandığınız editöre uygun giriş dosyasını (`GEMINI.md`, `.cursorrules`, `AGENTS.md`) oluşturup iki dosyaya referans verin (`@./UNIVERSAL_RULES.md`, (`@./PROJECT_RULES.md`).

4. Aşağıdaki başlangıç istemlerinden ihtiyacınıza uygun olanını vererek süreci başlatın.

## Başlangıç İstemleri (Prompts)

### 1. Mevcut Projede Onboarding İsterken

```
Bu projede ilk kez onboarding yap.

PROJECT_RULES.md içindeki discovery protokolünü eksiksiz uygula,
repository'yi incele ve PROJECT_RULES.md'yi yalnızca kanıtlanabilir
bilgilerle doldur.

Kod değişikliği yapma.
```

### 2. Sıfırdan Proje Başlatırken (Greenfield)

```
Yeni bir greenfield proje başlatıyoruz.

Önce gerekli proje gereksinimlerini ve teknik kararları benden topla.

Framework, architecture, database, state management veya tooling
konusunda varsayım yapma.

Kararlaştırılan bilgileri PROJECT_RULES.md içerisinde DECLARED olarak kaydet.

Başlangıç teknik planı oluşturulmadan implementation'a başlama.
```

## Katkıda Bulunma

Ben de bu alanda denemeler yapmaya ve süreçlerimi iyileştirmeye devam ediyorum. Eğer sistemde bir eksik, çelişki veya geliştirilebilecek bir alan görürseniz Issue açabilir ya da Pull Request gönderebilirsiniz. Deneyimlerinizi paylaşmanızdan mutluluk duyarım!
