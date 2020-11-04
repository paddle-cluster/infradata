[English](/README.md) | [Svenska](/sv.md) | Deutsche | Espanõl

# Avslöjar digitala datainfrastrukturer
Denna workshop ger en introduktion till hur man kan göra en del grundläggande analyser av data som utbyts mellan en dator och onlineservrar när man använder plattformar eller tjänster (t.ex. sociala medier, lärplattformer osv.). Vi kommer att använda metoder för att avslöja infrastrukturer, datapaketströmmar och IP-geolokalisering.

### Vad ska vi jobba med?
All trafik på datanätverk inklusiv Internet består av paket som är små bitar av data. Dessa paket finns i många olika former (eller protokoll) och alla har käll- och destinationsadresser. För att göra det kommer vi att titta på paket genom att samla in så kallade metadata, vilket är data som ger information om annan data.
Utöver detta kommer vi att titta på IP-adresser (Internet Protocol) för källan och destinationen för varje datapaket som utbyttes. Med hjälp av databaser som länkar dessa IP-adresser till geografiska platser kan vi kartlägga den infrastruktur som är involverad medan en plattform eller tjänst används.

### Vilka mjukvaror kommer vi att använda?
Under denna workshop kommer vi att använda Wireshark, Excel och en GeoIP-databas.
- Vi valde Wireshark för denna workshop, eftersom det är en gratis och öppen källkodspaketanalysator. Den används för felsökning av nätverk, analys, utveckling av programvara och kommunikationsprotokoll och utbildning..
- Microsoft Excel is a spreadsheet program that features among others calculation, graphing tools, pivot tables. Excel was chosen, as it has been a very widely applied spreadsheet. 
- IP Geolocations are used to attempt to discover the geographical location of an IP address. An IP address, short for internet protocol address, is a series of numbers that is automatically assigned to each device connecting to a computer network. For this workshop, we chose the GeoIP database provided by Maxmind.

## Samlar in metadata
I den första delen av denna workshop kommer vi att fokusera på att samla in datapaket och metadata.
All trafik på datanätverk som Internet består av paket som är små bitar av data. Vi kan använda en process som kallas paketsniffning för att samla in dessa bitar av metadata och för att få en känsla av dataflödena utan att titta på innehållet i själva paketen.

### Spåra källan och destinationen för den utbytta datan
1. Ladda ner nätverksanalysverktyget [Wireshark](https://www.wireshark.org) (öppen källkod och tillgängligt för Windows, Mac och Linux)
2. Installera Wireshark och öppna den
3. 
- Windows: klickar på "Redigera" i det övre vänstra hörnet följt av "Inställningar"
- Mac: klickar på "Wireshark" i det övre vänstra hörnet följt av "Inställningar"
- I det nya fönstret klickar på "Name Resolution" och markerar de första 5 rutorna på höger sida ("Resolve MAC addresses" till "Use an external network name resolver")
- Klicka på "OK" för att stänga fönstret

4. Börja spela in din nätverksanvändning genom att klicka på den blå hajfenan på vänster sidan av den övre menyraden. Wireshark registrerar nu källan, destinationen och datatypen för varje datapaket som utbyts mellan din dator och en annan
5. Surfa på webben som vanligt
6. Klicka på stoppknappen i den övre menyraden i Wireshark för att stoppa inspelningen
7. Gå till "Arkiv"> "Exportera paket dissekeringar", välj "Som CSV ..." och spara CSV-filen någonstans där du hittar den

## Visualizing digital data infrastructures
In the second part of this workshop, we will visualize the metadata we collected about the digital data exchanged between your computer and external servers during part 1.

### Who have you exchanged data with?
1. Download and open the following <a href="/revealing_digital_infrastructure201103.xlsx" download="download">Excel file</a>
2. Mac: Go to the "Data" tab of the supplied spreadsheet and select the top left cell
2. Windows: Go to the "Data" tab of the supplied spreadsheet and select "From Text" in the top left cell ("Get external data") 
3. Mac: Go to "File"  > "Import", select "CSV file" and click on "Import"
3. Windows: Look up the file you want to import and click on "import"
4. Find and select one of the files you exported from Wireshark, make sure "Delimited" is selected for file type and click "Next"
5. Make sure that only "Comma" is selected for delimiters and click "Next" again
6. Leave "General" selected for column data format and click "Finish"
7. Once the "Data" is filed with the exported data from Wireshark, click on the "Analysis" tab to see the results!

### Where have you exchanged data with?
Now that we have an idea about the data packets that are sent and received, we will look at the geographical distribution. By using the GeoIP we can map the infrastructure that is involved while a platform or service is in use.

1.	Download the following GeoIP database files: 
-  <a href="/GeoLite2-ASN.mmdb" download="download">GeoLite2-ASN</a>
-  <a href="/GeoLite2-Country.mmdb" download="download">GeoLite2-Country</a>

The GeoLite2 data contained in the files is created by MaxMind and available from <a href="https://www.maxmind.com">https://www.maxmind.com</a>

(Optional: Go to the Wireshark folder (e.g.: C:\Program Files\Wireshark) Create a folder called “GeoIp” and copy & paste the two files into the new folder) 

2.	In Wireshark, go to 'Edit→Preferences→Name Resolution'  
3.	Click 'Edit' next to 'Max Mind database directories' Choose the folder that you put the downloaded Geolite2 database in (if you followed the optional step, choose “C:\Program Files\Wireshark\GeoIP) 
4.	Go to 'Statistics→Endpoints'  
5.	On the top of the new window, make sure IPv4 is selected (you can try IPv6 as well, but the newer IP standard usually has less traceable addresses)  
6.	At the bottom of the window, click 'Map→Open in browser'

## Bonus activity
Repeat the steps, but this time do not visit any social media webpages (e.g. Facebook, Youtube…)
How do the visualizations of the digital data infrastructure change? Are the same providers involved or have some disapeared?
