# slowloris_improved
Apa itu Slowloris? 
Slowloris pada dasarnya adalah serangan HTTP Denial of Service yang memengaruhi threaded server. 
Cara kerjanya seperti ini:
- Kita mulai membuat banyak permintaan HTTP. 
- Lalu mengirim header secara berkala (setiap ~15 detik) untuk menjaga koneksi tetap terbuka. 
- Dan tidak pernah menutup koneksi kecuali jika server yang melakukannya. Jika server menutup koneksi, 
- kita membuat koneksi baru dan terus melakukan hal yang sama. 
- Hal ini akan menghabiskan thread pool server dan server tidak dapat membalas permintaan dari orang lain.
