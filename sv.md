[English](/README.md) | Svenska | Deutsche | Espanõl

# Avslöjar digitala datainfrastrukturer
Denna workshop ger en introduktion till hur man kan göra en del grundläggande analyser av data som utbyts mellan en dator och onlineservrar när man använder plattformar eller tjänster (t.ex. sociala medier, lärplattformer osv.). Vi kommer att använda metoder för att avslöja infrastrukturer, datapaketströmmar och IP-geolokalisering.

### Vad ska vi jobba med?
All trafik på datanätverk inklusiv Internet består av paket som är små bitar av data. Dessa paket finns i många olika former (eller protokoll) och alla har käll- och destinationsadresser. För att göra det kommer vi att titta på paket genom att samla in så kallade metadata, vilket är data som ger information om annan data.
Utöver detta kommer vi att titta på IP-adresser (Internet Protocol) för källan och destinationen för varje datapaket som utbyttes. Med hjälp av databaser som länkar dessa IP-adresser till geografiska platser kan vi kartlägga den infrastruktur som är involverad medan en plattform eller tjänst används.

### Vilka mjukvaror kommer vi att använda?
Under denna workshop kommer vi att använda Wireshark, ett kalkylark (Excel fungerar bäst, men Google Sheets, LibreOffice och Numbers fungerar med lite justering), en GeoIP-databas, och datorns terminal.
- Vi valde Wireshark för denna workshop, eftersom det är en gratis och öppen källkodspaketanalysator. Den används för felsökning av nätverk, analys, utveckling av programvara och kommunikationsprotokoll och utbildning.
- Microsoft Excel är ett kalkylprogram som innehåller bland annat beräkning, diagramverktyg, pivottabeller. Excel valdes, eftersom det har varit ett mycket allmänt tillämpat kalkylark. 
- IP Geolocations används för att försöka upptäcka en IP-adresss geografiska läge. En IP-adress, kort för internetprotokolladress, är en serie nummer som automatiskt tilldelas varje enhet som ansluter till ett datornätverk. För denna workshop valde vi GeoIP-databasen från Maxmind.

## Samlar in metadata
I den första delen av denna workshop kommer vi att fokusera på att samla in datapaket och metadata.
All trafik på datanätverk som Internet består av paket som är små bitar av data. Vi kan använda en process som kallas paketsniffning för att samla in dessa bitar av metadata och för att få en känsla av dataflödena utan att titta på innehållet i själva paketen.

