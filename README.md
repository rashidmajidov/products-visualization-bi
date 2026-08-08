# Products Visualization (Power BI)

Bu layihə ulduz sxemi (star schema) əsasında qurulmuş satış datası üzərində Power BI vasitəsilə interaktiv "Sales Performance Dashboard" hazırlanmasını əhatə edir.

## Data Modeli

Data ulduz sxemi (star schema) formatında təşkil olunub — bir Fact cədvəli və çoxlu Dimension cədvəlləri:

```
data/
├── FactSales.csv           # Əsas satış faktları (sifariş, məhsul, müştəri, işçi, coğrafiya üzrə)
├── FactSalesTarget.csv     # Kateqoriya üzrə aylıq satış hədəfləri
│
├── DimDate2.csv            # Tarix ölçüsü (il, rüb, ay, gün, həftə sonu/bayram)
├── DimProduct.csv          # Məhsul ölçüsü (kateqoriya, subkateqoriya, rəng, ölçü, qiymət)
├── DimCustomer.csv         # Müştəri ölçüsü (loyallıq səviyyəsi, cins, qeydiyyat tarixi)
├── DimEmployee.csv         # İşçi ölçüsü (rol, işə başlama tarixi)
└── DimGeography.csv        # Coğrafiya ölçüsü (ölkə, region, şəhər)
```

`FactSales` cədvəli `OrderDateKey`, `ProductKey`, `CustomerKey`, `EmployeeKey`, `GeographyKey` açarları vasitəsilə digər cədvəllərlə əlaqələnir və `Quantity`, `UnitPrice`, `Discount`, `SalesAmount`, `TotalCost`, `Profit`, `Channel`, `PaymentMethod`, `OrderPriority` sütunlarını ehtiva edir.

## Layihənin Strukturu

```
products-visualization-bi/
│
├── data/                    # Fact və Dimension cədvəlləri (CSV)
│
├── reports/                 # Dashboard-un ekran görüntüləri
│   ├── Dashboard Dizaynı.png
│   ├── Hədəfəvvəlki dövrlə müqayisəli KPI xülasə kartlar.png
│   ├── Bir neçə vizual arasında bağlı interaktiv filtrslicer.png
│   └── Dataya uyğun seçilmiş 4+ fərqli qrafik.png
│
├── products dashboard.pbix  # Hazır Power BI dashboard faylı
└── README.md
```

## İstifadə Olunan Texnologiya

- Power BI Desktop

## Dashboard-un Xüsusiyyətləri

- **KPI xülasə kartı** — ümumi satış məbləği (Total Sales) və hədəflə (Target Sales Amount) müqayisə göstəricisi
- **Time-series qrafik** — ay üzrə ümumi satışın dinamikası
- **Kateqoriya üzrə bar chart** — Clothing, Accessories, Electronics, Kitchen, Furniture, Outdoors kateqoriyaları üzrə ümumi satış
- **Donut chart** — cins üzrə satış bölgüsü
- **Coğrafi xəritə** — ölkə/region üzrə TotalCost göstəricisi
- **Slicer-lər** — Region və Year üzrə filtrasiya, bütün vizuallar arasında qarşılıqlı əlaqəli (cross-filter)

## Necə Açmaq

1. `products dashboard.pbix` faylını Power BI Desktop ilə açın
2. Data mənbələri `data/` qovluğundakı CSV fayllara işarə edir — repo-nu lokal kompüterə klonlayıb açdıqdan sonra lazım gələrsə data mənbəyi yolunu (Transform Data → Data Source Settings) öz mühitinizə uyğun yeniləyin
3. Dashboard-dakı Region/Year slicer-ləri vasitəsilə vizualları interaktiv filtrləyə bilərsiniz
