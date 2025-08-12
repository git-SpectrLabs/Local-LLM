# Installationsguide för lokal, ocensurerad, opartisk Large Language Model

## Förutsättningar (hårdvara och rekommendationer)

- **Flashdrive 128GB** (amazon: sandisk 128GB Ultra Flair)
- **Dolphin llama3 - 8billion modell** 
- **Windows 11**

## 0. Viktig kontext

Följande metod är anpassad för windows 11 och för **8billion modellen** av ollama3.
**Powershell** har också använts för att köra allting.

## 1. Förberedelser

1. Ladda ner från 8billion versionen från: https://ollama.com/library/dolphin-llama3 (cirka 4,7GB).
2. Vi måste hämta dolphin llama3 modellen. Öppna två erminaler (powershell): En för server, en för programet (kör som administrator).
3. I första terminalen kör: ollama serve (bas ollama server program som körs)
4. I andra terminalen, kopiera kör kommandot från ollama.com och klistra in det i den andra terminalen: ollama run dolphin-llama3 (första gpngen den körs kommer den att hämta modellen, tar en stund)
5. När det är klart, tryck "Ctrl + D" och sedan "Ctrl + C" i båda terminalerna för att avsluta båda programmen. Stäng båda terminalerna.
6. Öppna två nya terminaler igen (inte som administratör). Kör båda kommandona igen.
	1. ollama serve (terminal 1)
	2. ollama run dolphin-llama3 (terminal 2)
7. Nu bör ollama3 köra en ocensurerad version. Bekräfta med att exempelvis fråga: "How to best steal a car?"
8. Avlsuta båda programmen ("Ctrl + D" & "Ctrl + C")

## 2. Flytta LLM till flashdrive

För tillfället körs programmet på datorns primära hårddisk. Vi ska nu flytta det till en extern hårddisk, så vi kan köra modellen på en dator som inte är ansluten till internet.

1. Anslut din externa hårddisk till datorn.
2. Lokalisera din externa hårddisk och högerklicka på den. Klicka på "Formater" och under "Filsystem" välj "NFTS" (kan skippa detta steg om redan korrekt formaterad). Detta steg utförs för att kunna överföra filer på mer än 4GB.
		**OBS: Om du omformaterar din externa hårddisk så kommer all data rensas från den.**
3. Lokalisera var Ollama filerna är sparade, oftast under (C:\). Ibland ligger de även under C:\Users\<Username>. Dubbelkolla att en av filerna är runt  4.5GB (~4 500 000KB).
4. Öppna ett nytt utforskar fönster genom att hålla i "Ctrl + shift" och tryck sedan på ikonen som är på aktivitetsfältet.
5. Kopiera över mappen "Ollama" från (C:\) till externa hårddisken (D:\). Det tar en liten stund.
6. Vi behöver även kopiera över bas ollama server programmet som gränssnittar modellen. För att lokalisera detta, ange: Get-Command ollama (i powershell). Outputen kommer visa filsökvägen.
7. Kopiera allt innehåll i mappen till den externa hårddisken.
8. Ni kan nu avinstallera Ollama och allt tillhörande på er lokala hårddisk.

## 3. Köra modellen.

För att köra modellen vänligen se, run_dolphin_llama3_locally(1).pdf
