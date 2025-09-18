## elefay - [331 point]


> Flag file in /flag.txt

> Author: vannn



- Explanation
<p>Kita diarahkan apda sebuah website</p>
<img width="1499" height="453" alt="image" src="https://github.com/user-attachments/assets/6b360073-8aba-4d59-a08a-fa569e878f02" />

<p>Pada deskripsi soal, terlihat flag ada pada page /flag.txt</p>
<p>Code mencoba mencegah directory traversal dan akses flag.txt dengan dua preg_replace ad-hoc yang menghapus literal ../ dan flag.txt. Karena penghapusan dilakukan non-overlapping dan tanpa canonicalization, input yang terstruktur dapat direkombinasi menjadi path valid ../../../.../flag.txt. Akibatnya file_exists() true dan highlight_file() mengekspose isi flag.</p>

#### Path yang saya gunakan

```
http://8ec15533-7a4a-4d3b-843f-68c33a7f08db.chall.intersec.hcs-team.com/?file=../../../../////flflag.txtag.txt
```

<img width="1866" height="120" alt="image" src="https://github.com/user-attachments/assets/fab859e0-8563-4ac7-a616-a86c6fd5f071" />




## Flag = HCS{k4mu_k0k_j4g0_b4ng3t_s1h_b4n9_m44f_ya_soalny4_t3rlalu_g4mp4ng_bu4t_k4mu_:3_c3e7afb5-9ef8-4883-abcd-d23db8f2f2ac}

