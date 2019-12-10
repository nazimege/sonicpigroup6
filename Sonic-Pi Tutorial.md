# __GİRİŞ__
Sonic Pi’a hoş geldiniz. Umarım siz de çılgın müzikler yapmaya başlamak için, benim size öğretmek için heyecanlı olduğum kadar heyecanlısınızdır. Müzik, sentez, programlama, kompozisyon, performans ve daha fazlasına doğru eğlenceli bir yolculuğa başlıyoruz.

Fakat durun, ne kadar da kabayım! Kendimi tanıtmama izin verin – Ben Sam Aaron – Sonic Pi’ı yaratan kişiyim. Beni Twitter’dan @samaaron adıyla bulabilirsiniz, size selam vermekten mutluluk duyarım. Ayrıca, seyirci önünde Sonic Pi ile kodlayarak canlı müzik yapma performansımı da görmek isteyebilirsiniz.

Eğer aklınızda Sonic Pi’ı geliştirmeye dair fikirler varsa lütfen aktarın, geri dönüt almak çok yardımcı oluyor. Fikrinizin sonraki yenilik olabileceğini asla bilemezsiniz!

Bu rehber kategorize edilmiş bölümlerden oluşmaktadır. Bu rehberi baştan sona kolay bir öğrenme aracı olması için yazdım, istediğiniz bölümlere özgürce girip çıkmaktan çekinmeyin. Eğer eksik bir kısım olduğunu düşünüyorsanız daha sonraki versiyonlarda eklemem için bana söyleyebilirsiniz.

Son olarak, diğer insanları kodlayarak canlı müzik yaparken izlemek de çok iyi bir öğrenme yoludur. Düzenli olarak http://youtube.com/samaaron kanalında canlı yayın yapıyorum, uğrayıp selam vermekten ve soru sormaktan çekinmeyin 

## __1.1	Canlı Kodlama__

Sonic Pi’ın en ilgi çekici özelliklerinden bir tanesi, sanki gerçek bir olanak tanımasıdır. Demek oluyor ki sadece biraz pratikle Sonic Pi’ı alıp sahneye çıkabilirsiniz.

__Zihninizi Boşaltın__

Rehberimizin devamında Sonic Pi’ın detaylarına inmeden önce size, canlı kodlamanın nasıl bir deneyim olduğunu göstermek istiyorum. Çok fazla (ya da hiç) anlamasanız da endişelenmeyin, sadece koltuğunuza yaslanıp keyfini çıkartın.

__Canlı Döngü__

Haydi başlayalım, aşağıdaki kodu yukarıdaki katmanlardan birine kopyalayın:

live_loop :flibble do
  sample :bd_haus, rate: 1
  sleep 0.5
end.                                                    

Şimdi,  Run tuşuna tıklayın ve hoş bass bateri ritmini duyun. Ne zaman sesi susturmak isterseniz  Stop tuşuna basabilirsiniz. Ancak hemen basmayın, henüz değil. Onun yerine aşağıdaki adımları takip edin:

1.	Bass bateri sesinin hala devam ettiğinden emin olun
2.	değerini 0.5’den 1 gibi daha yüksek bir değerle değiştirin
3.	Run tuşuna tekrar basın
4.	Bateri hızının nasıl değiştiğini fark edin.
5.	Son olarak, bu anı unutmayın, bu ilk canlı kodladığınız an ve son da olmayacak…

Tamam, bu yeterince basitti. Haydi mix’e başka şeyler ekleyelim. sample :bd_haus satırının üstüne sample :ambi_choir, rate: 0.3 satırını ekleyin. Kodunuz bu şekilde gözükmeli: 

live_loop :flibble do
  sample, rate: 0.3
  sample :bd_haus, rate: 1
  sleep 1
end

Şimdi, biraz kodla vakit geçirin. Değerleri değiştirin – daha yüksek değerler kullandığınızda ne oluyor, daha düşük değerler ya da negatif değerler? :ambi_choir için rate: değerini değiştirdiğinizde (mesela 0.29) ne olduğunu görün. Çok çok küçük bir değeri seçerseniz ne oluyor? Eğer çok küçük bir değer verirseniz bilgisayarınız ritme yetişemeyip bir hata vererek duracaktır (eğer bu olursa daha büyük bir sleep değeriyle programı tekrardan çalıştırın).

Sample satırlarından birine  # ekleyerek yoruma dönüştürün, böylece kodunuzdan çıkmış olacak:

