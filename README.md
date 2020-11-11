English | [Svenska](/sv.md) | Deutsche | Espanõl

# Revealing digital data infrastructures
This workshop gives an introduction to how you can do some basic analysis of the data that is exchanged between a computer and online servers when using particular platforms or services (e.g. social media, learning management systems, etc). We will use approaches to uncovering infrastructures, data packet streams and IP geolocation.

### What will we look at?
All traffic on data networks like the internet consists of packets that are small chunks of data. These packets come in many different forms (or protocols) and each have source and destination addresses. To do so, we will look at packets by collecting so-called metadata, which is data that provides information about other data.
In addition to this, we will look at Internet Protocol (IP) addresses for the source and destination of each packet of data that was exchanged. Using databases that link those IP addresses to geographic locations, we can map the infrastructure that is involved while a platform or service is in use.

### What programs will we use?
During this workshop, we will use Wireshark, a spreadsheet (Excel works best, but Google Sheets, LibreOffice and Numbers work with a little tweaking), a GeoIP database, and your computer's terminal. 
- We chose Wireshark for this workshop, as it is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education.
- Microsoft Excel is a spreadsheet program that features among others calculation, graphing tools, pivot tables. Excel was chosen, as it has been a very widely applied spreadsheet. 
- IP Geolocations are used to attempt to discover the geographical location of an IP address. An IP address, short for internet protocol address, is a series of numbers that is automatically assigned to each device connecting to a computer network. For this workshop, we chose the GeoIP database provided by Maxmind.

## Collecting metadata
In the first part of this workshop, we will focus on collecting data packets and metadata. 
All traffic on data networks like the internet consists of packets that are small chunks of data. We can use a process called packet sniffing to collect these pieces of metadata and to get a sense of the flows of data without looking at the content of the packets themselves.

### Tracking the source and destination of the data you exchange
1. Download the network analysis tool [Wireshark](https://www.wireshark.org) (open source and available for Windows, Mac and Linux)
2. Install Wireshark and open it
3. Click on "Edit" (Windows) or "Wireshark" (Mac) in the top left corner followed by "Preferences"
4. In the new window, click on "Name Resolution" and tick the first 5 boxes on the right side ("Resolve MAC adresses" to "Use an external network name resolver") followed by "OK" to close the window
5. Start recording your network use by clicking on the blue shark fin on the left of the upper menubar. Wireshark will now record the source, destination, and type of data for every data packet that is exchanged between your computer and another
6. Surf the web as you usually would
7. Click the stop button in the upper menubar of Wireshark to stop recording
8. Go to "File" > "Export Packet Dissections", select "As CSV..." and save the CSV file somewhere that you can find it

## Who have you exchanged data with?
### Windows:
1. Download and open the following <a href="/revealing_digital_infrastructure201103.xlsx" download="download">Excel file</a>
2. Go to the "Data" tab of the supplied spreadsheet and select "From Text" in the top left cell ("Get external data") 
3. Look up the file you want to import and click on "import"
4. Find and select one of the files you exported from Wireshark, make sure "Delimited" is selected for file type and click "Next"
5. Make sure that only "Comma" is selected for delimiters and click "Next" again
6. Leave "General" selected for column data format and click "Finish"
7. Once the "Data" is filed with the exported data from Wireshark, click on the "Analysis" tab to see the results!

### Mac:
1. Download and open the following <a href="/revealing_digital_infrastructure201103.xlsx" download="download">Excel file</a>
2. Go to the "Data" tab of the supplied spreadsheet and select the top left cell
3. Go to "File"  > "Import", select "CSV file" and click on "Import"
4. Find and select one of the files you exported from Wireshark, make sure "Delimited" is selected for file type and click "Next"
5. Make sure that only "Comma" is selected for delimiters and click "Next" again
6. Leave "General" selected for column data format and click "Finish"
7. Once the "Data" is filed with the exported data from Wireshark, click on the "Analysis" tab to see the results!

## Where have you exchanged data with?
Now that we have an idea about the data packets that are sent and received, we will look at the geographical distribution. By using the GeoIP we can map the infrastructure that is involved while a platform or service is in use.

1.	Download the following GeoIP database files: 
-  <a href="/GeoLite2-ASN.mmdb" download="download">GeoLite2-ASN</a>
-  <a href="/GeoLite2-Country.mmdb" download="download">GeoLite2-Country</a>

(Optional: Go to the Wireshark folder (e.g.: C:\Program Files\Wireshark) Create a folder called “GeoIp” and copy & paste the two files into the new folder)

The GeoLite2 data contained in the files is created by MaxMind and available from <a href="https://www.maxmind.com">https://www.maxmind.com</a>

2.	**Windows:** In Wireshark, go to Edit→Preferences→Name Resolution | **Mac:** In Wireshark, go to Wireshark→Preferences→Name Resolution
3.	Click Edit next to Max Mind database directories and choose the folder that you put the downloaded Geolite2 database in (if you followed the optional step, choose C:\Program Files\Wireshark\GeoIP) 
4.	Go to Statistics→Endpoints  
5.	On the top of the new window, make sure IPv4 is selected (you can try IPv6 as well, but the newer IP standard usually has less traceable addresses)  
6.	At the bottom of the window, click Map→Open in browser

## Where have your packets been on the way?
Now we have seen which providers data has been exchanged with and have an idea of where their servers are, but that isn't the whole story. As data packets travel across the internet, they hop between different networks leaving a trace of where they have been. Using a technique called traceroute we can reveal the different networks that data packets travel on between our own computers and a particular server.

### Windows:
1. Go to Excel and bring up the Data tab in the revealing_digital_infrastructure file
2. Choose one of the addresses listed in either the Source or Destination column and copy it. Be sure not to choose your own computer's address (that's the one that appears most often)
3. Open the Windows search box and type "CMD"
4. Open the Command Prompt app
5. In the Command Prompt app type "tracert" followed by a space and the address from the Excel e.g. tracert google.com
6. Press enter and watch as the computer traces the route between your computer and the server

### Mac:
1. Go to Excel and bring up the Data tab in the revealing_digital_infrastructure file
2. Choose one of the addresses listed in either the Source or Destination column and copy it. Be sure not to choose your own computer's address (that's the one that appears most often).
3. Open the Terminal app, either through the Applications→Utilities folder or through Spotlight (search)
4. In the Terminal write "traceroute" followed by a space and then the address from Excel e.g. traceroute google.com
5. Press enter and watch as the computer traces the route between your computer and the server

## Bonus activity
Repeat the steps, but this time do not visit any social media webpages (e.g. Facebook, Youtube…). How do the visualizations of the digital data infrastructure change? Are the same providers involved or have some disapeared?

