Cacti-Pi-CPU-Temperature
========================

Script to write pi CPU temp to rrd for cacti graph.



Requires working Cacti installation perferably hosted on the pi, 'bc' (sudo apt-get install bc), and rrdtool (should be installed automatically with cacti)


After creating a folder for the files to reside, create the RRD file with the following command in your directory:

rrdtool create pitemp.rrd --step 120 DS:pi1:GAUGE:200:U:U DS:pi2:GAUGE:200:U:U RRA:AVERAGE:0.5:1:12 RRA:AVERAGE:0.5:1:288 RRA:AVERAGE:0.5:12:168 RRA:AVERAGE:0.5:12:720 RRA:AVERAGE:0.5:288:365


You can import the graph and data template to cacti, you must manually create the device. Use the screenshot provided here as a template. After modifying the path to the rrd to suite your needs, make the script executable and use cron to run it automatically every two minutes. (Be sure not to change this interval or you will have to modify cacti settings, as well as recreate the rrd)
