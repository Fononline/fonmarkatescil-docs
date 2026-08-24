# FonMarkaTescil — Kurulum ve Kullanım Kılavuzu

Bu kılavuz, **FonMarkaTescil** marka tescil başvuru yönetim modülünün WISECP panelinize kurulumunu, yapılandırılmasını ve gündelik kullanımını anlatır.

![Marka Tescil Tanıtım Görseli](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-tanitim.jpg)

---

## İçindekiler

1. [Genel Bakış](#genel-bakis)
2. [Kurulum](#kurulum)
3. [Admin Ayarları](#admin-ayarlari)
4. [Müşteri Deneyimi](#musteri-deneyimi)
5. [Sipariş Yönetimi](#siparis-yonetimi)
6. [FonPageBuilder ile Sayfa Zenginleştirme](#fonpagebuilder-ile-sayfa-zenginlestirme)
7. [Sık Sorulan Sorular](#sik-sorulan-sorular)

---

## 1. Genel Bakış <span id="genel-bakis"></span>

FonMarkaTescil, müşterilerinizin marka tescil başvurularını sizin WISECP panelinizden sipariş vermesini, belge yüklemesini ve sürecin her aşamasını takip etmesini sağlayan bir hizmet yönetim sistemidir. Modül, gerçek bir marka vekilliği hizmeti vermez — sizin (veya anlaştığınız bir marka vekilinin) TÜRKPATENT nezdinde yürüttüğü süreci, sipariş ve iletişim katmanı olarak müşteriye şeffaf bir şekilde yansıtır.

### Neden iki ayrı modül?

Paket, WISECP'in kendi mimarisine uygun olarak **iki ayrı modülden** oluşur:

| Modül | Türü | Görevi |
|---|---|---|
| **FonMarkaTescil** | Ürün (Product) | Fiyatlandırma, sınıf ayarları, belge tanımları, sipariş/fatura yaşam döngüsü — **tek doğruluk kaynağı** |
| **FonMarkaTescilApp** | Eklenti (Addon) | Müşterinin gördüğü, temadan bağımsız herkese açık başvuru formu |

WISECP'te "ürün" (Product) modülleri kendi başına genel-erişimli bir sayfaya sahip olamaz — bu tür sayfalar yalnızca "eklenti" (Addon) modülleriyle sunulabilir. Bu yüzden başvuru formu ayrı bir eklenti modül olarak paketlenmiştir. **Tüm ayarlar (fiyat, sınıflar, belgeler, SEO adresi) yine de tek yerden, FonMarkaTescil'in kendi admin panelinden yönetilir** — FonMarkaTescilApp'in kendi ayar ekranı sadece sizi doğru yere yönlendiren bir bilgi notu içerir.

---

## 2. Kurulum <span id="kurulum"></span>

1. **Modül dosyalarını yükleyin.** Her iki modül klasörünü de WISECP kurulumunuza kopyalayın:
   - `coremio/modules/Product/FonMarkaTescil/`
   - `coremio/modules/Addons/FonMarkaTescilApp/`
2. **Ürün Grubu Oluşturun.** Yönetim Paneli →  Ürünler / Hizmetler → Ürün/Hizmet Yönetimi → Ürün / Hizmet Grubu Oluştur menüsüne tıklayın ve yeni bir hizmet grubu oluşturun. Başlık olarak istediğiniz bir başlığı verin (Örneğin: **Marka Tescil**) ve grubu kaydedin. Bu Ürün Grubu daha sonra modül ayarlarından seçilecektir.
3. **Ürün Oluşturun.** Yönetim Paneli →  Ürünler / Hizmetler menüsü altından 2. adımda oluşturduğunuz Ürün Hizmet Grubuna (Örneğin: **Marka Tescil**) ait menüye tıklayın. Açılan sayfada yeni bir ürün oluşturun. Bu Ürün daha sonra modül ayarlarından seçilecektir.
   - **Ürün Adı:** Ürün Adı olarak bir ad belirleyin. Örneğin **Marka Tescil Başvurusu**
   - **Otomasyon Ayarları:** Otomasyon Ayarları sekmesinde **Modül** olarak **Marka Tescil Modülü** modülünü seçiniz. **Otomatik Kurulum** seçeneğini işaretlemeyin.
   - **Fiyatlandırma:** Fiyatlandırma sekmesine geçin ve **Tek Sefer** döngüsüne sahip tek bir fiyat oluşturun ve **Tutar** olarak **0** (sıfır) girin.
4. **FonMarkaTescilApp Modülünü Etkinleştirin.** Yönetim Paneli → Araçlar → Eklentiler menüsüne tıklayın ve **Marka Tescil (Başvuru Sayfası)** (Eklenti) için "Aktifleştir" işlemini yapın. 
5. **FonMarkaTescil Modülünü Yapılandırın.** Yönetim paneli → Ürünler / Hizmetler → Ürün/Hizmet Yönetimi → Ürün / Hizmet Api Yönetimi menüsünü tıklayın ve buradaki **Diğer** bölümündeki ** Yönet** düğmesine tıklayın. **Tüm Modüller** sekmesine tıklayarak **Marka Tescil Modülü** modülünü bularak tıklayın ve modülün yapılandırma ekranını açın.
6. Devam etmeden önce [Admin Ayarları](#admin-ayarlari) bölümündeki adımları sırasıyla tamamlayın.


### Gereksinimler

- Aktif bir WISECP kurulumu (3.1.9.8.2 veya üzeri)
- PHP `curl` ve `openssl` uzantıları
- ionCube Loader (v14 veya üzeri) — WISECP'in kendi gereksinimi
- Sunucunuzun `fononline.net` adresine giden HTTPS bağlantılarına izin vermesi

---

## 3. Admin Ayarları <span id="admin-ayarlari"></span>

Tüm yapılandırma, yönetim paneli → Ürünler → **FonMarkaTescil** üzerinden, aşağıdaki sekmelerle yapılır.

### Genel Ayarlar <span id="genel-ayarlar"></span>
![Genel Ayarlar](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-genel-ayarlar.jpg)

- **Widget Başlığı**: Başvuru formunun üstünde görünecek başlık metni (çok dilli).
- **Alt Başlık / Açıklama**: Başvuru formunun üstünde görünecek açıklama metni (çok dilli).
- **Ön Bilgilendirme Metni**: Başvuru formunun altında görünecek bilgilendirme metni (çok dilli). Boş bırakılırsa formun altında hiçbir metin gösterilmez.
- **Buton Metni**: Formdaki "sepete ekle" butonunun metni (çok dilli).
- **Bağlı Ürün ve Kategori**: Başvuru formunun (Addon sayfası) hangi ürüne sepete eklerken bağlanacağı ve bu ürünün hangi kategoride (ürün grubu) yer aldığı burada seçilir.
  - **Bağlı Ürün**: Müşterinin sipariş sırasında fiilen satın alacağı WISECP ürününü seçin (fatura ve ödeme bu ürün üzerinden işler). Bu ürünü **2. Kurulum** talimatlarındaki **3. adımda** oluşturmuş olmalısınız.
  - **Bağlı Ürün Grubu (Kategori)**: Müşterinin sipariş sırasında fiilen satın alacağı WISECP ürününün ait olduğu kategoriyi seçin (SEO Ayarları sekmesinde bu kategorinin adresini başvuru formuna yönlendiren .htaccess kodu üretmek için kullanılır.). Bu ürüngrubunu **2. Kurulum** talimatlarındaki **2. adımda** oluşturmuş olmalısınız.
- **Görünüm Ayarları**: Başvuru formundaki düğme, kenarlık ve seçili sınıf renklerini özelleştirin.
  - **Genel Vurgu Rengi**: Düğmeler, aktif filtreler ve odaklanmış giriş alanları için kullanılır.
  - **Mal Sınıfları Rengi**: Mal (1–34) sınıflarının rozeti, seçili satır kenarlığı ve arkaplanı için kullanılır.
  - **Hizmet Sınıfları Rengi**: Hizmet (35–45) sınıflarının rozeti, seçili satır kenarlığı ve arkaplanı için kullanılır.
  - **Kenarlık Kullan**: Başvuru formu listeleme ve özet kartlarında kenarlık kullanmak istiyorsanız etkinleştirin.
  - **Gölge Kullan**: Başvuru formu listeleme ve özet kartlarında gölge kullanmak istiyorsanız etkinleştirin.

---

### Fiyat Ayarları <span id="fiyat-ayarlari"></span>
![Fiyatlandırma Ayarlar](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-fiyat-ayarlari.jpg)

Fiyatlar aylık değil, başvuru başına ücrettir. TÜRKPATENT resmi harç tutarları her yıl güncellenmektedir. Marka sınıfı seçimine göre kademeli ücretlendirme burada tanımlanır:

- **Kurum Harcı (Tek Sınıf)**: Tek bir sınıf için geçerli kurum karcı ücretidir. Ek sınıflar için ayrıca ücretlendirme yapılır. Baz ücret olarak bu tutar kullanılır.
- **Kurum Harcı (Ek Sınıf)**: İlk sınıf sonrasında seçilen her ek sınıf için eklenecek tutar. Kurum harcı baz ücreti ile aynı ücret olabilir veya farklı olabilir.
- **Hizmet Bedeli (Tek Sınıf)**: Tek bir sınıf için geçerli hizmet bedeli ücretidir. Ek sınıflar için ayrıca ücretlendirme yapılır. Hizmet bedeli baz ücret olarak bu tutar kullanılır.
- **Hizmet Bedeli (Ek Sınıf)**: İlk sınıf sonrasında seçilen her ek sınıf için eklenecek hizmet tutarıdır. Hizmet bedeli baz ücreti ile aynı ücret olabilir veya farklı olabilir.

> ⚠️ Fatura tutarı doğrudan **seçilen sınıf sayısına** göre hesaplanır. Bu yüzden bir sipariş oluşturulduktan sonra sınıf *sayısının* değiştirilmesine sistem tarafından izin verilmez (bkz. [Sipariş Yönetimi](#siparis-yonetimi)).

#### Kampanya Fiyatları (Sınıf Sayısına Özel)

Aynı sekmede, belirli bir sınıf sayısı için yukarıdaki baz+ek sınıf formülü yerine kullanılacak **sabit bir fiyat** tanımlayabilirsiniz (örn. "kampanya kapsamında 3 sınıf için özel fiyat"). Bunun için "Kampanya Fiyatı Ekle" ile yeni bir satır açıp sınıf sayısını, kurum harcını ve hizmet bedelini girmeniz yeterli.

> ⚠️ **Önemli:** Girdiğiniz kurum harcı ve hizmet bedeli, **sınıf başına değil**, seçilen sınıf sayısının **tamamı için geçerli toplam tutardır**. Örneğin "3 sınıf için Kurum Harcı: 1000" girerseniz, müşteri 3 sınıf seçtiğinde Kurum Harcı olarak toplamda 1.000 TL gösterilir (3.000 TL değil).
>
> Aynı sınıf sayısı için birden fazla satır girerseniz sonuncusu geçerli olur. Bir sınıf sayısı için kampanya tanımlı değilse, o sınıf sayısında normal baz+ek sınıf formülü kullanılmaya devam eder.

Tanımladığınız kampanyalar, başvuru formunda müşteriye de otomatik olarak gösterilir — bkz. [Müşteri Deneyimi](#musteri-deneyimi).

---

### Marka Sınıfları (Nice Sınıflandırması) <span id="marka-siniflari"></span>
![Marka Tescil Sınıfları](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-sinif-ayarlari.jpg)

Nice Sınıflandırması'nın 45 sınıfının tamamı sistemde hazır tanımlıdır. Bu sekmeden **hangi sınıfların** müşterilere sunulacağını (aktif/pasif) seçersiniz. Yalnızca burada aktif işaretlenen sınıflar başvuru formunda ve admin düzenleme ekranında seçilebilir olur.

- **Özel Notlar**: Her sınıf için, müşteriye başvuru formunda gösterilecek kısa bir açıklama notu girebilirsiniz (örn. "Bu sınıf, giyim ve aksesuar ürünlerini kapsar"). Boş bırakılırsa hiçbir not gösterilmez.

---

### Örnek Belgeler <span id="ornek-belgeler"></span>
![Gerekli Örnek Belgeler](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-belge-ayarlari.jpg)

Başvuru için müşteriden istenecek belgeleri (örn. vekaletname) burada tanımlarsınız — her belge için ad ve bir FontAwesome simgesi (örn. `fa-regular fa-file-lines`) girilir. Müşteri panelinde bu tanımlara göre yükleme alanları otomatik oluşur.
- **Yeni Belge Ekle**: Yeni bir belge tanımı ekler.
- **Belge Simgesi**: FontAwesome 6.4.2 sürümünden bir simge seçin (örn. `fa-regular fa-file-lines`).
- **Belge Adı**: Müşteriye gösterilecek belge adı (çok dilli).
- **Dosya**: Müşterinin yüklemesi gereken örnek dosya (PDF, DOCX vb.) — boş bırakılırsa örnek dosya gösterilmez. Bu dosya müşteri tarafından indirilir, taranır, imzalanıp kaşelenir ve sipariş sonrası hizmet detayından tekrar yüklenir.

---

### SEO Ayarları <span id="seo-ayarlari"></span>
![SEO Ayarları](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-seo-ayarlari.jpg)

Başvuru formunun her dil için görüneceği **SEO dostu adresi** burada belirlersiniz (örn. Türkçe için `marka-tescili`, İngilizce için `trademark-application`). Slug'ları girip kaydettiğinizde, sayfa aşağıda sizin için hazır bir `.htaccess` kod bloğu üretir.

**Bu kodu, sitenizin kök dizinindeki `.htaccess` dosyasına eklemeniz gerekir** — kılavuzdaki talimata göre, dosyanın `RewriteCond %{REQUEST_FILENAME} !-d` ile başlayan genel koşul bloğunun **hemen öncesine**. Yanlış yere eklenirse sitenizdeki görsel/dosya adresleri (özellikle admin panelinde) bozulabilir, bu adımı dikkatle uygulayın.

Bağlı bir ürün grubu (kategori) seçtiyseniz, o kategori adresine gelen ziyaretçileri de başvuru formuna yönlendiren ek bir kod bloğu ayrıca üretilir.

---

## 4. Müşteri Deneyimi <span id="musteri-deneyimi"></span>

Müşterileriniz başvuru formuna iki şekilde ulaşabilir:

- **Native adres**: yukarıda tanımladığınız SEO slug'ı (örn. `siteniz.com/marka-tescili`).
- **FonPageBuilder sayfası**: aynı formu, kendi tasarladığınız zengin bir sayfaya widget olarak gömebilirsiniz — bkz. [FonPageBuilder ile Sayfa Zenginleştirme](#fonpagebuilder-ile-sayfa-zenginlestirme).

Form üzerinde müşteri marka adını yazar, sınıflarını seçer (ücret anlık hesaplanır) ve sepete ekler. Tanımlı kampanya fiyatlarınız varsa (bkz. [Admin Ayarları → Fiyat](#fiyat-ayarlari)), formun altında müşteriye bunları gösteren bir "Kampanyalı Fiyatlar" şeridi otomatik olarak görünür — ayrıca bir işlem yapmanız gerekmez.

![Kapanyalı Fiyat Bildirimi](https://fonwise.com/addons/wisecp-marka-tescil/modul-kampanyali-fiyat-bildirim.jpg)

Sipariş tamamlandıktan sonra müşteri, kendi panelinden (Siparişlerim) sürecin tamamını takip eder:

![Süreç Takip](https://fonwise.com/addons/wisecp-marka-tescil/modul-surec-takip.jpg)

1. **Başvuru Alındı** — sipariş oluşturulduğu an.
2. **TÜRKPATENT'e Başvuru Yapıldı** — siz başvuru numarasını girdiğinizde.
3. **İnceleme Sürecinde** — otomatik ara aşama, herhangi bir işlem gerekmez.
4. **Sonuçlandı** — siz sonucu (tescil/ret/itiraz) işlediğinizde.

Aynı ekrandan müşteri, tanımladığınız belgeleri de yükleyip durumlarını (beklemede/onaylandı/reddedildi) görebilir.

---

## 5. Sipariş Yönetimi <span id="siparis-yonetimi"></span>

Bir siparişin detay sayfasında (Siparişler → ilgili sipariş → **Otomasyon Ayarları** sekmesi) şu araçlar bulunur:

![Sipariş Yönetimi](https://fonwise.com/addons/wisecp-marka-tescil/marka-tescil-siparis-otomasyon.jpg)

### Marka Adı / Sınıf Düzeltme

Müşteri, TÜRKPATENT'e başvuru yapılmadan **önce** yanlış marka adı veya sınıf bildirdiğini size iletirse, bu alandan düzeltebilirsiniz:

- **TÜRKPATENT Başvuru No** alanı boş olduğu sürece marka adı ve sınıflar düzenlenebilir.
- Başvuru numarasını girdiğiniz an bu alanlar **kalıcı olarak kilitlenir** — marka, hukuken başvurusu yapıldıktan sonra değiştirilemez; bir sonraki ihtiyaçta müşterinin yeni bir sipariş vermesi gerekir.
- **Sınıf sayısı değiştirilemez** — yalnızca *hangi* sınıfların seçili olduğunu değiştirebilirsiniz, seçili sınıf *adedini* değil (fatura tutarı sınıf sayısına göre hesaplandığından).


### Belge Onay/Red

Müşterinin yüklediği her belge burada listelenir; **Onayla**/**Reddet** butonlarıyla durumunu güncelleyebilirsiniz. Bu, müşteri panelindeki belge durumuna anında yansır.

### TÜRKPATENT Başvuru No

Başvuruyu resmi kuruma ilettiğinizde, başvuru numarasını buraya girip kaydedin. Bu, hem ilerleme çubuğunun 2. aşamasını tamamlar hem de marka adı/sınıf alanlarını kilitler.

### Sonuç Bilgisi

Süreç sonuçlandığında (Tescil Edildi / Reddedildi / İtiraz Edildi / Diğer) sonucu ve isterseniz bir açıklama notu girip kaydedin — müşteri panelindeki 4. aşama bu bilgiyle güncellenir.

---

## 6. FonPageBuilder ile Sayfa Zenginleştirme <span id="fonpagebuilder-ile-sayfa-zenginlestirme"></span>

Sitenizde **FonPageBuilder** kuruluysa, başvuru formunu tek başına bir sayfaya hapsetmek zorunda değilsiniz. Sayfa oluşturucudaki widget listesinde **"Marka Tescil Başvuru Formu"** adlı bir bileşen görürsünüz (yalnızca FonMarkaTescil modülü kurulu ve aktifken listede görünür) — bu widget'ı, üstüne bir tanıtım (hero) bölümü, altına detaylı bilgilendirme ekleyebileceğiniz herhangi bir sayfaya sürükleyip bırakabilirsiniz. Widget'ın kendine ait bir ayarı yoktur; formun kendisi (başlık, buton metni, sınıflar vb.) yine FonMarkaTescil'in kendi admin ayarlarından yönetilmeye devam eder.

### ⚠️ Önemli: aynı adresi iki kez kullanmayın

FonMarkaTescilApp'in kendisinin, [SEO sekmesinde](#seo-ayarlari) tanımladığınız sabit bir adresi vardır. FonPageBuilder ile **yeni bir özel sayfa** oluşturursanız, bu sayfa da kendi girdiğiniz slug'a sahip ayrı bir fiziksel sayfa olarak oluşur.

**Bu iki özelliği aynı adreste birlikte kullanmayın** — yani FonPageBuilder sayfanıza, FonMarkaTescil'in SEO ayarlarında zaten tanımlı olan slug'ın **aynısını** vermeyin. Aksi halde `.htaccess` yönlendirmesi FonPageBuilder sayfanızı gölgeler ve o sayfa hiçbir zaman gösterilmez.

Doğru kullanım şu iki yoldan biridir:

1. **Sadece native adresi kullanın** — FonPageBuilder ile ayrı bir sayfa oluşturmayın, SEO sekmesindeki adres yeterli.
2. **Sadece FonPageBuilder sayfasını kullanın** — bu durumda [SEO sekmesindeki](#seo-ayarlari) slug alanlarını **hiç doldurmanıza ve `.htaccess`'e o kodu eklemenize gerek yoktur** — asıl müşteriye göstereceğiniz/menüden link vereceğiniz adres, FonPageBuilder ile oluşturduğunuz, kendi slug'ına sahip sayfa olsun.

Her iki adresi de bilinçli olarak canlı tutmak isterseniz (örn. eski bir bağlantı için), menü ve iç bağlantılarınızı her zaman zenginleştirilmiş (FonPageBuilder) sayfaya verin; native sayfayı hiçbir yerden link vermeden bırakın.

#### Bağlı ürün grubu (kategori) yönlendirmesi kullanıyorsanız

SEO sekmesinde bir ürün grubunu (kategoriyi) bu modüle bağladıysanız, sayfa aynı zamanda o kategori adresine gelen ziyaretçileri **native slug'a** yönlendiren ek bir `.htaccess` kodu da üretir (bkz. [SEO sekmesi](#seo-ayarlari)).

**FonPageBuilder sayfasını kullanmayı seçtiyseniz, bu yönlendirme kodunun hedefini de değiştirmeniz gerekir** — kod, ziyaretçiyi artık kullanmadığınız native forma değil, FonPageBuilder ile oluşturduğunuz sayfanın slug'ına göndermelidir. Aksi halde kategori sayfasına gelen ziyaretçiler, zenginleştirilmiş sayfanız yerine hâlâ çıplak forma yönlendirilir.

---

## 7. Sık Sorulan Sorular

- **Müşteri sepete ekledikten sonra marka adını neden değiştiremiyorum?** Başvuru TÜRKPATENT'e fiilen yapıldıktan (başvuru numarası girildikten) sonra marka hukuken değiştirilemez. Bu durumda müşterinin yeni bir sipariş vermesi gerekir.

- **Sınıf sayısını sonradan artırabilir miyim?** Hayır — fatura tutarı sınıf sayısına göre hesaplandığından, mevcut bir siparişte sınıf sayısı değiştirilemez. Ek sınıf isteği yeni bir sipariş olarak ele alınmalıdır.

- **FonPageBuilder kurulu değilse ne olur?** Hiçbir şey değişmez — widget seçim listesinde görünmez, native SEO sayfası normal şekilde çalışmaya devam eder.
