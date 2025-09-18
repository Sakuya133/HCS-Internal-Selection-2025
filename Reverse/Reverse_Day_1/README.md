## Reverse Day 1 - [100 point]


> Ketika pertama kali belajar reverse engineering, biasanya challenge bisa di-solved cukup dengan strings. Sayangnya, kali ini strings saja belum bisa untuk mendapatkan flag.

> Author: erzyyyy

- Explanation
  <p>Diberikan sebuah file "chall" tanpa extension, karena ini soal reverse, saya coba buka menggunakan ghidra</p>
<p>Pada Ghidra terdapat baris kode yang rada mencurigakan</p>

```
local_40 = *(long *)(in_FS_OFFSET + 0x28); local_58 = 0x3b283b2c250d1d16; local_50 = 0x3b012d37013b2d2c; local_48 = 0x2727243f; local_44 = 0x2727; local_42 = 0x23; local_71 = 0x5e; local_80 = param_1; iVar2 = a(); local_68 = (long)(iVar2 + 1) + -1; uVar3 = (((long)(iVar2 + 1) + 0xfU) / 0x10) * 0x10; for (puVar4 = auStack_88; puVar4 != auStack_88 + -(uVar3 & 0xfffffffffffff000); puVar4 = puVar4 + -0x1000) { *(undefined8 *)(puVar4 + -8) = *(undefined8 *)(puVar4 + -8); } lVar1 = -(ulong)((uint)uVar3 & 0xfff); local_60 = puVar4 + lVar1; if ((uVar3 & 0xfff) != 0) { *(undefined8 *)(puVar4 + ((ulong)((uint)uVar3 & 0xfff) - 8) + lVar1) = *(undefined8 *)(puVar4 + ((ulong)((uint)uVar3 & 0xfff) - 8) + lVar1); } local_70 = 0; while( true ) { *(undefined8 *)(puVar4 + lVar1 + -8) = 0x101320; iVar2 = a(); if (iVar2 <= local_70) break; local_60[local_70] = *(byte *)((long)&local_58 + (long)local_70) ^ local_71; local_70 = local_70 + 1; } *(undefined8 *)(puVar4 + lVar1 + -8) = 0x10132a; iVar2 = a(); local_60[iVar2] = 0; local_6c = 0; while( true ) { *(undefined8 *)(puVar4 + lVar1 + -8) = 0x101380; iVar2 = a(); if (iVar2 <= local_6c) break; if (*(char *)(local_80 + local_6c) != local_60[local_6c]) { *(undefined8 *)(puVar4 + lVar1 + -8) = 0x10136d; puts("Wrong!"); /* WARNING: Subroutine does not return */ *(undefined8 *)(puVar4 + lVar1 + -8) = 0x101377; exit(1); } local_6c = local_6c + 1; } *(undefined8 *)(puVar4 + lVar1 + -8) = 0x101394; puts("GG!, dont forget to submit your flag!"); if (local_40 != *(long *)(in_FS_OFFSET + 0x28)) { /* WARNING: Subroutine does not return */ __stack_chk_fail(); } return;
```
<p>Deskripsi: Program menyimpan beberapa konstanta (8+8+4+2+1 byte), membaca byte per byte dalam little-endian dari konstanta-konstanta itu, lalu XOR setiap byte dengan 0x5e untuk membentuk string target (local_60). Setelah di-null-terminate, program membandingkan byte-per-byte input (param_1) dengan local_60. Jika cocok → cetak “GG!, dont forget to submit your flag!”, kalau tidak → “Wrong!”.</p>

### decode.py
```py
import struct

vals = [
    0x3b283b2c250d1d16,  
    0x3b012d37013b2d2c,  
    0x2727243f,          
    0x2727,              
    0x23                 
]

b = b''
b += struct.pack('<Q', vals[0])
b += struct.pack('<Q', vals[1])
b += struct.pack('<I', vals[2])
b += struct.pack('<H', vals[3])
b += struct.pack('<B', vals[4])

key = 0x5e
decoded = bytes([x ^ key for x in b])
print(decoded.decode())

```
  


## Flag = HCS{reverse_is_eazyyyy}








  <br>
  <br>
