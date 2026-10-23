# balikcilik_temali_bulmaca_oyunu
A. Sistem Gereksinimleri
1. Projenin Amacı ve Kapsamı (Scope)
Bu sistem hangi problemi çözüyor?
Sadece eğlenceye odaklanan oyunlar oyuncuya bir şey öğretmiyor. Klasik bilgi yarışmaları ise sürekli aynı
soru-cevap düzeninde ilerlediği için kısa sürede sıkıcı hale geliyor. Biz bu ikisini birleştiren, balık tutma
temalı bir bulmaca oyunu yapmaya karar verdik. Oyuncu oltasını attığında farklı nadirlikte bir balık ya da
eşya çıkıyor; onu kazanabilmek için de eşyanın nadirliğine göre zorlaşan bir genel kültür sorusunu doğru
cevaplaması gerekiyor. Böylece oyuncu hem eğleniyor hem de genel kültürünü geliştiriyor.
Sistem ne yapacak?
Zamanlamaya dayalı olta atma ve balık tutma mini oyunu sunacak.
Yakalanan balık ya da eşyanın nadirliğini 5 seviyeden (Yaygın, Sıra Dışı, Nadir, Epik, Efsanevi) rastgele
belirleyecek.
Nadirliğe uygun zorlukta, 4 şıklı ve süreli bir genel kültür sorusu getirecek.
Doğru cevapta puan, para ve eşya verecek; yanlış cevapta puan kesip doğru cevabı gösterecek.
Dükkânda olta, şapka, kıyafet ve pantolon satacak. Daha iyi olta, nadir eşya yakalama şansını
artıracak.
Envanterdeki eşyaları gösterecek ve oyuncunun eşya kuşanmasını sağlayacak.
Profil ekranında seviye, toplam puan, doğru cevap oranı ve yakalanan en nadir eşyayı gösterecek.
Oyuncunun ilerlemesini bilgisayara (yerel JSON dosyasına) kaydedecek.
Sistem ne yapmayacak? (Kapsam dışı)
Çok oyunculu (online) mod olmayacak, oyun tek oyunculu olacak.
Gerçek para ile oyun içi satın alma olmayacak.
Soru eklemek için web paneli ya da ayrı bir soru editörü olmayacak; sorular JSON dosyasından
okunacak.
Bulut kayıt ve kullanıcı hesabı olmayacak; tüm veriler oyuncunun bilgisayarında tutulacak.
Oyun sadece bilgisayar için yapılacak, mobil sürümü olmayacak.
2. Kullanıcı Profilleri / Aktörler
Aktör Açıklama
Oyuncu Oyunun tek kullanıcısıdır. Oltayı atar, soruları cevaplar, envanterine bakar, eşya kuşanır ve
dükkândan alışveriş yapar.
Oyun Sistemi Bir kişi değil, oyunun arka planda kendi başına yaptığı işlerdir. Rastgele nadirlik belirler, soru
havuzundan uygun soruyu seçer, cevabı kontrol eder, ödül ya da ceza uygular.
Oyunda giriş sistemi ve admin rolü yok. Oyun tek kişilik olduğu ve sorular dosyadan okunduğu için
bunlara gerek görmedik.
3. Fonksiyonel Gereksinimler
Persona: Oyunun hedef kullanıcısı; kısa aralarda oyun oynamayı seven ve oynarken genel kültürünü de
geliştirmek isteyen öğrenci ya da genç.
User story'leri 4 ana başlık (epic) altında topladık. Her story'nin yanına, o özelliğin tamamlanmış
sayılması için gereken kabul kriterlerini yazdık.
Epic 1: Balık Tutma
No User Story Kabul Kriterleri
1 Bir oyuncu olarak, oltamı denize atmak
istiyorum, böylece bir balık ya da eşya
yakalayabileyim.
"Başlat" butonuna basınca olta atılır. Zamanlamaya
göre balık ya da eşya suyun yüzeyine çıkar. Olta takılı
değilse atış yapılamaz.
2 Bir oyuncu olarak, yakaladığım şeyin nadirliğini
görmek istiyorum, böylece ne kadar değerli
olduğunu bileyim.
Nadirlik 5 seviyeden biri olarak rastgele belirlenir. Nadir
seviyelerin çıkma ihtimali daha düşüktür. Nadirlik
ekranda etiket olarak gösterilir.
Epic 2: Bilgi Yarışması
No User Story Kabul Kriterleri
3 Bir oyuncu olarak, yakaladığım eşyanın nadirliğine
göre soru almak istiyorum, böylece değerli eşyaları
hak ederek kazanayım.
Soru, eşyanın nadirlik seviyesindeki havuzdan
seçilir. Soru 4 şıklıdır ve süre sayacı başlar. Süre
dolarsa cevap yanlış sayılır.
4 Bir oyuncu olarak, doğru cevap verince ödül almak
istiyorum, böylece ilerleyebileyim.
Doğru cevapta eşya envantere eklenir. Nadirliğe
göre puan ve para verilir. Ekranda yeşil bir onay
mesajı görünür.
5 Bir oyuncu olarak, yanlış cevap verince doğrusunu
görmek istiyorum, böylece yeni bir şey öğreneyim.
Yanlış cevapta puan kesilir ve eşya verilmez. Doğru
şık kırmızı uyarıyla birlikte gösterilir.
Epic 3: Dükkân ve Envanter
No User Story Kabul Kriterleri
6 Bir oyuncu olarak, kazandığım parayla dükkândan
daha iyi olta almak istiyorum, böylece nadir eşya
yakalama şansım artsın.
Olta, şapka, kıyafet ve pantolon kategorileri
listelenir. Para yetmiyorsa satın alma yapılmaz. Yeni
olta alınınca şans çarpanı artar.
7 Bir oyuncu olarak, topladığım eşyaları görmek
istiyorum, böylece neler kazandığımı bileyim.
Envanterde eşyalar adı, nadirliği ve adediyle
listelenir. Aynı eşyadan birden fazla varsa adet artar.
8 Bir oyuncu olarak, aldığım eşyaları kuşanmak
istiyorum, böylece karakterimin görünümünü
değiştireyim.
Envanterden bir eşya seçilip kuşanılabilir. Aynı
türden önceki eşya çıkarılır. Karakterin görünümü
hemen değişir.
Epic 4: İlerleme ve Profil
No User Story Kabul Kriterleri
9 Bir oyuncu olarak, profilimde istatistiklerimi görmek
istiyorum, böylece ne kadar geliştiğimi göreyim.
Profilde kullanıcı adı, seviye, toplam puan, doğru
soru sayısı, doğru cevap yüzdesi ve en nadir eşya
gösterilir.
10 Bir oyuncu olarak, oyunu kapattığımda ilerlememin
kaybolmamasını istiyorum, böylece kaldığım yerden
devam edebileyim.
Puan, para, envanter ve istatistikler oyun
kapanırken JSON dosyasına kaydedilir. Oyun
açılınca bu bilgiler geri yüklenir.
4. Fonksiyonel Olmayan Gereksinimler
Performans: Oyun orta seviye bir bilgisayarda en az 60 FPS ile akıcı çalışacak. Soru yükleme ve sahne
geçişleri 1 saniyeden kısa sürecek.
Kullanılabilirlik: Soru ve şıklar yüksek kontrastlı renklerle ve okunaklı yazı boyutuyla gösterilecek.
Oyun tamamen fare ile oynanabilecek.
Veri kalıcılığı: Oyuncunun puanı, parası, eşyaları ve istatistikleri oyun kapanırken hatasız şekilde
yerel dosyaya yazılacak.
Genişletilebilirlik: Sorular kodun içine yazılmayacak, ayrı JSON dosyalarında tutulacak. Koda
dokunmadan yeni soru eklenebilecek.
Uyumluluk: Oyun Windows 10 ve üzeri bilgisayarlarda çalışacak.
5. Harici Arayüz Gereksinimleri
Oyun herhangi bir web servisine, sunucuya veya üçüncü parti API'ye bağlanmayacak ve internet
gerektirmeyecek. Oyuncu verileri ve soru havuzu bilgisayardaki JSON dosyalarında tutulacak. Fare ve
klavye girişleri Unity Input System ile alınacak.
B. Dizayn Raporu
1. Kullanım Senaryoları (Use-Case)
UC-01: Oltayı Fırlat
Açıklama Oyuncunun oltayı denize atıp bir balık ya da eşya yakalaması.
Birincil Aktör Oyuncu
Amaç Rastgele nadirlikte bir eşya yakalayıp soru aşamasına geçmek.
Paydaşlar Oyuncu, Oyun Sistemi
Ön Koşul Oyuncu ana oyun sahnesinde ve oltası takılı.
Tetikleyici Oyuncu "Başlat" butonuna basar.
Son Koşul Bir eşya yakalanır ve soru penceresi açılır.
Temel Akış:
1. Oyuncu "Başlat" butonuna basar.
2. Karakter oltayı suya atar.
3. Oyun Sistemi rastgele bir nadirlik belirler. Oltanın şans çarpanı bu sonucu etkiler.
4. Bu nadirlikte bir eşya suyun yüzeyine çıkar.
5. Soru penceresi açılır.
Alternatif Yol:
1. Oyuncunun takılı oltası yoksa "Önce bir olta kuşanmalısın" uyarısı çıkar.
2. Oyuncu doğru zamanda tıklamazsa balık kaçar ve tekrar denemesi gerekir.
UC-02: Soruyu Yanıtla
Açıklama Oyuncunun yakaladığı eşya için çıkan soruyu cevaplaması.
Birincil Aktör Oyuncu
Amaç Doğru cevap vererek eşyayı ve ödülü kazanmak.
Paydaşlar Oyuncu, Oyun Sistemi
Ön Koşul Ekranda soru penceresi açık.
Tetikleyici Soru penceresi açılır ve süre başlar.
Son Koşul Ödül ya da ceza uygulanır, oyuncu ana sahneye döner.
Temel Akış:
1. Oyun Sistemi eşyanın nadirliğine uygun bir soru getirir.
2. Oyuncu 4 şıktan birini seçer.
3. Oyun Sistemi cevabı kontrol eder.
4. Cevap doğruysa eşya envantere eklenir, puan ve para verilir.
5. Oyuncu ana sahneye döner.
Alternatif Yol:
1. Cevap yanlışsa puan kesilir ve doğru şık gösterilir.
2. Süre biterse cevap yanlış sayılır.
UC-03: Dükkândan Yükseltme Al
Açıklama Oyuncunun kazandığı parayla dükkândan olta ya da kozmetik eşya alması.
Birincil Aktör Oyuncu
Amaç Daha iyi olta ile şansını artırmak ya da karakterinin görünümünü değiştirmek.
Paydaşlar Oyuncu, Oyun Sistemi
Ön Koşul Dükkân ekranı açık.
Tetikleyici Oyuncu dükkândan bir ürün seçer.
Son Koşul Ürün envantere eklenir ve para düşülür.
Temel Akış:
1. Oyuncu ana sahnedeki dükkâna tıklar.
2. Şapka, kıyafet, pantolon ya da olta kategorisinden bir ürün seçer.
3. Oyun Sistemi oyuncunun parasının yetip yetmediğini kontrol eder.
4. Para düşülür ve ürün envantere eklenir.
5. Ürün oltaysa şans çarpanı güncellenir.
Alternatif Yol:
1. Para yetmiyorsa "Yeterli paran yok" uyarısı çıkar, satın alma yapılmaz.
2. Oyuncu "Geri Dön" butonuyla hiçbir şey almadan ana sahneye döner.
UC-04: Eşya Kuşan
Açıklama Oyuncunun envanterindeki bir eşyayı karakterine takması.
Birincil Aktör Oyuncu
Amaç Karakterin görünümünü değiştirmek ya da yeni oltayı kullanmak.
Paydaşlar Oyuncu
Ön Koşul Envanterde kuşanılabilir bir eşya var.
Tetikleyici Oyuncu envanterden bir eşya seçer.
Son Koşul Eşya karaktere takılır.
Temel Akış:
1. Oyuncu envanteri açar.
2. Kuşanmak istediği eşyayı seçer.
3. Aynı türden takılı bir eşya varsa çıkarılır.
4. Yeni eşya takılır ve karakterin görünümü güncellenir.
Alternatif Yol:
1. Seçilen eşya kuşanılamayan bir türse (örneğin balık) "Bu eşya kuşanılamaz" mesajı çıkar.
2. UML Sınıf Diyagramı ve ERD
UML Sınıf Diyagramı
Oyunun ana kontrolü OyunYoneticisi sınıfında. Bu sınıf karakteri, soruları, ödülleri ve cezaları yöneten
sınıflarla bağlantılı. Karakter sınıfı envanterdeki eşyaları ve takılı eşyaları tutuyor. Olta ve KozmetikEsya,
ortak özellikleri Esya sınıfından miras alıyor. Hem soruların zorluğu hem de eşyaların değeri
NadirlikSeviyesi ile belirleniyor.
ERD
Verileri ayrı bir veritabanı yerine JSON dosyalarında tutacağız, ama tabloların birbiriyle ilişkisini bu
şekilde planladık. Bir oyuncunun envanterinde birden fazla eşya olabilir. Bir eşya da birden fazla
oyuncunun envanterinde bulunabilir. NadirlikSeviyesi tablosu hem eşyaların yakalanma ihtimalini hem
de soruların zorluğunu belirliyor. Oyuncu tablosundaki AktifOltaId, oyuncunun o an kullandığı oltayı
gösteriyor.
3. UI/UX Tasarımları
Ana Oyun Ekranı: Oyunun geçtiği yer. Karakter iskelede durup oltayı atıyor. Solda dükkâna giriş için
kulübe var. "Başlat" butonuna basınca olta atılıyor ve sudan bir eşya çıkıyor.
Soru-Cevap Ekranı: Eşya yakalanınca açılıyor. Sol üstte eşyanın nadirlik seviyesi, ortada soru, altta 4
şık var. Doğru cevapta yeşil, yanlışta kırmızı uyarı çıkıyor.
Dükkân Ekranı: Üstte Profil, Tecrübe ve Para bilgileri var. Solda Şapka, Kıyafet, Pantolon ve Olta
kategorileri, sağ altta "Geri Dön" butonu bulunuyor.
Profil Ekranı: Oyuncunun adı, seviyesi, toplam puanı, doğru soru sayısı, doğru cevap oranı ve
yakaladığı en nadir eşya görünüyor.
4. Kullanılan Teknolojiler
Alan Teknoloji Neden
Oyun motoru Unity (2D) 2D oyun yapmak için hazır fizik, animasyon ve arayüz araçları var.
Ücretsiz ve kaynağı bol.
Programlama dili C# Unity'nin kullandığı dil. Nesne yönelimli yapıya uygun.
Veri saklama JSON Ayrı bir veritabanı sunucusu gerektirmiyor. Hem oyuncu kaydı hem
de soru havuzu için kullanılıyor.
Eşya tanımları ScriptableObject Eşyaların ve nadirlik seviyelerinin bilgilerini Unity içinde kolayca
düzenlemek için.
Kontroller Unity Input
System
Fare ve klavye girişlerini almak için.
Diyagram ve tasarım Draw.io Use-case, sınıf diyagramı, ERD ve ekran tasarımlarını çizmek için.
Sürüm kontrolü Git ve GitHub İki kişi aynı proje üzerinde çalışabilmek için.
Oyun tek kişilik ve internetsiz çalışacağı için veritabanı sunucusu yerine JSON dosyalarını seçtik. Böylece
kurulum gerektirmeyen, taşınabilir bir yapı elde ediyoruz.
