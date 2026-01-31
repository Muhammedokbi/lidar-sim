# Autoware ve AWSIM Kullanım Rehberi

> **Uyarı:** Bu içerik yazılım güncellemelerine bağlı olarak zamanla değişiklik gösterebilir.


## Proje Klasör Yapısı

```text
YAPTIM/
├─ goruntuler         # README'de kullanılan görseller
│   ├─ rviz.png
│   ├─ kiss_icp.png
│   ├─ kiss_icp_1.png
│   ├─ cloudcompare.png
│   ├─ makas.png
│   ├─ onay.png
│   ├─ ornek.png
│   ├─ ciktiDosyalar.png
│   ├─ rviz_harita.png
│   ├─ rviz_harita_yok.png
│   └─ rviz_harita_var.png
└─ README.md
```

## 1. AWSIM Nedir?

AWSIM, Unity tabanlı bir simülasyon uygulamasıdır. Gerçek hayat senaryolarına ve **Robotaksi** konseptine en uygun simülasyon ortamını sunar. Esnek yapısı sayesinde gelecekte içeriği kolayca değiştirilebilir veya geliştirilebilir.

**Başlatma Komutları:**
Terminal üzerinden şu komutlarla çalıştırılır:

```bash
cd ~/Downloads/AWSIM-Demo
./AWSIM-Demo.x86_64

```

*Kurulumu kolaydır ve yeterli dokümantasyona sahiptir.*

---

## 2. Autoware Nedir?

Autoware, aracı otonom sürüşe en uygun hale getiren açık kaynaklı bir yazılımdır. Birçok ayar dosyası ve modül ile desteklenir. Kurulumu ve derlenmesi zahmetli olsa da, hazır bir sistemde şu şekilde başlatılır:

**Başlatma Komutları:**

```bash
cd ~/autoware
source install/setup.bash
ros2 launch autoware_launch e2e_simulator.launch.xml vehicle_model:=sample_vehicle sensor_model:=awsim_sensor_kit map_path:=/home/lagaca/Downloads/Shinjuku-Map/map

```

*Not: Haritanın AWSIM ile uyumlu olarak indirilmiş olması gerekir (Örn: Shinjuku haritası).*

---

## 3. Haberleşme ve Kontrol

İki uygulama ayrı terminallerde açılmalıdır. Açıldıkları andan itibaren birbirleriyle **ROS 2 (Robot Operating System)** protokolü üzerinden haberleşirler.

### Üst Panel Araçları (Tools)

* **2D Pose Estimate:** Aracın harita üzerindeki başlangıç konumunu ayarlamanızı sağlar.
* **2D Goal Pose:** Aracın gitmesini istediğiniz hedef noktayı (rota sonu) belirler.

### Autoware State Panel

Genellikle ekranın solunda bulunur ve aracın durumunu (manuel/otonom) gösterir. En önemli kontroller şunlardır:

* **Set Velocity Limit:** Aracın şehir içi hız sınırını belirlemenizi sağlar.
* **Stop:** Başlangıçta seçili gelir, aracı durur halde tutar.
* **Auto:** Aracın otonom modda, belirlenen rotaya uygun şekilde gitmesini sağlar.

---
