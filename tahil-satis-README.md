# 🌾 Tahıl & Ürün Satış Portalı

Spring Boot ile geliştirilmiş, tahıl ve tarım ürünleri için basit bir satış/ilan yönetim sistemi.

## 🖥️ Ekran Görüntüleri

> *(Ekran görüntüleri eklenecek)*

## 🚀 Özellikler

- **Ürün Listeleme** — Tüm ürünleri tablo halinde görüntüleme
- **Arama** — Ürün adı veya cinsine göre canlı arama
- **Ürün Ekleme / Düzenleme** — Form üzerinden CRUD işlemleri
- **Ürün Detay Sayfası** — Seçilen ürünün tüm bilgilerini gösteren detay görünümü
- **Görsel Seçimi** — Ürün için hazır görsellerden seçim yapma
- **Silme** — Onay diyaloğu ile güvenli silme

## 🛠️ Teknolojiler

| Teknoloji | Versiyon |
|-----------|----------|
| Java | 24 |
| Spring Boot | 3.4.12 |
| Spring Data JPA | - |
| Thymeleaf | - |
| MySQL | - |
| Lombok | - |
| Bootstrap | 5.3.0 |

## 🏗️ Mimari

Katmanlı (layered) mimari kullanılmıştır:

```
Controller → Service → Repository → Entity
              ↕
            Mapper ↔ DTO
```

- **Controller**: HTTP isteklerini karşılar, view döner
- **Service**: İş mantığı
- **Repository**: Spring Data JPA ile veritabanı işlemleri
- **Mapper**: Entity ↔ DTO dönüşümü
- **DTO**: View katmanına veri taşıma

## ⚙️ Kurulum

### Gereksinimler

- Java 24 (JDK)
- Maven
- MySQL Server

### Veritabanı Kurulumu

```sql
CREATE DATABASE tahil_db;
```

Tablo, `spring.jpa.hibernate.ddl-auto=update` ayarı sayesinde uygulama ilk çalıştığında otomatik oluşturulur.

### Bağlantı Ayarları

`src/main/resources/application.properties` dosyasını kendi MySQL bilgilerinize göre düzenleyin:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/tahil_db?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
spring.datasource.username=KULLANICI_ADINIZ
spring.datasource.password=PAROLANIZ
```

### Çalıştırma

```bash
./mvnw spring-boot:run
```

Uygulama varsayılan olarak `http://localhost:8080` adresinde çalışır.

## 📁 Proje Yapısı

```
src/main/java/com/tarim/tahil_satis/
├── controller/
│   └── TahilController.java
├── service/
│   ├── TahilService.java
│   └── TahilServiceImpl.java
├── repository/
│   └── TahilRepository.java
├── mapper/
│   └── TahilMapper.java
├── dto/
│   └── TahilDto.java
├── entity/
│   └── Tahil.java
└── TahilSatisApplication.java

src/main/resources/
├── templates/
│   ├── index.html
│   ├── form.html
│   └── detay.html
├── static/images/
└── application.properties
```

## 🔌 Endpoint'ler

| Method | Endpoint | Açıklama |
|--------|----------|----------|
| GET | `/` | Ana sayfa, ürün listesi ve arama |
| GET | `/yeni` | Yeni ürün ekleme formu |
| POST | `/kaydet` | Ürün kaydetme |
| GET | `/duzenle/{id}` | Ürün düzenleme formu |
| GET | `/sil/{id}` | Ürün silme |
| GET | `/goruntule/{id}` | Ürün detay sayfası |

## ⚠️ Bilinen Limitasyonlar

- Veritabanı bağlantı bilgileri şu an `application.properties` içinde yer almaktadır; ilerleyen sürümlerde ortam değişkenlerine (environment variables) taşınacaktır
- Ürün görselleri için kullanıcı yüklemesi yerine hazır görsel listesinden seçim yapılmaktadır

## 📄 Lisans

Bu proje eğitim amaçlı geliştirilmiştir.
