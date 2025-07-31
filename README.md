# AI Chatbox WordPress Eklentisi

Modern ve güvenli AI chatbox WordPress eklentisi. Tüm AI sağlayıcılarını destekler ve lisans sistemi ile korunur.

## Özellikler

### 🤖 AI Desteği
- **OpenAI GPT** (GPT-3.5-turbo, GPT-4)
- **Anthropic Claude** (Claude-3-sonnet)
- **Google Gemini** (Gemini Pro)

### 🎨 Özelleştirme
- Buton tasarımı (icon, renk, boyut, şekil)
- Chatbox pozisyonu (yukarı/aşağı ayarlama)
- Karşılama mesajı
- AI ve kullanıcı profil fotoğrafları
- Chatbox renkleri

### 🔒 Güvenlik
- Rate limiting (dakikada max 10 istek)
- SQL injection koruması
- XSS koruması
- Güvenlik başlıkları
- API anahtarı şifreleme
- Şüpheli istek tespiti

### 📜 Lisans Sistemi
- 1 yıllık lisans
- Otomatik lisans doğrulama
- Lisans süresi kontrolü
- Admin panelinden lisans yönetimi

### 🔄 Otomatik Güncelleme
- Lisanslı kullanıcılar için otomatik güncelleme
- Güvenli güncelleme sistemi
- Güncelleme bildirimleri

## Kurulum

1. Eklentiyi WordPress'e yükleyin
2. WordPress admin panelinden eklentiyi aktifleştirin
3. "AI Chatbox" menüsünden ayarları yapın
4. Lisans anahtarınızı girin
5. AI sağlayıcısı ve API anahtarını seçin

## Lisans Sistemi

### Lisans Sunucusu Gereksinimleri

Lisans sistemi için ayrı bir sunucu gereklidir. Sunucu şu API endpoint'lerini sağlamalıdır:

#### 1. Lisans Doğrulama
```
POST /api/verify
Body: {
    "license_key": "xxx",
    "site_url": "https://example.com",
    "plugin_slug": "ai-chatbox",
    "plugin_version": "1.0.0"
}
Response: {
    "status": "valid|invalid|expired",
    "expires": "2024-12-31 23:59:59"
}
```

#### 2. Lisans Aktifleştirme
```
POST /api/activate
Body: {
    "license_key": "xxx",
    "site_url": "https://example.com",
    "plugin_slug": "ai-chatbox"
}
Response: {
    "status": "activated|error",
    "expires": "2024-12-31 23:59:59",
    "message": "Success message"
}
```

#### 3. Lisans Deaktifleştirme
```
POST /api/deactivate
Body: {
    "license_key": "xxx",
    "site_url": "https://example.com",
    "plugin_slug": "ai-chatbox"
}
Response: {
    "status": "deactivated|error",
    "message": "Success message"
}
```

#### 4. Güncelleme Kontrolü
```
POST /api/check-update
Body: {
    "license_key": "xxx",
    "site_url": "https://example.com",
    "plugin_slug": "ai-chatbox",
    "current_version": "1.0.0"
}
Response: {
    "has_update": true|false,
    "new_version": "1.0.1",
    "download_url": "https://...",
    "requires": "5.0",
    "requires_php": "7.4",
    "tested": "6.0",
    "last_updated": "2024-01-01",
    "description": "...",
    "changelog": "..."
}
```

#### 5. Plugin Bilgisi
```
POST /api/plugin-info
Body: {
    "license_key": "xxx",
    "site_url": "https://example.com",
    "plugin_slug": "ai-chatbox"
}
Response: {
    "name": "AI Chatbox",
    "version": "1.0.1",
    "author": "İsmail Çavuş",
    "author_profile": "https://...",
    "last_updated": "2024-01-01",
    "homepage": "https://...",
    "description": "...",
    "installation": "...",
    "changelog": "...",
    "screenshots": "...",
    "banner_high": "https://...",
    "banner_low": "https://..."
}
```

## Güvenlik Özellikleri

### Rate Limiting
- Dakikada maksimum 10 API isteği
- IP bazlı kısıtlama
- Otomatik geçici bloklama

### Güvenlik Başlıkları
- X-Content-Type-Options: nosniff
- X-Frame-Options: SAMEORIGIN
- X-XSS-Protection: 1; mode=block
- Referrer-Policy: strict-origin-when-cross-origin

### Veri Şifreleme
- API anahtarları AES-256-CBC ile şifrelenir
- WordPress salt kullanılır
- Fallback mekanizması

### Saldırı Tespiti
- SQL injection denemeleri
- XSS denemeleri
- JavaScript injection
- Şüpheli karakter dizileri

## Dosya Yapısı

```
ai-chatbox/
├── ai-chatbox.php          # Ana eklenti dosyası
├── includes/
│   ├── license-manager.php  # Lisans yönetimi
│   ├── updater.php         # Otomatik güncelleme
│   └── security.php        # Güvenlik sistemi
├── admin/
│   └── admin-page.php      # Admin panel
├── templates/
│   └── chatbox.php         # Chatbox template
├── assets/
│   ├── css/
│   │   └── chatbox.css     # Stil dosyası
│   └── js/
│       └── chatbox.js      # JavaScript
└── README.md               # Bu dosya
```

## Lisans

Bu eklenti ticari kullanım için tasarlanmıştır. 1 yıllık lisans ile satılır.

**Yazar:** İsmail Çavuş

## Destek

Teknik destek için lisans sahibi ile iletişime geçin.

## Güncelleme Notları

### v1.0.0
- İlk sürüm
- AI chatbox özelliği
- Lisans sistemi
- Güvenlik özellikleri
- Otomatik güncelleme sistemi 