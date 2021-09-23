# Jarkom-Modul-1-E06-2021

## Anggota:
- ### Muhammad Daffa 05111940000175
- ### Putu Krisna Andyartha 05111940000082
- ### Ananda ...

## 1.
## 2.
## 3.
## 4.
## 5.
## 6. Cari username dan password ketika melakukan login ke FTP Server!

  Dengan memasukkan `ftp.request.command == PASS` pada filter display, maka muncul list packet dengan request login FTP
  ![image](https://user-images.githubusercontent.com/36522826/134306332-4831ac33-d8ef-44a9-b670-1d5908050c52.png)
  Setelah muncul list packet tersebut, kemudian dilanjutkan dengan follow TCP stream
  ![image](https://user-images.githubusercontent.com/36522826/134306423-ffac1d82-3854-494e-9b49-7b2625d542db.png)
  Maka muncul username `secretuser` dan password `aku.pengen.pw.aja`

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

  Dengan menggunakan `frame contains "Real.pdf"` kemudian muncul packet yang mengandung file Real.pdf.
  ![image](https://user-images.githubusercontent.com/36522826/134306569-8f04be5f-cdd3-4efe-889a-425580d7ecaf.png)
  Kemudian follow TCP Stream, kemudian di bagian Show Data As diganti yang awalnya ASCII diubah menjadi raw kemudian di save as Real.zip. Kemudian dibuka Real.pdf dan terdapat gambar Rick Astley
  ![image](https://user-images.githubusercontent.com/36522826/134306659-2db9cffc-78e0-4828-88a8-1b22314d45cb.png)
  ![image](https://user-images.githubusercontent.com/36522826/134306832-84a02e9e-1b70-44df-bcbe-6b0876063304.png)

## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

  Dengan menggunakan `ftp-data.command == RETR`, seharusnya akan muncul list packet yang menunjukkan pengambilan file dari ftp di soal. Namun di kasus kali ini tidak muncul list packet pada soal
  ![image](https://user-images.githubusercontent.com/36522826/134307280-1764afa1-8f6d-40dd-ac7a-a00c37b1b50f.png)

## 9. Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

  Dengan memasukkan `ftp-data.command contains "secret.zip"` pada display filter maka akan muncul list packet yang mengandung secret.zip, kemudian di export seperti cara nomor 7
  ![image](https://user-images.githubusercontent.com/36522826/134307390-3a0afda1-fd60-472a-bee5-08d604acc06e.png)
  Namun pada saat di buka masih terdapat password yang akan kita cari di soal selanjutnya

## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

  Yang pertama ialah memasukkan `ftp-data.command contains "history.txt"` pada filter display dan akan muncul packet yang mengandung history.txt yang kemudian jika di follow TCP stream
  ![image](https://user-images.githubusercontent.com/36522826/134307541-5fdd3db1-bee2-4fc8-ba47-293833216d6f.png)
  Maka akan muncul command linux untuk men-zip file Wanted.pdf dengan password yang ada pada file bukanapaapa.txt kemudian dilanjutkan dengan `ftp-data.command contains "bukanapaapa.txt"` untuk mencari file yang mengandung password secret.zip. Jika di follow TCP Stream packet tersebut maka akan muncul password zipnya.
  ![image](https://user-images.githubusercontent.com/36522826/134307666-400ea533-0fbe-4939-8b2b-d0b4560b9794.png)
  Password zipnya adalaha `D1b1langbukanapaapajugagapercaya`, dan jika menggunakan password ini untuk membuka file secret.zip maka akan muncul gambar poster luffy!
  ![image](https://user-images.githubusercontent.com/36522826/134307792-74410935-2e02-4b5c-aa31-22edf622454f.png)

## 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80! 

  Terdapat 3 kata kunci dari soal, yakni:
  - _mengambil_, berarti melakukan filter **capture**
  - _berasal_, berarti menggunakan `src`
  - _port 80_, berarti mencari `port 80`

  Langkah yang dilakukan yakni:
  - Pilih koneksi untuk difilter, disini menggunakan **Ethernet 2**
  - Set **Capture Filter** menjadi `src port 80`
    
    ![image](https://user-images.githubusercontent.com/43901559/134439743-e5f64e04-c14e-43ba-a92e-d5741aef10aa.png)
    
    ![image](https://user-images.githubusercontent.com/43901559/134439752-418f059b-c43c-4309-be47-05e571b6c632.png)

  - Hasil capture sebagai berikut
    
    ![image](https://user-images.githubusercontent.com/43901559/134439806-24697e6f-47b7-4fa5-8c17-ff53e5838c75.png)


## 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

  Terdapat 2 kata kunci dari soal, yakni:
  - _mengambil_, berarti melakukan filter **capture**
  - _port 21_, berarti mencari `port 21`

  Langkah yang dilakukan yakni:
  - Memilih koneksi **Adapter for loopback traffic capture**
  - Set **Capture Filter** menjadi `port 21`

    ![image](https://user-images.githubusercontent.com/43901559/134440012-96a6d653-64f9-4301-8f22-0f36b46e3923.png)

  - Hasil capture

    ![image](https://user-images.githubusercontent.com/43901559/134440023-0f0e72e3-5b5f-4c69-806d-44ed918b3899.png)


## 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

  Terdapat 2 kata kunci dari soal, yakni:
  - _menampilkan_, berarti melakukan filter **display**
  - _menuju_, berarti `dst`
  - _port 443_, berarti memfilter dari `port 443`

  Langkah yang dilakukan yakni:
  - Set **Display Filter** menjadi `tcp.dstport == 443 || udp.dstport == 443`

    ![image](https://user-images.githubusercontent.com/43901559/134441213-f544e186-c1d7-4359-9414-b85721c4af79.png)

  - Hasil capture

    ![image](https://user-images.githubusercontent.com/43901559/134441177-2ff8534b-2bef-448b-b7ce-988c41467ddb.png)


## 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

  Terdapat 3 kata kunci dari soal, yakni:
  - _mengambil_, berarti melakukan filter **capture**
  - _tujuan_, berarti `dst`
  - _kemenag.go.id_, berarti harus membuka website-nya agar bisa muncul di Wireshark ketika capture

  Langkah yang dilakukan yakni:
  - Pilih koneksi untuk di filter, disini menggunakan **Ethernet 2**
  - Set filter `dst host kemenag.go.id`

    ![image](https://user-images.githubusercontent.com/43901559/134441455-a3a1e09c-ebe2-4031-a38d-6cc857cffd7c.png)

  - Hasil capture

    ![image](https://user-images.githubusercontent.com/43901559/134441461-55d9c63b-a625-413a-b6a7-444b4bc609b3.png)


## 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

  Terdapat 3 kata kunci dari soal, yakni:
  - _mengambil_, berarti melakukan filter **capture**
  - _berasal_, berarti `src`
  - _ip kalian_, berarti harus menggunakan IP sendiri sebagai filter

  Langkah yang dilakukan, yakni:
  - Mencari IP sendiri

    ![image](https://user-images.githubusercontent.com/43901559/134441617-9cc2a54d-a145-4213-9d3a-b7ae6ac2a2a5.png)

  - Pilih koneksi untuk di filter, disini menggunakan **Ethernet 2**
  - Set filter `ip src {IP}`

    ![image](https://user-images.githubusercontent.com/43901559/134441633-eb08d977-f11e-4624-b24f-743912b94f10.png)

  - Hasil capture

    ![image](https://user-images.githubusercontent.com/43901559/134441651-8c5bf2d0-e35f-4900-bafb-82e904cdb2f9.png)