live_loop :flibble do
  sample :ambi_choir, rate: 0.3
#  sample :bd_haus, rate: 1
  sleep 1
end

Bilgisayarınızın o satırı nasıl görmezden geldiğini fark ettiniz mi, böylece o satırı duymuyoruz. Buna yorum denir. Sonic Pi’da yorumları kodumuzdan bir şeyler çıkarmak ya da kodumuza bir şeyler eklemek için kullanabiliriz. 

Son olarak, size oynaması eğlenceli olacak bir şey bırakmama izin verin. Aşağıdaki kodu alıp farklı bir katmana kopyalayın. Şimdi, çok fazla anlamaya çalışmadan sadece iki tane farklı döngü olduğunu görün – yani iki şey aynı anda devam ediyor. Şimdi, en iyi yaptığınız şeyi yapın – deneyin ve oynayın. İşte birkaç tavsiye:

+	Mavi rate: değerlerini değiştirip sesin nasıl değiştiğine bakın.
+	Sleep değerlerini değiştirerek iki döngünün de nasıl birbiri etrafında farklı
+	Yoruma dönüştürdüğünüz satırı tekrar eski haline getirip arkada çalan gitarın keyfini çıkartın.
+	Mavi mix: değerlerinden birini 0 ile 1 aralığında değiştirin.

Run tuşuna basıp değiştirdiğiniz şeyin sonraki döngü başlangıcında sesteki etkisini görün. Eğer bir şekilde zor durumda kalırsanız endişelenmeyin, sadece Stop tuşuna basın, kodu silip değiştirilmemiş halini tekrardan yapıştırın. Böylece tekrar doğaçlamaya başlayabilirsiniz. Hata yapmak öğrenmenin en kısa yoludur…

live_loop :guit do
  with_fx :echo, mix: 0.3, phase: 0.25 do
    sample :guit_em9, rate: 0.5
  end
#  sample :guit_em9, rate: -0.5
  sleep 8
end

live_loop :boom do
  with_fx :reverb, room: 1 do
    sample :bd_boom, amp: 10, rate: 1
  end
  sleep 8
end

Şimdi, merakınız tetiklenene ve bununla daha neler yapabileceğinizi düşünmeye başlayana kadar denemeye ve oynamaya devam edin. Şimdi rehberin geri kalanını okumaya hazırsınız.

Ee, daha ne duruyorsunuz…

## __1.2– Sonic Pi Ara yüzü__

Sonic Pi müzik kodlamak için çok basit bir ara yüze sahip. Haydi biraz zaman geçirerek keşfedelim.

 

+	A – Oynatma Kontrolleri
+	B – Düzenleme Kontrolleri
+	C – Bilgilendirme ve Yardım
+	D – Kod Düzenleyicisi
+	E – Tercih Paneli
+	F – Geçmiş Paneli
+	G – Yardım Sistemi
+	H – Kapsam Görüntüleyici

__A.	Oynatma Kontrolleri__

Bu pembe tuşlar sesleri başlatma ve bitirmenin ana yoludur. Run tuşu düzenleyicideki kodu çalıştırmaya, Stop tuşu da çalışan bütün kodları durdurmaya, Save tuşu kodu dış bir dosyaya kaydetmeye ve Record tuşu ise çalan sesi kaydetmeye (WAV dosyası şeklinde) yarar.

__B.	Düzenleyici Kontrolleri__

Bu turuncu tuşlar kod düzenleyicisini kontrol etmenizi sağlar. Size + ve Size – tuşları yazıyı büyütmeye ve küçültmeye yarar. 

__C.	Bilgilendirme ve Yardım__

Bu mavi tuşlar bilgilendirmelere, yardıma ve tercihlere erişiminizi sağlar. Info tuşu Sonic Pi’ın kendisi hakkında – çekirdek ekip, tarihçe, yardımcı olanlar ve topluluk- hakkında bilgi veren bir pencere açar. Help tuşu yardım sistemini (G) aktifleştirir ve Prefs tuşu basit sistem parametrelerini kontrol edebileceğiniz bir tercihler penceresi açar.

__D.	Kod Düzenleyicisi__

