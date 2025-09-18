## xoxo - [100 point]


> They tried to keep a secret in the relationship, but their habits gave everything away.

> Author: Vaa

- Explanation
 <p>Diberikan sebuah file Python, yang berisi algoritma dan output dari program tersebut, yang kemungkinan berisi flag</p>

 ### chall.py
 ```py
import os
from Crypto.Util.number import long_to_bytes
from Crypto.Util.strxor import strxor

FLAG = "HCS{placeholder}"

key = os.urandom(4) * 9

flag_bytes = FLAG.encode()

c = strxor(flag_bytes, key[:len(flag_bytes)])
print(c.hex())
# d61a7019ec6a5351aa2d120cf9065b52ec061211c12d1352c12e1056f5065b0de6365e

```
<p>kunci 4-byte diulang setiap 4 byte, dan format flag dimulai HCS{, jadi kita bisa mendapatkan 4 byte kunci dengan XOR antara 4 byte pertama ciphertext dan string HCS{}, lalu pakai kunci itu berulang untuk mendekripsi seluruh ciphertext.</p>

### decode.py

```py
ct_hex = "d61a7019ec6a5351aa2d120cf9065b52ec061211c12d1352c12e1056f5065b0de6365e"
ct = bytes.fromhex(ct_hex)

prefix = b"HCS{"
key4 = bytes(ct[i] ^ prefix[i] for i in range(4))

full_key = key4 * ((len(ct) + 3) // 4)
pt = bytes(ct[i] ^ full_key[i] for i in range(len(ct)))
print(pt.decode())

```
 
 
 
## Flag = HCS{r3p34t1ng_x0r_1s_t00_w34k_xoxo}


