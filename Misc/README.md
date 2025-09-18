## decodescii - [491 point]


> A new threat actor has recently been identified running amok in the depths of the dark web. Help us catch them.

> Author: kek.c

- Explanation
<p>Ini adalah sebuah challenge, yang terdiri dari 3 kasus/pertanyaan yang perlu dijawab untuk mendapatkan flag</p>

> 1. THE WEIRD STRING...
>  We intercepted this IRC communication from one of their members during a C2 authentication, we believe it contains the key to their C2. Help us crack it.
22 59 34 6e 6b 33 33 20 5a 33 72 30 20 46 75 6c 6c 20 35 37 30 70 20 20 35 33 76 33 6e 20 48 30 37 33 6c 20 37 68 72 33 33 20 20 4b 31 6c 30 20 37 68 72 33 33 20 59 34 6e 6b 33 33 20 20 30 6e 33 20 46 31 76 33 20 20 30 6e 33 20 37 68 72 33 33 20 30 6e 33 20 37 77 30 20 22
-------------
<p>Kita coba identifikasi kumpulan bilangan tersebut dengan cipher identifier, dan didapat, bilangan tersebut merupakan string yang di encode menggunakan HEX</p>

```
22 59 34 6e 6b 33 33 20 5a 33 72 30 20 46 75 6c 6c 20 35 37 30 70 20 20 35 33 76 33 6e 20 48 30 37 33 6c 20 37 68 72 33 33 20 20 4b 31 6c 30 20 37 68 72 33 33 20 59 34 6e 6b 33 33 20 20 30 6e 33 20 46 31 76 33 20 20 30 6e 33 20 37 68 72 33 33 20 30 6e 33 20 37 77 30 20 22

```
### From hex

```
"Y4nk33 Z3r0 Full 570p  53v3n H073l 7hr33  K1l0 7hr33 Y4nk33  0n3 F1v3  0n3 7hr33 0n3 7w0 "
```
<p> String yang didapat masih terlihat seperti cipher text, kita coba identifikasi lagi, dan didapat string tersebut di encode menggunakan Leet Speak 1337. Metode ini kita ulang terus hingga menemukan sebuah jawaban </p>

### Leet Speak 1337
```
YAnkEE ZErO Full STOp  SEvEn HOTEl ThrEE  KIlO ThrEE YAnkEE  OnE FIvE  OnE ThrEE OnE TwO
```
### NATO Phonetic Alphabet
```
Y 0 FULL . 7 H 3 K 3 Y 1 5 1 3 1 2
```
<p>Pada string tersebut, terlihat seperti Yo FULL the key is 1312 </p>

#### Jawaban 1 = 1312

> 2. Asset?
>  Continuing the investigation, the actors seems to have caught on and changed the cover of their messages.
>  We believe this contains a malicious binary they're about to send. Help us locate it on the web, provide the link.
---------
```
3G4P47S44:8D7/DR44+3EEB6S44EECM9EM-DZED1Q5LQE0/DZEDT44S44+8DA44ZEDGEC3EF2LE1Q5-EDJ:4944SUEF1A TAI1AWL6A69L7BG%63M6U6AQIBXY9UTAX+9 TA8*6PTAA+84X6VX8CIA71A5X60C9DH8K+997BWYATTAYY9HX7HX7HX7Y0
```
<p>Sama seperti soal sebelumnya, di identifikasi menggunakan cipher identifier, hingga menemukan jawaban</p>

### From Base45
```
"w8, think som1s tappin in, sendin u the binary rq, it's at OVTWOY3GHIXS643WPFZGMLTQNZTW6YTLFZ5GE4RPON5HIMBRNMXGU4TPMM======"
```
### From base32
```
uggcf://svyrf.pngobk.zbr/szt01k.jroc
```
### caesar cipher
```
https://files.catbox.moe/fmg01x.webp
```
#### Jawaban 2 = https://files.catbox.moe/fmg01x.webp

