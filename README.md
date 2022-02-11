#Ambient Weather Station Client

Poll the live data on the Ambient ObserverIP and format data into an Influxdb line protocol message and send it via UDP to a Telegraf listener.
The Observer IP with firmware 4.6.1 is the IP interface to the Ambient WS-1401-IP weather station.
Live date is retrieved by
   http://<ip-of-IPObserver>/livedata.htm

The data is return in an html form. This program parses the data into an Influxdb line protocol
message and sends it to the Influx UDP port.

Run with

    $ AmbiientPoll <station-ip>  <influx-ip> <influxdb-port> <sample-time-sec> [verbose]

Build with cmake:

    $ cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE=RPiCrossTools.cmake
    $ cd build
    $ make


Uses Boost ASIO.
C++17
 