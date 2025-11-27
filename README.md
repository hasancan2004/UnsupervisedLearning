# Country Budget Clustering

Bu projede ülkeleri ekonomik ve sosyo-demografik değişkenlere göre
segmentleyip hangi ülkelerin bütçe desteğine daha fazla ihtiyaç duyduğunu
inceledim.

## Kullanılan Veri

- child_mort
- exports
- health
- imports
- income
- inflation
- life_expec
- total_fer
- gdpp

## Uygulanan Yöntemler

- Ölçekleme: MinMaxScaler
- Boyut indirgeme: PCA (3 bileşen)
- Kümeleme Algoritmaları:
  - KMeans (PCA ile ve PCA'sız)
  - Hierarchical Clustering (PCA ile ve PCA'sız)
  - DBSCAN (PCA üzerinde) – *denendi, ancak sınırlı anlamlı segmentler verdi*
  - HDBSCAN (PCA üzerinde) – *noise + esnek cluster yapısı için kullanıldı*

## Ana Sonuçlar

- KMeans + PCA ve Hierarchical + PCA, ülkeleri **Budget Needed / In Between / No Budget Needed**
  şeklinde oldukça mantıklı segmentlere ayırdı.
- HDBSCAN, bazı ülkeleri `Noise / Uncertain` olarak işaretleyerek yoğunluktan
  sapmaları gösterdi ve genel harita gerçek dünya dağılımıyla uyumlu çıktı.
- DBSCAN, çoğu parametrede tek büyük cluster ürettiği için ana analizde
  kullanılmadı, sadece alternatif yöntem olarak değerlendirildi.

## Dünya Haritaları

Notebook içerisinde Plotly ile üretilen choropleth haritalarda:
- Kırmızı: Budget Needed
- Sarı: In Between
- Yeşil: No Budget Needed
- Gri: Noise / Uncertain