> 3. Final Attack
>  Investigating the binary, it seems to be a ransomware polyglot. Our forensics team found this encryption software which validates the key with the following program, help us crack it!
---------------
```
b'aHR0cHM6Ly9hamFuc2UubWUvYXNjaWlkb3RzLz9jb2RlPVlGUkZUVlZMUVU0Z1NVNVFWVlFnVkVWU1MwVkRTVXdnV1VGT1J5Qk5SVTFGVGxWSVNTQlFVazlIVWtGTklFbE9TV0FLSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnWDE1ZklDQWdJQ0FnSUNCZlgxOWZDaUFnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0JnVUU5V09pQlpUMVVnVkZKWklGUlBJRVJQWUNBZ0lDQWdJQ0FnSUNBZ0lDQWdMeTA5SzF4Y0lDQWdMeThqUFNzclBWd0tJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJR0JCVTBOSlNTQkJVbFFnU1U0Z01qUklMR0FnSUNBZ0lDQWdJQ0FnSUNBZ0xpMGpNVEF3TURBd09ESTROamt5TmpReU5UVXdOSFlLSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUdCUVRGTWdSRTlPSjFRZ1IxSkpURXdnVFVVZ09qeGdJQ0FnSUNBZ0lDQWdmQ002UFQwOUx5c3JLMTlmSzE5Zkt5c3RMUzB0UER4Y0NpQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUh3dkxWOHJMVHdyWEQxZkx6MDlPaUFnSUNBZ0lDQmNmQW9nSUNBZ0xpMGpQM1pmSUNBZ0lDQmZYeUFnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQXZMejByTHlBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBS0lDQWdJQ0FnTHlCY0xWd2dJQ0F2WEMxY0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNCZlgxOWZYMTlmWHlBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnZkNBZ0lDQWdZRWhKVGxRNklGbFBWU0JOUVZrZ1RrOVVJRmRCVGxSZ0NpQWdJQ0FnSUNCY0lGeGNYQ0FnWENCY1hGd2dJQ0FnSUNCZlgxOWZYMTlmWHlNdkxTMHRMUzB0TFMwdFhDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUh3Z0lDQWdJR0JVVHlCQ1VsVlVSU0JVU0VsVExDQlhTRUZVSjFNZ1FVNWdDaUFnSUNBZ0lDQWdYQ0JjWEMwcUxTMHRMUzFjTFM4dExTMHFMUzB0TFMwdExTMWNQaTB0ZGw5ZlgxOWZMeUFnSUNBZ0lDQWdJQ0FnSUNBZ0lId2dJQ0FnSUdCRlJrWkpRMGxGVGxRZ1YwRlpJRlJQSUVkUElGUklVbFZnQ2lBZ0lDQWdJQ0FnSUZ3Z1hDMC1JelF4TFZzcVhYd2dmQ0JjS2lNeUxTMHRMUzByWG5ZdGZGeGZYMTlmWDE4Z0lDQWdJQ0FnSUNBZ0lDQWdJSHdnSUNBZ0lHQkJJRTFQVGs5VVQwNUpReUJHS0hncElFUlBUVUZKVGo5Z0NpQWdJQ0FnSUNBZ0lDQmNJRnd0WENBZ1hDQmNMUzhnSUZ3Z1hGd2dJQ0FnSUNCY1gxOTdYbjB0TFMwdExYWmNJQ0FnSUNBZ0lDQWdJQ0FnSUh3S0lDQWdJQ0FnSUNBZ0lDQmNMMTh2SUNBZ1hDOWZMeUFnSUZ3Z1hDMGpORFE1TlRSZlBpdGZYMTlmWDNaZmZGOWNJQ0FnSUNBZ0lDQWdJQ0FnZkNBZ0lDOHRKQ2RQVFVjZ1FrVlNTRUZUU1V3Z1BETW5DaUFnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdYRjljWDE5ZlgxOHZJQ0FnSUM5MkxYc3FmVHhmTHlBZ0lDQWdJQ0FnSUNBZ0lId2dMaTEtTFNRblRXRnphV2dnYTNWeVlXNW5JSEJoYXlBNlBDY0tJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0FnSUNBZ0lDQWdJQ0I4WHo1ZlgxOWZYMTh0TFMwdExTMHRMUzB0TFMxN1IzMHRMVjRL'
```
<p>Kita coba identifikasi cipher text ini</p>

### From Base64

