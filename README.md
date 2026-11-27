# Estimasi Klorofil-a Perairan Segara Anakan, Cilacap

Tugas UAS Sistem Informasi Geografi, Opsi B (Ecological Layer). Repository ini berisi notebook, data hasil, dan peta untuk estimasi klorofil-a dari citra Sentinel-2 di Google Earth Engine.

## Isi repository

- `UAS_SIG_Chla_SegaraAnakan.ipynb`: versi 1, perbandingan Februari dan Agustus 2025.
- `UAS_SIG_Chla_SegaraAnakan_v2.ipynb`: versi 2, komposit musiman 2023-2025 dengan zona laguna.
- `peta_chla_segara_anakan.png`, `grafik_chla_bulanan.png`, `chla_bulanan.csv`: hasil versi 1.
- `peta_chla_musiman_v2.png`, `grafik_chla_bulanan_v2.png`, `statistik_musiman.csv`, `chla_bulanan_laguna_2023_2025.csv`: hasil versi 2.
- File `.tif`: raster estimasi klorofil-a (EPSG:4326).

## Metode

Citra yang dipakai adalah Sentinel-2 SR Harmonized (`COPERNICUS/S2_SR_HARMONIZED`). Awan dibuang dengan band SCL, dan badan air dipisahkan dengan NDWI di atas 0,1. Klorofil-a diestimasi dari NDCI = (B5 - B4) / (B5 + B4) dengan persamaan Mishra dan Mishra (2012): Chl-a = 14,039 + 86,115 NDCI + 194,325 NDCI². Hasilnya dikomposit dengan median per bulan (versi 1) atau per musim (versi 2), lalu dipetakan dan dihitung statistiknya dengan Python.

## Menjalankan notebook

1. Buka notebook di Google Colab.
2. Isi `PROJECT_ID` di sel parameter dengan Project ID Google Cloud yang sudah terdaftar di Earth Engine.
3. Jalankan semua sel dari atas dan login saat `ee.Authenticate()` meminta.

## Keterbatasan

Persamaan klorofil-a belum divalidasi dengan data lapangan Segara Anakan, jadi hasilnya adalah estimasi relatif. Jumlah scene per bulan sedikit karena tutupan awan, terutama di musim hujan. Nilai di perairan terbuka kemungkinan terlalu tinggi karena NDCI dibuat untuk perairan keruh.

## Anggota

Aldhi Syahrul Syabani
Relita Anindya Maulida
Fakhriza Alwi A
