# Metro_Simulation
 Metro Simulation 🚇 | Pathfinding with BFS & A*

Kullanılan Sınıf ve Modüller:
1-)collections Modülü: Python'ın standart kütüphanesinde bulunan collections modülü, yüksek performanslı ve kullanışlı veri yapıları sağlar. Bu modül, geleneksel veri tiplerine ek olarak deque, Counter, OrderedDict, defaultdict gibi ek veri tiplerini içerir. ​

2-)deque Sınıfı: collections modülünün bir parçası olan deque (double-ended queue), her iki uçtan da hızlı ve verimli bir şekilde eleman ekleme ve çıkarma işlemleri yapabilen bir veri yapısıdır. Bu özellikleri sayesinde, kuyruk ve yığın gibi veri yapılarının uygulanmasında kullanılır. ​

3-)heapq Modülü: heapq modülü, Python'da öncelik kuyrukları ve yığınlar (heap) oluşturmak için kullanılan bir modüldür. Min-heap özelliğini kullanarak, her zaman en küçük öğenin kök düğümde bulunmasını sağlar. Bu, özellikle öncelik sırasına göre elemanların işlenmesi gereken durumlarda faydalıdır. ​

4-)defaultdict Sınıfı: collections modülünde bulunan defaultdict, varsayılan bir değer türü belirleyerek, sözlükte olmayan bir anahtara erişildiğinde otomatik olarak bu varsayılan değeri atayan bir sözlük türüdür. Bu, özellikle sayma veya gruplama işlemlerinde kullanışlıdır. ​


5-)List, Set, Tuple, Optional: typing modülünden gelen bu generik tipler, Python'da statik tip denetimi ve kodun daha okunabilir olması için kullanılır. List bir listeyi, Set bir küme yapısını, Tuple sabit uzunlukta ve sıralı bir veri yapısını, Optional ise bir değerin ya belirtilen tipte ya da None olabileceğini ifade eder.
 
 BFS Algoritması:
  -Seçili bir düğümden(kaynak veya başlangıç düğümü) başlayarak ve grafiği katman katman dolaşarak komşu düğümleri(kaynak düğüme doğrudan bağlı düğümler) keşfetmeniz gereken bir geçiş algoritmasıdır.
  1-)Başlangıç ve Hedef İstasyon Kontrolü
  -Başlangıç ve hedef istasyonlarının tanımlanan metro ağı içinde olup olmadığı kontrol edilir.

  2-)Başlangıç Değerlerinin Ayarlanması
  -Baslangıç ve hedef istasyonları değişkenlerde tutulur
  -Kuyruk yapısı oluşturulur ve kuyruğa (baslangic_id, [baslangic]) eklenir.
  -Ziyaret edilen istasyonlar(visited) kümesi oluşturulur ve başlangıç istasyonu eklenir.

  3-)Kuyruk İşleme(BFS Döngüsü)
  -Kuyruk boş olana kadar döngü devam eder
  -popleft() ile kuyruktaki ilk eleman alınır.

  4-)Hedef Kontrolü
  -Eğer current_id==hedef__id ise,current_route döndürülerek işlem tamamlanır.

  5-)Komşuları İşleme
  -Mevcut istasyonun komşuları döngü ile incelenir.
  -Eğer komşu istasyon ziyaret edilmemişse:
     -visited listesine eklenir
     -komşu istasyon kuyruğa eklenir.
     
   6-Hedefe Ulaşılmadıysa
   -Kuyruk tamamen işlendiyse ve hedef istasyona ulaşılamadıysa None döndürülür

 A* Algoritması:
 -​Bilgisayar bilimlerinde yaygın olarak kullanılan sezgisel bir arama ve yol bulma algoritmasıdır. Bu algoritma, başlangıç düğümünden hedef düğüme en düşük maliyetli yolu bulmayı amaçlar.
1-) Başlangıç ve Hedef Kontrolü
-Başlangıç ve hedef istasyonlarının metro ağı içinde olup olmadığı kontrol edilir.
-Eğer istasyonlardan biri yoksa None döndürülür.

2️-)Öncelik Kuyruğu (Priority Queue) Hazırlanır
-Öncelik kuyruğu (pq) oluşturulur ve içine (0, baslangic_id, baslangic, [baslangic]) eklenir.
-Buradaki 0, başlangıç istasyonunun toplam süresidir.
-Ziyaret edilen istasyonlar (visited) kümesi oluşturulur.

3️-)Kuyruk İşleme (A Döngüsü)*
-Öncelik kuyruğu boş olana kadar döngü devam eder.
-Süre bakımından en düşük istasyon heapq.heappop(pq) ile kuyruktan çıkarılır.
-current_cost → Güncel istasyona kadar olan toplam süre
-current_id → Güncel istasyonun kimliği
-current_station → Güncel istasyonun kendisi
-current_route → Şu ana kadar olan güzergah

4-) Hedef Kontrolü
Eğer current_id == hedef_id ise, (current_route, current_cost) döndürülerek işlem tamamlanır.

5️-) Ziyaret Edilenleri Güncelleme
Güncel istasyon daha önce ziyaret edildiyse işleme alınmaz.
Ziyaret edilmemişse, visited listesine eklenir.

6-) Komşuları İşleme
Mevcut istasyonun komşuları döngü ile incelenir.
Eğer komşu istasyon ziyaret edilmemişse:
Yeni toplam süre hesaplanır: new_cost = current_cost + travel_time
Komşu istasyon (new_cost, neighbor.idx, neighbor, current_route + [neighbor]) olarak öncelik kuyruğuna eklenir.

7️-)Hedefe Ulaşılamadıysa
-Kuyruk tamamen işlendiyse ve hedef istasyona ulaşılamadıysa None döndürülür.

BFS Algoritması,ağırlıksız grafiklerde en kısa yolu bulmada etkilidir.BFS,başlangıç noktasından itibaren tüm komşu düğümleri seviyeler halinde ziyaret eder ve hedefe ulaşan ilk yolu en kısa yol olarak garanti eder.

A* Algoritması,sezgisel fonksiyonlar kullanarak başlangıç noktasından hedefe en kısa veya en hızlı yolu bulur.İstasyonlar arasındaki seyahat süreleri farklılık gösterebileceğinden bu algoritmayı kullanarak bu sürelere göre en hızlı rotayı belirlemede oldukça işlevseldir..

Bu projenin devamında daha geniş bir metro ağı simüle edebilir ve farklı senaryolar üzerinde çalışabilirim. Örneğin, bir hattın bakımda olması durumunda alternatif rotaların nasıl oluşturulacağına dair çözümler geliştirebilirim. Ayrıca, metro ağı ve rotaları görsel olarak temsil eden, kullanıcı dostu bir arayüz tasarlayarak daha etkileşimli bir deneyim sunabilirim.
   
  
   
   
  

 
 