```
https://ajanse.me/asciidots/?code=YFRFTVVLQU4gSU5QVVQgVEVSS0VDSUwgWUFORyBNRU1FTlVISSBQUk9HUkFNIElOSWAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgX15fICAgICAgICBfX19fCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBgUE9WOiBZT1UgVFJZIFRPIERPYCAgICAgICAgICAgICAgLy09K1xcICAgLy8jPSsrPVwKICAgICAgICAgICAgICAgICAgICAgICAgICAgIGBBU0NJSSBBUlQgSU4gMjRILGAgICAgICAgICAgICAgLi0jMTAwMDAwODI4NjkyNjQyNTUwNHYKICAgICAgICAgICAgICAgICAgICAgICAgICAgIGBQTFMgRE9OJ1QgR1JJTEwgTUUgOjxgICAgICAgICAgfCM6PT09LysrK19fK19fKystLS0tPDxcCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHwvLV8rLTwrXD1fLz09OiAgICAgICBcfAogICAgLi0jP3ZfICAgICBfXyAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAvLz0rLyAgICAgICAgICAgICAgICAgICAKICAgICAgLyBcLVwgICAvXC1cICAgICAgICAgICAgICAgICBfX19fX19fXyAgICAgICAgICAgICAgICAgfCAgICAgYEhJTlQ6IFlPVSBNQVkgTk9UIFdBTlRgCiAgICAgICBcIFxcXCAgXCBcXFwgICAgICBfX19fX19fXyMvLS0tLS0tLS0tXCAgICAgICAgICAgICAgIHwgICAgIGBUTyBCUlVURSBUSElTLCBXSEFUJ1MgQU5gCiAgICAgICAgXCBcXC0qLS0tLS1cLS8tLS0qLS0tLS0tLS1cPi0tdl9fX19fLyAgICAgICAgICAgICAgIHwgICAgIGBFRkZJQ0lFTlQgV0FZIFRPIEdPIFRIUlVgCiAgICAgICAgIFwgXC0-IzQxLVsqXXwgfCBcKiMyLS0tLS0rXnYtfFxfX19fX18gICAgICAgICAgICAgIHwgICAgIGBBIE1PTk9UT05JQyBGKHgpIERPTUFJTj9gCiAgICAgICAgICBcIFwtXCAgXCBcLS8gIFwgXFwgICAgICBcX197Xn0tLS0tLXZcICAgICAgICAgICAgIHwKICAgICAgICAgICBcL18vICAgXC9fLyAgIFwgXC0jNDQ5NTRfPitfX19fX3ZffF9cICAgICAgICAgICAgfCAgIC8tJCdPTUcgQkVSSEFTSUwgPDMnCiAgICAgICAgICAgICAgICAgICAgICAgICAgXF9cX19fX18vICAgIC92LXsqfTxfLyAgICAgICAgICAgIHwgLi1-LSQnTWFzaWgga3VyYW5nIHBhayA6PCcKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB8Xz5fX19fX18tLS0tLS0tLS0tLS17R30tLV4K
```
<p>Hasil plain textnya mengarahkan kita pada suatu website</p>
<img width="2355" height="1244" alt="image" src="https://github.com/user-attachments/assets/65323000-9ec1-4c34-a79a-8120988d21b7" />
<br>
<p>Deskripsi: Website tersebut adalah online compiler untuk bahasa Pemrograman AsciiDots. Pada web tersebut terdapat program yang menerima input user, jika input user lebih dari target maka akan di print "OMG BERHASIL <3", sebaliknya "Masih kurang pak :<", jawaban untuk soal 3, yaitu bilangan paling kecil yang jika di input akan menghasilkan output "OMG BERHASIL <3" </p>
<p>Eksekusi: Untuk soal ini, saya menggunakan metode Binary search, dimana saya mencoba bilangan kelipatan 10, yang output berhasil, setelahnya saya melakukan /2, namun jika pembagian berikutnya outputnya kurang, saya akan melakukan penjumlahan + 1/2 %</p>

  #### Contoh 
```
10000 berhasil
5000 kurang
7500 berhasil
dll
```
<p>Lakukan hal tersebut hingga jawaban di dapat</p>

#### Jawaban 3 = 115036

   
## Flag = HCS{weird_4hhh_fl4gzz_ye_aw1kw0k_1cb33472-3741-49cf-b934-216c7a5ca567}



