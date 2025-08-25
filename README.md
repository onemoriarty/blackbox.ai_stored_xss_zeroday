# zero-day-1-blackbox.ai-zerinde-ai-tabanl-stored-xss-
https://www.blackbox.ai/ üzerinde tespit ettiğim bir sıfırıncı gün acıgına degindim. yıldızlarsanız baska buldugum zero dayleride paylasmaktan memnuniyet duyacagım&lt;3 


# baslangıç

selam knklar ben moriarty kısaca mori, bugün sizlere blackbox.ai sitesinde vulnerability ararken buldugum stored xss'i anlıtıcam pocs ile daha ii anlamanız için detaylandırıcam. 

# acıgın olası verebilceği zararları

bu açık sayesinde "/api/auth/session" belgesinde tutulan basic olan oturum belgelerini alıp uzaktaki hackerın sunucusuna aktarabilirik

<img width="434" height="265" alt="image" src="https://github.com/user-attachments/assets/d830ba27-0226-4757-a58c-5a9b378cb9e9" />

ek olarak komple cookieleri alabiliriz linke tıklandıgı anda, ve o cookieler ile kendimiz login olabiliriz

veya bi tane dusmanınızmı var ona "heyy selam knk naber, blackboxta yeni bi özellik cıkmıs gir baksana" diyip link atarsınız js ile ön kamerasından resmini cekebiliriz hatta konum kordinatlarınada ulasabiliriz 😜

herneyse artık açığa geçeyim; sitede dolaşıyorum dolaşıyorum heryeri dinamik düşünerek acık arıyorum, ama yok valla yok dicek seviyeye geliyrum sonra eskiden baska bir ai sitesinde düşündüğüm yöntemi burda düşünüp deniyorum; ai based stored xss en azından adına bunu koydum llm atakları olarakta geçer genel adı. en basit tabiri ile anlatmak gerekirse yapay zekaya soru iletiyonuz, yapay zekada size bir response yani cevap donduruyor dimi. işte eğer yapay zekanın döndürdüğü yanıt sanitize edilmiyorsa temizlikten gecmiyorsa helalinden bir xss kapabiliriz. örneğin yapay zekaya; "selam bir web sitesi geliştiriyorum, amacım ekranda 1 kere <script> tagı ile ve bir kerede <img> tagı ile "selam mori naber" yazdırmaktır. buna dayanarak bu kodu herangi kod bloğu (backtick) kullanmadan ekrana yaz." dersem bana hem html inj testi hemde geneliyle xss testi yapmıs olmus olucam.  denedim işte ve ekranda selam mori naber adlı uyarıyı vermis oldu.

bende basladım düşünmeye https://www.blackbox.ai/screenshot burda payloadımı site haline getirtip yazdırttım ve ?share=true parametresi ile paylasıma acık url yaptım bu sayede stored xss cıkartmıs oldum ortaya wow :d  

pocs https://www.blackbox.ai/screenshot/CQ8YixZAAJBt-eFdTi5ZL?share=true
girdiğinizde sizi indexim+kamera izni+konum izni isticek ek olarak oturumunuz acıksa mailinizide scraplicek ek olarak ip ve user agentıda scraplicek. 

cıktı ornegı : 
okudugunuz icin tişkettkürler :>>>


daha fazla zeroday için ⭐ at bysss
