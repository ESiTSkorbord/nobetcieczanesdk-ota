# nobetcieczanesdk-ota

Nobetci Eczane panellerinin uzaktan yazilim guncellemesi (OTA) dosyalari.
Her panel boyunun KENDI sürüm dosyasi ve KENDI yazilim (.bin) dosyasi vardir; boylar birbirine karismaz.

| Panel boyu | Sürüm dosyasi       | Yazilim dosyasi              | Sürüm etiketi |
|------------|---------------------|------------------------------|---------------|
| Kucuk      | `versiyon_kb.txt`   | `nobetcieczanesdk_kb.bin`    | `KB_01`, `KB_02` ... |
| Orta       | `versiyon_ob.txt`   | `nobetcieczanesdk_ob.bin`    | `OB_01`, `OB_02` ... |
| (Buyuk)    | `versiyon_bb.txt`   | `nobetcieczanesdk_bb.bin`    | `BB_01` ... (gerekince) |

`versiyon.txt` + `nobetcieczanesdk.bin` (eski, adi ayrilmamis) SADECE eski `v10_10` yazilimli kucuk
paneller icindir (ilk gecis). Bu panellerin hepsi KB_xx'e gectikten sonra silinebilir.

## Yeni surum yayinlama (HER boy icin ayri)
1. `NobetciEczaneSDK_ana*.ino` icinde `PANEL_BOY` satirini ayarla (0 = kucuk, 1 = orta).
2. Arduino IDE: Sketch -> Export Compiled Binary. Cikan `.ino.bin` dosyasini al.
3. Bu depoya o boyun `.bin` dosyasini AYNI ADLA yukle (ustune yazar).
4. O boyun `versiyon_xx.txt` icerigini yeni etiket yap (orn. `KB_02`). Etiket, .ino'daki `OTA_VERSIYON`
   ile BIREBIR ayni olmali (kodda `BOY_KOD "_02"` olarak guncelle).
5. Panel uygulamadan "Guncelle" ile (ya da otomatik kontrolde) yeni surumu bulur.

Kural: bin ve versiyon dosyasi HER ZAMAN birlikte guncellenir; yanlis boyun .bin'i yanlis boyun
paneline yuklenirse panel goruntusu bozulur (GUID/yazi boyutlari farklidir).
