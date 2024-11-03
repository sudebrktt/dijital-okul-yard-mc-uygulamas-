# dijital-okul-yard-mc-uygulamas-
öğrencilerin işine yarayacak birçok özellik ve kısa yolun bulunduğu bir projedir.
otomotik ses kaydından yazıya çevirme 
yazıyı ses kaydına çevirme 
ders özetleri ve önemli yerleri vırgulama
ders saati hatırlatıcısı ve haftalık özet 
günlük bildirimler ve motivasyon mesajları 
arkadaşlarda etüt odaları açıp birlikte ders çalışabilme
öğrencilerin anlamadığı soruları birlikte tartışabilmeleri için soru cevap odaları 
uygulamamızın özellikleridir.
# Dijital-Okul-Yard-mc-s-program-
>	Dijital dünyada öğrencilere yönelik böyle bir okul yardımcısı programı, hem zaman kazandırıcı hem de öğrenme sürecini daha verimli hale getirebilir.
>	Dijital Okul Yardımcısı Uygulaması öğrencilere ders takibi, not alma ve organize olma sürecindeki karmaşık ve zaman alıcı süreci kolaylaştırabilir.
> Bu durumu kolaylaştıracak, genel bir “okul yardımcısı” uygulaması geliştirmek, öğrenme ihtiyaçlarına mükemmel bir çözüm sunarak daha kolay ve güzel olabilir.
>
##Dijital Okul Yardımcısı uygulamasında ne gibi özellikler olacak.
>
>Ses kaydını yazıya çevirme
>
>Yazıyı ses kaydına çevirme
>
>Otomatik özetleme ve vurgulama
>
>Çeşitli sorunların birlikte çözümlenebileceği topluluk kısmı
>
>Günlük bildirimler ve motivasyon mesajları
>
>
###Uygulama hakkında genel düsünceler nelerdir

>	Bu uygulama öğrencilerin ders içi ve dışı etkinliklerini en iyi şekilde yönetmelerine yardımcı olabilir.
>Aynı zamanda gelişen teknolojiyle öğrenme süreçlerini daha iyi anlayıp çözümleyerek dersleri daha anlaşılır kılar.
> Özellikle sesli ve yazılı bilgilerin kolayca birbirine dönüştürülmesi öğrencilerin öğrenme tarzlarına göre en uygun yöntemi seçmelerine çok büyük katkı sağlar.
> Böyle bir uygulama ders çalışma alışkanlıklarına yeni kazanımlar sağlarken zaman yönetimi konusunda da öğrencilere çok büyük katkı sağlar.
> Ve bu sayede gençlerin asla uzak duramadığı teknoloji ve eğitimi buluşturan bu uygulama çok yenilikçi bir adım olur.


####Proje çalışmaları bölümlemeleri.
>Proje sistem sahipleri Emine Yıldız Fatma Danışmaz Sude Bereket olarak üç kişi çalışıyoruz bütün aşamalarda hepimiz söz hakkı sahibiyiz.
>Her aşamada hepimizin onayı ve desteği olarak projemizi kurmaya çalışıyoruz.
>Bu süreç uzun bir süreç hepimiz her konuda destekçi ve beraberiz hepimizin bilgileri ile idame ettiriyoruz.

#####Projemize benzer örnek olabilecek bir uygulama aşağıda bıraktık.

[benzer uygulama lnkine aşağıdan ulaşabilirsiniz.](https://apps.apple.com/tr/app/ai-note-taker-voice-to-notes/id6621190550?l=tr)



<img src="[image](https://github.com/user-attachments/assets/99ac91e4-c4b1-4c5d-8d6e-562342a9797a)"alt="alt text" width="20" height="15">


from gtts import gTTS
import os

def text_to_speech(text):
    tts = gTTS(text=text, lang='tr')
    tts.save("output.mp3")
    os.system("start output.mp3")
    
# Örnek kullanım
text_to_speech("Merhaba! Bugünkü çalışma hedefinize ulaştınız mı?")

import speech_recognition as sr

def speech_to_text():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Lütfen konuşun...")
        audio = recognizer.listen(source)
    try:
        text = recognizer.recognize_google(audio, language="tr-TR")
        print(f"Algılanan metin: {text}")
        return text
    except sr.UnknownValueError:
        print("Ses anlaşılamadı.")
    except sr.RequestError:
        print("Servise bağlanılamadı.")
        
# Örnek kullanım
speech_to_text()

import random
import time

motivasyon_mesajlari = [
    "Başarı bir yolculuktur, varış noktası değil.",
    "Bugün harika bir gün olacak!",
    "Kendine güven, harika işler başaracaksın!"
]

def gonder_motivasyon_mesaji():
    mesaj = random.choice(motivasyon_mesajlari)
    print("Motivasyon Mesajı:", mesaj)

# Her gün sabah 9'da göndermek için (basit bir bekletme ile simüle edilebilir)
while True:
    gonder_motivasyon_mesaji()
    time.sleep(86400)  # 24 saat bekle

    from datetime import datetime, timedelta

ders_takvimi = {
    "Pazartesi": "Matematik 10:00",
    "Salı": "Fizik 12:00",
    "Çarşamba": "Kimya 14:00"
}

def ders_bilgisi_goster():
    bugun = datetime.now().strftime("%A")
    if bugun in ders_takvimi:
        print(f"Bugün dersiniz: {ders_takvimi[bugun]}")
    else:
        print("Bugün ders yok.")

ders_bilgisi_goster()

from flask import Flask, render_template, request

app = Flask(name)
sorular = []

@app.route('/')
def ana_sayfa():
    return render_template("index.html", sorular=sorular)

@app.route('/soru', methods=["POST"])
def soru_sor():
    soru = request.form.get("soru")
    if soru:
        sorular.append(soru)
    return ana_sayfa()

if name == "main":
    app.run(debug=True)
