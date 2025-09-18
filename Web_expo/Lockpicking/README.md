## Lockpicking - [139 point]


> I just made a vault to store my treasured things, it should be very secure right?
> http://intersec.hcs-team.com:30003

> Author: anarchistx


- Explanation

<p>Kita diarahkan pada sebuah website</p>
<img width="1638" height="1228" alt="image" src="https://github.com/user-attachments/assets/b52ce732-f71b-4c49-be60-e208c6adb7d4" />

<br>
<p>Terlihat ada input username dan password, jadi saya menggunakan pendekatan SQL Injection. Saya menggunakan template yang saya ambil dari repositori, https://github.com/payloadbox/sql-injection-payload-list</p>

#### Input yang saya gunakan
```
" OR 1 = 1 -- - ' OR '' = '
```
<p>Setelah berhasil, kita diarahkan pada input berikutnya, yang kurang lebih sama seperti page sebelumnya, hanya disini ada penyaringan dimana ada beberapa input yang tidak boleh seperti or, and, union, select, from, where, information_schema, --, #. Jadi saya menggunakan input yang tidak ada chars tersebut</p>


<img width="906" height="776" alt="image" src="https://github.com/user-attachments/assets/7efe1700-206a-47f3-874f-80a956f7e8fc" />

#### Input yang saya gunakan

```
'&'
```

<img width="1098" height="1076" alt="image" src="https://github.com/user-attachments/assets/bf8d5690-612b-463c-a959-756f5d8378ee" />


## Flag =HCS{d1d_y0u_just_unl0ck_th1s_v4ult?_c0ngr4tz_th3n_y0u_th13f}


