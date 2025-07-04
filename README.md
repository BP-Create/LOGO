# VibeMatch Project Flowchart

This flowchart illustrates the complete pipeline of the VibeMatch movie recommendation system, integrating text-based emotion analysis and facial emotion recognition.

```mermaid
graph LR
    A[Başlangıç] --> B(Veri Edinimi ve Hazırlık);

    B --> C{Giriş Verileri};
    C --> C1[Belediye DWG'si & Nokta Bulutu Verileri];

    C1 --> D(3D Modelleme ve Geometri Tanımı);
    D --> D1[Rhino 3D ve Grasshopper Kullanımı];
    D1 --> E(3D Bina Modelleri Oluşturulması);

    E --> F(Enerji Simülasyonu ve Performans Verisi Üretimi);
    F --> F1[Honeybee, Ladybug ve EnergyPlus ile Kapsamlı Simülasyonlar];
    F1 --> G(Detaylı Simülasyon Veri Kümeleri Oluşturulması);

    G --> H{Coğrafi Veri Entegrasyonu};
    E --> H1[3D Modellerden Coğrafi Shapefile Dönüşümü];
    H1 --> I(ArcGIS Pro'da Veri Eşleştirme ve Entegrasyon);
    G --> I;

    I --> J(Web Platformu Geliştirme ve Araç Konsolidasyonu);
    J --> J1[ArcGIS Pro'dan ArcGIS Online'a Veri Yayınlama];
    J1 --> J2[Python, JavaScript ve Grafik Kütüphaneleri ile İnteraktif Dashboard ve Araç Geliştirme];

    J --> K[Sonuç: Kapsamlı Web Tabanlı Karar Destek Aracı];
    K --> L[Bitiş];
