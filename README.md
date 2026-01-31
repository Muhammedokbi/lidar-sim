Harika, haklısın. Bir önceki LiDAR örneğindeki gibi **Proje Klasör Yapısı**nı ekleyerek ve görsellerin/videoların nerede durduğunu netleştirerek çok daha profesyonel bir yapı hazırladım.

Aşağıdaki metni kopyalayıp `README.md` dosyana yapıştırabilirsin.

```markdown
# 🚗 Autoware ve AWSIM Otonom Sürüş Simülasyonu

Bu proje, Unity tabanlı **AWSIM** simülatörü ile **Autoware** otonom sürüş yazılımının entegrasyonunu, kurulumunu ve temel kullanımını kapsar.

> ⚠️ **Uyarı:** Bu belgedeki bilgiler, yazılım sürümleri (Unity, ROS 2, Autoware) güncellendikçe değişiklik gösterebilir.

---

## 📂 Proje ve Dosya Yapısı

Görsellerin, haritaların ve çalıştırılabilir dosyaların konumu aşağıdaki gibi düzenlenmiştir:

```text
HOME_DIR (~)/
├── Downloads/
│   ├── AWSIM-Demo/                # Simülasyon uygulaması
│   │   └── AWSIM-Demo.x86_64
│   └── Shinjuku-Map/              # Harita verileri
│       └── map/                   # Pointcloud ve Lanelet2 haritaları
├── autoware/                      # Autoware çalışma alanı (workspace)
└── dokumantasyon/                 # README görselleri ve videoları
    ├── awsimgoruntusu.png
    ├── autowareaçilmaani.png
    ├── ikisininayniekrandaolduguan.png
    ├── hepsi.png
    ├── tools/
    │   ├── 2DPoseEstimate.png
    │   ├── 2DGoalPose.png
    │   ├── serVelocitlimit.png
    │   ├── stop.png
    │   └── Auto.png
    └── gittigianvideosu.mp4

```

---

## 1️⃣ AWSIM (Simülasyon Ortamı)

AWSIM, Unity tabanlı olup gerçek hayata ve özellikle **Robotaksi** senaryolarına en uygun simülasyon ortamını sunar. Açık kaynak yapısı sayesinde içeriği gelecekte değiştirilebilir.

### Başlatma Komutu

```bash
cd ~/Downloads/AWSIM-Demo
./AWSIM-Demo.x86_64

```

---

## 2️⃣ Autoware (Otonom Sürüş Yazılımı)

Autoware, aracı otonom sürüşe hazır hale getiren yazılımdır. Kurulumu karmaşık olsa da, sistemin kurulu olduğu varsayılarak başlatma işlemi aşağıdadır.

> 📌 **Not:** Harita yolu (Map Path) sisteminizdeki indirilmiş harita konumuna göre düzenlenmelidir.

### Başlatma Komutu

```bash
cd ~/autoware
source install/setup.bash
ros2 launch autoware_launch e2e_simulator.launch.xml vehicle_model:=sample_vehicle sensor_model:=awsim_sensor_kit map_path:=/home/lagaca/Downloads/Shinjuku-Map/map

```

---

## 3️⃣ Entegrasyon ve Haberleşme

Autoware ve AWSIM'in **iki ayrı terminalde** açılması gerekir. Açıldıkları andan itibaren **ROS 2** üzerinden otomatik olarak haberleşirler.

---

## 4️⃣ RViz Kullanımı ve Kontrol Panelleri

Araç kontrolü için RViz üzerindeki araçlar ve panellerin anlamları aşağıdadır:

### 📍 Üst Panel Araçları (Tools)

| Simge | Araç Adı | Açıklama |
| --- | --- | --- |
|  | **2D Pose Estimate** | Aracın haritadaki **başlangıç konumunu** eşleştirmek için kullanılır. |
|  | **2D Goal Pose** | Aracın gitmesini istediğiniz **hedef noktayı** belirler. |

### 🎛️ Autoware State Panel (Durum Paneli)

Genellikle ekranın sol tarafında bulunur.

| Simge | Durum | İşlev |
| --- | --- | --- |
|  | **Velocity Limit** | Aracın şehir içi maksimum hız limitini ayarlar. |
|  | **Stop** | Başlangıçta seçilidir. Aracın durduğunu belirtir. |
|  | **Auto** | Aracı **otonom moda** alır ve rotayı takip etmesini sağlar. |

---

## 5️⃣ Sonuç ve Demo

Tüm sistemlerin (Simülasyon + Autoware + Görselleştirme) aynı anda çalıştığı genel görünüm:

### 🎥 Otonom Sürüş Testi

Sistemin çalıştığını ve aracın rotayı takip ettiğini gösteren video:

[▶️ Test Videosunu İzle](https://www.google.com/search?q=dokumantasyon/gittigianvideosu.mp4)

```

```