### Spåra källan och destinationen för den utbytta datan
1. Ladda ner nätverksanalysverktyget [Wireshark](https://www.wireshark.org) (öppen källkod och tillgängligt för Windows, Mac och Linux)
2. Installera Wireshark och öppna den
3. Klickar på "Redigera" (Windows) eller "Wireshark" (Mac) i det övre vänstra hörnet följt av "Inställningar"
4. I det nya fönstret klickar på "Name Resolution" och markerar de första 5 rutorna på höger sida ("Resolve MAC addresses" till "Use an external network name resolver") följt av "OK" för att stänga fönstret
5. Börja spela in din nätverksanvändning genom att klicka på den blå hajfenan på vänster sidan av den övre menyraden. Wireshark registrerar nu källan, destinationen och datatypen för varje datapaket som utbyts mellan din dator och en annan
6. Surfa på webben som vanligt
7. Klicka på stoppknappen i den övre menyraden i Wireshark för att stoppa inspelningen
8. Gå till "Arkiv" > "Exportera paket dissekeringar", välj "Som CSV ..." och spara CSV-filen någonstans där du hittar den

## Vem har du utbytt data med?
### Windows:
1. Ladda ner och öppna följande <a href="/revealing_digital_infrastructure201103.xlsx" download="download"> Excel-fil </a>
2. Gå till fliken "Data" i det medföljande kalkylarket och välj "Från text" i den övre vänstra cellen ("Hämta externa data")
3. Leta upp filen du vill importera och klicka på "importera"
4. Hitta och välj en av filerna du exporterade från Wireshark, se till att "Avgränsad" är markerad för filtyp och klicka på "Nästa"
5. Se till att endast "Komma" är markerat för avgränsare och klicka på "Nästa" igen
6. Lämna "Allmänt" valt för kolumndataformat och klicka på "Slutför"
7. När "Data" har fyllt med de exporterade data från Wireshark, klicka på "Analysis" -fliken för att se resultaten!

### Mac:
1. Ladda ner och öppna följande <a href="/revealing_digital_infrastructure201103.xlsx" download="download"> Excel-fil </a>
2. Gå till fliken "Data" i det medföljande kalkylarket och välj cellen längst upp till vänster
3. Gå till "Arkiv"> "Importera", välj "CSV-fil" och klicka på "Importera"
4. Hitta och välj en av filerna du exporterade från Wireshark, se till att "Avgränsad" är markerad för filtyp och klicka på "Nästa"
5. Se till att endast "Komma" är markerat för avgränsare och klicka på "Nästa" igen
6. Lämna "Allmänt" valt för kolumndataformat och klicka på "Slutför"
7. När "Data" har fyllt med de exporterade data från Wireshark, klicka på "Analysis" -fliken för att se resultaten!

## Var har du utbytt data med?
Nu när vi har en uppfattning om de datapaket som skickas och tas emot kommer vi att titta på deras geografiska fördelningen. Genom att använda GeoIP kan vi kartlägga infrastrukturen som är involverad medan en plattform eller tjänst används.

1.	Ladda ner följande GeoIP-databasfiler: 
-  <a href="/GeoLite2-ASN.mmdb" download="download">GeoLite2-ASN</a>
-  <a href="/GeoLite2-Country.mmdb" download="download">GeoLite2-Country</a>

(Valfritt: Gå till mappen Wireshark (t.ex. C: \ Programfiler \ Wireshark). Skapa en mapp som heter “GeoIP” och kopiera och klistra in de två filerna i den nya mappen)

GeoLite2-datan i filerna skapas av MaxMind och är tillgänglig från <a href="https://www.maxmind.com">https://www.maxmind.com</a>

2. **Windows:** I Wireshark, gå till Redigera → Inställningar → Namnupplösning | **Mac:** I Wireshark, gå till Wireshark → Inställningar → Namnupplösning
3. Klicka på Redigera bredvid Max Mind-databaskataloger och välj den mapp som du satte den nedladdade Geolite2-databasen i (om du följde det valfria steget, välj C: \ Program Files \ Wireshark \ GeoIP)
4. Gå till Statistik → Slutpunkter
5. Se till att IPv4 är markerat högst upp i det nya fönstret (du kan också prova IPv6, men den nyare IP-standarden har vanligtvis mindre spårbara adresser)
6. Längst ner i fönstret klickar du på Karta → Öppna i webbläsaren

## Var har dina paket varit på väg?
Nu har vi sett vilka leverantör som data har utbytts med och har en uppfattning om var deras servrar är, men det är inte hela historien. När datapaket reser över internet hoppar de mellan olika nätverk och lämnar spår av var de har varit. Med hjälp av en teknik som kallas traceroute kan vi avslöja de olika nätverk som datapaket reser mellan våra egna datorer och en viss server.

### Windows:
1. Gå till Excel och öppna fliken "Data" i filen avslöjande_digital_infrastruktur
2. Välj en av adresserna i kolumnen Source eller Destination och kopiera den. Var noga med att inte välja din egen dators adress (det är den som visas oftast)
3. Öppna Windows-sökrutan och skriv "CMD"
4. Öppna appen Kommandotolken
5. Skriv "tracert" i kommandotolken-appen följt av ett mellanslag och adressen från Excel, t.ex. tracert google.com
6. Tryck på enter och se när datorn spårar vägen mellan din dator och servern

### Mac:
1. Gå till Excel och öppna fliken "Data" i filen avslöjande_digital_infrastruktur
2. Välj en av adresserna i kolumnen Source eller Destination och kopiera den. Var noga med att inte välja din egen dators adress (det är den som visas oftast)
3. Öppna Terminal-appen, antingen genom mappen Program → Verktyg eller genom Spotlight (sök)
4. Skriv "traceroute" i terminalen följt av ett mellanslag och sedan adressen från Excel t.ex. spåra google.com
5. Tryck på enter och se när datorn spårar vägen mellan din dator och servern

## Bonusaktivitet
Upprepa stegen, men den här gången besöka inga sociala medier (t.ex. Facebook, Youtube ...). Hur förändras visualiseringarna av den digitala datainfrastrukturen? Är samma leverantörer inblandade eller har några försvunnit?
