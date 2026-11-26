# Estimasi Klorofil-a Perairan Segara Anakan, Cilacap (Sentinel-2 + Google Earth Engine)

Tugas UAS Sistem Informasi Geografi — Opsi B (Ecological Layer).

## Isi repository

| File | Keterangan |
|---|---|
| `UAS_SIG_Chla_SegaraAnakan.ipynb` | Notebook Colab (script GEE + Python) beserta outputnya |
| `peta_chla_segara_anakan.png` | Layout peta resolusi tinggi (Februari vs Agustus 2025) |
| `grafik_chla_bulanan.png` | Grafik rata-rata Chl-a bulanan 2025 |
| `chla_bulanan.csv` | Tabel rata-rata Chl-a dan jumlah scene per bulan |
| `chla_2025_02.tif`, `chla_2025_08.tif` | Raster hasil estimasi Chl-a (EPSG:4326, 20 m) |

## Metode singkat

1. Sentinel-2 SR Harmonized (`COPERNICUS/S2_SR_HARMONIZED`) di Google Earth Engine.
2. Masking awan dengan band SCL, masking badan air dengan NDWI > 0,1.
3. NDCI = (B5 − B4) / (B5 + B4), lalu Chl-a = 14,039 + 86,115·NDCI + 194,325·NDCI² (Mishra & Mishra, 2012).
4. Komposit median bulanan, peta, dan statistik dengan Python (geemap, rasterio, matplotlib).

## Cara menjalankan

1. Buka notebook di Google Colab.
2. Isi `PROJECT_ID` pada sel parameter dengan Project ID Google Cloud yang terdaftar di Earth Engine.
3. Jalankan semua sel dari atas ke bawah dan login saat diminta `ee.Authenticate()`.

## Catatan keterbatasan

- Persamaan Chl-a belum divalidasi dengan data lapangan Segara Anakan; hasil adalah estimasi relatif.
- Jumlah scene per bulan sedikit (1–5) akibat tutupan awan; Februari hanya 1 scene.
- Nilai di laut terbuka kemungkinan terlalu tinggi karena NDCI dirancang untuk perairan keruh.

## Anggota

Aldhi Syahrul Syabani
Relita Anindya Maulida
Fakhriza Alwi A
