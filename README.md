# Vue.js Eğitim Dashboard

Bu proje, Vue.js öğrenme sürecinde temel özellikleri ve kavramları göstermek için oluşturulmuş bir dashboard uygulamasıdır.

## Özellikler

### 1. Kimlik Doğrulama (Authentication)
- **Giriş Yapma (Sign In)**
  - Email ve şifre ile giriş
  - Form validasyonu
  - Hata mesajları gösterimi
  
- **Kayıt Olma (Sign Up)**
  - Kullanıcı adı, email ve şifre ile kayıt
  - Şifre eşleşme kontrolü
  - Form validasyonu
  - Hata mesajları gösterimi

### 2. Yapılacaklar Listesi (Todo List)
- Yeni görev ekleme
- Görev silme
- Görevleri tamamlandı olarak işaretleme
- Tamamlanan görev sayısını gösterme
- Boş liste durumu kontrolü

### 3. Vue.js Özellikleri

#### Event Modifiers
- `@keyup.enter`: Yeni görev eklemek için Enter tuşu kullanımı
- `@click.stop`: Görev silme butonunda event propagation'ı engelleme

#### Çift Yönlü Veri İşleme (Two-way Data Binding)
- `v-model` kullanımı:
  - Form inputları
  - Todo girişi
  - Checkbox durumları

#### Şartlı Render (Conditional Rendering)
- `v-if`: Hata mesajları ve boş liste durumu gösterimi
- Giriş/kayıt formları arasında geçiş
- Kullanıcı oturum durumuna göre içerik gösterimi

#### Döngü İşlemleri (List Rendering)
- `v-for`: Todo listesi render etme
- Key yönetimi
- Liste filtreleme

#### Computed Properties
- Tamamlanan görev sayısı hesaplama

## Stil Özellikleri
- Responsive tasarım
- Dark mode
- Modern UI bileşenleri
- Geçiş animasyonları
- Interaktif butonlar ve form elemanları

## Proje Yapısı
- Vue 3 Composition API
- TypeScript desteği
- Vite build tool
- Component-based mimari
- Modüler CSS