Bu alan kodunuzu yazdığınız ve müzik icra ettiğiniz alandır. Kod yazabileceğiniz, silebileceğiniz, kesip yapıştırabileceğiniz basit bir yazı düzenleyicisidir. Word veya Google Docs’un basit bir versiyonu gibi düşünebilirsiniz. Bu düzenleyici kelimeleri anlamlarına göre otomatik olarak renklendirir. Bu özellik başlangıçta garip gelebilir, ancak zaman geçtikçe ne kadar faydalı olabileceğini göreceksiniz. Örneğin, bir şeyin mavi olmasından onun bir sayı olduğunu anlayabileceksiniz.

__E.	Tercih Paneli__

Sonic Pi Bilgilendirme ve Yardım bölümündeki prefs butonuna tıklanarak ulaşılabilen bir tercihler penceresine sahiptir. Bu içinde bir miktar ayar bulunan tercihler penceresinin açılmasını sağlar. Örneğin, mono ses moduna geçme, stereoya geçme, Raspberry Pi’de ses seçici vb.


__F.	Geçmiş Paneli__ 

Kodunuzu çalıştırdığınızda programın ne yaptığı bu panelde gösterilir. Varsayılan olarak yarattığınız sesle eş zamanlı olarak sesle ilgili bir mesaj yazar. Bu özellik kodunuzdaki hataları görmek ve kodunuzun ne yaptığını anlamak için önemlidir.

__G.	Yardım Sistemi__

Sonic Pi’ın en önemli kısımlarından birisi de pencerenin altında yer alan yardım sistemidir. Bu sistem mavi  Help tuşuna tıklanarak aktifleştirilebilir. Yardım sistemi Sonic Pi’ın içinde bulundurduğu her şeyle, bu rehber, synthler, örnekler, FX ve Sonic Pi’ın sağladığı bütün fonksiyonların listesi, ilgili yardım ve bilgiler içerir.

__H.	Kapsam Görüntüleyici__

Kapsam görüntüleyici duyduğunuz sesi aynı zamanda görmenizi sağlar. Saw sesinin gerçekten de bir testereye benzediğini ve basit beep sesinin ise bir sinüs dalgası olduğunu kolayca görebilirsiniz. Ayrıca dalgaların boyutundan çaldığınız sesin kısık ya da yüksek olduğunu da anlayabilirsiniz. Oynayabileceğiniz 3 tane kapsam bulunmakta – varsayılan kapsam sağ ve sol kanalı birleştiren bulunmakta, ayrıca her bir kanal için ayrı bir kapsam oluşturan stereo kapsamı bulunmakta ve son olarak da Lissajous eğrisi sağ ve sol kanalın arasındaki ilişkiyi kullanarak güzel resimler çizebilirsiniz (https://en.wikipedia.org/wiki/Lissajous_curve).

__1.3– Çalarak Öğrenmek__

Sonic Pi sizi bilgisayarı ve müziği aynı anda çalarak ve deneyerek öğrenmeye teşvik eder. En önemli şey eğleniyor olmanız ve ayrıca nasıl kodlanacağını ve doğaçlama yapılacağını da öğrenmiş oluyorsunuz.

Hata Yoktur

Hazır bu konudayken size biraz yıllarca süren canlı kodlayarak müzik yapma hakkında edindiğim bilgileri tavsiye olarak vermeme izin verin – hata yoktur, sadece fırsatlar vardır. Bu benim sıklıkla Jazz hakkında duyduğum bir şey fakat aynı şey canlı kodlama için de geçerli. Ne kadar tecrübeli olduğunuz önemsiz – yeni başlayan birinden yıllarca kodlayarak müzik yapmış birine kadar herkes bazen beklenmedik sonuçlar alabilir. Bazen bu beklenmedik sonuçlar kulağa güzel gelebilir ve bazen müziğinize onu da dahil edersiniz. Fakat, bazen tamamen kötü de olabilir. Ne olduğu önemsiz, tek önemli olan onunla ne yaptığınız. Sesi alın, değiştirin ve müziğinizle uyumlu mükemmel bir şeye dönüştürün.

Basit Başlayın

Öğrenirken muhteşem şeyler yapmanın cazibesini göreceksiniz. Fakat, bu isteği birazcık sonraya saklayın. Şimdilik sadece basit şeyleri düşünüp bundan zevk almaya çalışın ve basit adımlar atın. Aklınıza bu basit adımlar hakkında fikirler geldiğinde onu gerçekleştirmeye çalışın ve verdiği fikirlerle çalın. Gerçekten yol kat etmekle meşgul olmaya başlamadan önce, yaptıklarınızı başkalarıyla paylaşmaktan çekinmeyin
