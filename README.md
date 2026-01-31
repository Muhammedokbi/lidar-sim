Harika bir proje dokümantasyonu taslağı. Yazdıklarını, Markdown (`README.md`) formatına uygun, hatalardan arındırılmış, okunabilir ve profesyonel bir yapıya dönüştürdüm.

İçerikteki komutları ve dosya yollarını (özellikle `/home/lagaca/...` kısmını) belirttiğin gibi **aynen korudum**, sadece anlatım bozukluklarını ve yazım yanlışlarını düzelttim.

Aşağıdaki kodu kopyalayıp `README.md` dosyanın içine yapıştırabilirsin.

```markdown
# Autoware ve AWSIM Kurulum ve Kullanım Rehberi

> **Uyarı:** Bu belgedeki bilgiler ve komutlar zamanla güncelleme alabilir ve değişiklik gösterebilir.

## 1. AWSIM (Simülasyon Ortamı)

AWSIM, Unity tabanlı bir simülasyon uygulamasıdır. Gerçek hayata ve özellikle Robotaksi senaryolarına en uygun simülasyon ortamını sunar. İçeriği gelecekte Unity üzerinden rahatça değiştirilebilir.

![AWSIM Görüntüsü](awsimgoruntusu.png)

Kurulumu kolaydır ve yeterince dokümantasyonu bulunmaktadır. Çalıştırmak için aşağıdaki komutları kullanabilirsiniz:

```bash
cd ~/Downloads/AWSIM-Demo
./AWSIM-Demo.x86_64

```

---

## 2. Autoware (Otonom Sürüş Yazılımı)

Autoware, aracı otonom sürüşe en uygun hale getiren yazılımdır. Birden çok ayar dosyası ile desteklenir. Kurulumu ve derlenmesi karmaşık olabilir; ancak kurulumun tamamlandığını varsayarak çalıştırma aşamasına geçiyoruz.

Haritanın (Map) Google üzerinden AWSIM'e uygun olarak indirilmiş olması gerekir. (Bu örnekte Shinjuku şehir haritası kullanılmıştır).

Çalıştırmak için aşağıdaki komutları kullanın:

```bash
cd ~/autoware
source install/setup.bash
ros2 launch autoware_launch e2e_simulator.launch.xml vehicle_model:=sample_vehicle sensor_model:=awsim_sensor_kit map_path:=/home/lagaca/Downloads/Shinjuku-Map/map

```

---

## 3. Sistemin Başlatılması ve Haberleşme

Autoware ve AWSIM'in **ayrı terminallerde** açılması gerekir. Açıldıkları andan itibaren birbirleriyle **ROS2** üzerinden haberleşmeye başlarlar.

### Araçlar ve Paneller (Tools)

Üst panelde bulunan araçların açıklamaları aşağıdadır:

**2D Pose Estimate**
Aracın harita üzerindeki mevcut konumunu ayarlamanızı sağlar.

**2D Goal Pose**
Aracın gitmesini istediğiniz hedef konumu (rotayı) belirlemenizi sağlar.

### Autoware State Panel (Durum Paneli)

Bu panel genellikle ekranın sol tarafında bulunur. Aracın manuel mi yoksa otonom modda mı olduğunu gösterir. Bizim için önemli olan 3 kısım vardır:

1. **Set Velocity Limit:** Aracın şehir içi hız sınırını ayarlamanızı sağlar.
2. **Stop:** Başlangıçta seçili olarak gelir, aracın durduğunu belirtir.
3. **Auto:** Aracı otonom moda alır ve belirlenen rotaya uygun gitmesini sağlar.

---

## 4. Genel Görünüm ve Test

Tüm sistemlerin aynı ekranda çalıştığı an:

**Otonom Sürüş Test Videosu:**
Aracın rotada ilerlediği anın videosunu aşağıdan izleyebilirsiniz:

[Otonom Sürüş Videosu](https://www.google.com/search?q=gittigianvideosu.mp4)

```

### Yaptığım Düzeltmelerin Özeti:
* **Yazım Hataları:** "simalson" -> "simülasyon", "tapanli" -> "tabanlı", "otonom", "fakan" -> "fakat" gibi kelime hataları düzeltildi.
* **Anlatım:** Cümleler daha akıcı ve anlaşılır hale getirildi ("sana nasıl açılacağını söylüyorum" yerine daha genel bir dil kullanıldı).
* **Format:** Başlıklar (`#`, `##`), kod blokları (` ```bash `) ve resim etiketleri (`![Açıklama](dosya.png)`) Markdown standartlarına uygun hale getirildi.
* **İçerik:** Verdiğin dosya yolları (path) ve dosya isimleri değiştirilmedi.

```
