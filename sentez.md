## __2.1- İlk Bipleriniz__

Aşağıdaki örnek koda bakalım:
	play 70
Bu kod her şeyin başlangıcı. Bu kodu kopyalayıp kod alanına (Run tuşunun altındaki beyaz alan) yapıştır ve sonra Run tuşuna bas!

__-Biipp!__

Etkileyici! Tekrar bas. Şimdi yine bas. Yine…

Vay be çılgın, Eminim bütün gün boyunca bu tuşa basıp durabilirsin. Fakat kendini sonsuz Beep’lerin içinde kaybetmeden önce, numarayı değiştirmeyi deneyebilirsin:

	play 75

Bir fark duyabiliyor musun? Daha düşük bir numarayı dene:

	play 60

Düşük rakamlar düşük perdede seslere, yüksek rakamlar yüksek perdede seslere yol açıyor. Aynı piyano gibi, piyanonun alt tarafındaki (sol tarafı) tuşlar daha düşük notalar çalarken üst tarafındaki (sağ taraf) tuşlar daha yüksek notaları çalıyor. Aslında bakarsak bu numaralar piyanonun tuşlarına denk geliyor, play 47 demek piyanonun 47’inci notasını çal demek. Bu da demek oluyor ki, play 48 aslında bir nota üstte (sağdan bir nota üstte). 4.oktav C, numara 60 oluyor.

## __-Akorlar__

Tek bir nota çalmak eğlenceli fakat birden fazla notayı aynı anda çalmak çok daha iyi: Alttaki örneği kopyalayıp yapıştır ve dene:

	play 72
	play 75
	play 79
 
Senin de fark ettiğin üzere birden fazla play yazdığında hepsi aynı anda çalıyor. Kendin yeni notaları dene, hangileri birlikte güzel oluyor? Hangileri kötü oluyor? Denemekten korkma, keşfet!

## __-Melodi__

Notaları ve akorları oynatmak eğlenceli, fakat bir melodiye ne dersin? Ya bir notayı başka bir notadan sonra oynatmak istersen o zaman napıcaksın? Tek yapman gereken arlarına sleep koymak!

	play 72
	sleep 1
	play 75
	sleep 1
	play 79
