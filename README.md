# Revealing digital data infrastructures
This workshop gives an introduction to how you can do some basic analysis of the data that is exchanged between a computer and online servers when using particular platforms or services (e.g. social media, learning management systems, etc). We will use approaches to uncovering infrastructures, data packet streams and IP geolocation.

### What will we look at?
All traffic on data networks like the internet consists of packets that are small chunks of data. These packets come in many different forms (or protocols) and each have source and destination addresses. To do so, we will look at packets by collecting so-called metadata, which is data that provides information about other data.
In addition to this, we will look at Internet Protocol (IP) addresses for the source and destination of each packet of data that was exchanged. Using databases that link those IP addresses to geographic locations, we can map the infrastructure that is involved while a platform or service is in use.

### What programs will we use?
During this workshop, we will use Wireshark, Excel and a GeoIP database. 
We chose Wireshark for this workshop, as it is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education.

Microsoft Excel is a spreadsheet program that features among others calculation, graphing tools, pivot tables. Excel was chosen, as it has been a very widely applied spreadsheet. 

IP Geolocations are used to attempt to discover the geographical location of an IP address. An IP address, short for internet protocol address, is a series of numbers that is automatically assigned to each device connecting to a computer network. For this workshop, we chose the GeoIP database provided by Maxmind.
