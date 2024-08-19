# slowloris_improved
Apa itu Slowloris? 
Slowloris pada dasarnya adalah serangan HTTP Denial of Service yang memengaruhi threaded server. 
Cara kerjanya seperti ini:
- Kita mulai membuat banyak permintaan HTTP. 
- Lalu mengirim header secara berkala (setiap ~15 detik) untuk menjaga koneksi tetap terbuka. 
- Dan tidak pernah menutup koneksi kecuali jika server yang melakukannya. Jika server menutup koneksi, 
- kita membuat koneksi baru dan terus melakukan hal yang sama. 
- Hal ini akan menghabiskan thread pool server dan server tidak dapat membalas permintaan dari orang lain.

# cara penggunaan
- python3 slowloris.py [-h] [-p PORT] [-s SOCKET]
+  [-v] [-ua] [-x]
+  [--proxy-host PROXY_HOST]
+  [--proxy-port PROXY_PORT]
+  [--https]
+  [--sleeptime SLEEPTIME]
+  [host]
- host   host to perform test
* options :
+ -h --help
+ -p PORT,  --port PORT port of webserver , biasanya 80
+ -s SOCKET, --socket SOCKET jumlah socket yang digunakan untuk test
+ -ua, --randuseragent menggunakan user agent secara acak dan ambacak tiap request
+ -x, --useproxy  menggunakan proxy SOCKS5 untuk koneksi
+ --proxy-host PROXY_HOST SOCKS5 proxy host
+ --proxy-port PROXY_PORT SOCKS5 proxy port
+ --https menggunakan https untuk request
+ --sleeptime SLEEPTIME waktu molor diantara header yg terkirim

# CONTOH
- biasa : python3 slowloris.py example.com
- lada : python3 slowloris.py -ua -v example.com
- super : python3 slowloris.py -https -v -ua example.com
