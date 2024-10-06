# Image to Data Projesi Yol Haritası

Bu projede hedefimiz, ekran görüntüsündeki tablo yapısını OCR teknolojisi ile tanıyıp, sonuçları CSV formatında export eden bir Streamlit uygulaması geliştirmek. Kodun temiz ve sürdürülebilir olması için modüler bir yapı ile ilerleyeceğiz ve SOLID prensiplerini dikkate alacağız. İşlevselliği parça parça geliştirip, her modülü ayrı bir dosyada tutacağız.

### 1. Modüller ve Dosya Yapısı

Proje yapısı aşağıdaki gibi olacaktır:

```bash
image_to_data/
│
├── main.py                 # Tüm modülleri birleştiren ana dosya.
├── streamlit_app.py        # Streamlit arayüzü.
├── image_processing.py     # Görüntü işlemleri.
├── line_removal.py         # Çizgileri kaldırma işlemleri.
├── ocr_processing.py       # OCR işlemleri ve bounding box.
├── csv_writer.py           # OCR sonuçlarını CSV'ye yazma.
└── tests/
    └── test_image_processing.py    # Test modülleri.
```

### 2. Yol Haritası

#### Adım 1: Görüntü İşleme Modülü (image_processing.py)
Bu adımda, görüntüyü gri tonlamaya çevirip, threshold işlemi uygulayacağız. Ayrıca görüntüyü ters çevirme (invert) işlemlerini gerçekleştireceğiz. Bu modülü oluşturduktan sonra test edilebilir olacak.

#### Adım 2: Çizgilerin Kaldırılması (line_removal.py)
Dikey ve yatay çizgileri erozyon ve genişletme işlemleri ile kaldıracağız. Görüntüdeki tablo çizgilerini tanıyıp temizleyeceğiz.

#### Adım 3: OCR ve Metin Blokları (ocr_processing.py)
Tesseract OCR'ı kullanarak görüntüdeki metinleri tanıyacağız. Bounding box yapısını oluşturarak metin bloklarını tabloya dönüştüreceğiz.

#### Adım 4: CSV Oluşturma (csv_writer.py)
Tanınan metin bloklarını CSV formatında dışa aktaran bir fonksiyon yazacağız.

#### Adım 5: Streamlit Entegrasyonu (streamlit_app.py)
Streamlit kullanarak kullanıcı arayüzü oluşturacağız. Bu aşamada kullanıcının görsel yükleyip verileri CSV formatında export etmesini sağlayacağız.

#### Adım 6: Test ve Debug
Her modül için test dosyaları oluşturacağız. Modüllerin doğru çalıştığını doğrulamak için `pytest` kullanacağız.

---