# ortalamahesaplayıipdosyayakaydetme
def ortalama_hesapla(satir):
    satir = satir[:-1]
    list = satir.split(":")
    ogrenciadi = list[0]
    notlar = list[1].split(",")
    sayi1 = int(notlar[0])
    sayi2 = int(notlar[1])
    sayi3 = int(notlar[2])
    ortalama = (sayi1 +sayi2 + sayi3) / 3

    if ortalama > 85 :
        harf = "a"
    elif ortalama <= 85 and ortalama > 50 :
        harf = "b"
    else:
        harf = "f"
    return ogrenciadi + ":" + harf + "," + str(ortalama) + "\n"

def notlari_oku():
    with open ("ogrencinotlari.txt", "r", encoding = "utf-8") as file:
        for satir in file:
            print(ortalama_hesapla(satir))
def not_gir():
    isim = input("İsminizi giriniz")
    not1 = input("1.notunuzu giriniz")
    not2 = input("2.notunuzu giriniz")
    not3 = input("3.notunuzu giriniz")
    with open ("ogrencinotlari.txt", "a", encoding = "utf-8") as file:
        file.write( isim +":" + not1 +"," + not2 + ","+ not3 + "\n" )

def not_kaydet():

    with open ("ogrencinotlari.txt","r", encoding = "utf-8") as file:
        listt = []
        for i in file:
            listt.append(ortalama_hesapla(i))
        with open ("kayitlinotlar.txt", "w", encoding = "utf-8") as file2:
            for i in listt:
                file2.write(i)

while True:
    islem = input("Notları okumak için 1'e basınız\nNot girmek için 2'ye basınız\nNotları kaydetmek için 3'e basınız\nÇıkış için x'e basınız")
    if (islem == "1"):

        notlari_oku()
    elif (islem == "2"):
        not_gir()

    elif (islem =="3"):
        not_kaydet()
    else:
        break
