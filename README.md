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

11.
12.
13.
14.
15.
16.
