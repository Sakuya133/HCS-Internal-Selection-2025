## strings - [100 point]


> Soal yang wajib ada di CTF pemerintah

> Author: Hanz

- Explanation

  `Pada challenge ini, kita diberikan 1 file "chall", tanpa extension apapun `
  <br>
  <img width="248" height="98" alt="Screenshot from 2025-09-18 06-25-20" src="https://github.com/user-attachments/assets/1ad253d5-070c-4d6a-99f1-d9cd98f8729c" /> <br>
  ##### Gambar: file chal
  <br>
   `Jika kita perhatikan judul soal ini, tertulis "strings", linux/unix sendiri memiliki command strings, yang berfungsi mengekstrak teks yang bisa dibaca manusia dari file yang ditarget. Kita coba pendekatan tersebut pada file "chal".`
```
   /lib64/ld-linux-x86-64.so.2
__libc_start_main
__cxa_finalize
libc.so.6
GLIBC_2.2.5
GLIBC_2.34
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
PTE1
u+UH
HCS{ctf_
gjls_
hadiah_el
it__
ayaya}
;*3$"
GCC: (Debian 12.2.0-14+deb12u1) 12.2.0
Scrt1.o
__abi_tag
crtstuff.c
deregister_tm_clones
__do_global_dtors_aux
completed.0
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
main.c
__FRAME_END__
_DYNAMIC
__GNU_EH_FRAME_HDR
_GLOBAL_OFFSET_TABLE_
__libc_start_main@GLIBC_2.34
_ITM_deregisterTMCloneTable
_edata
_fini
__data_start
__gmon_start__
__dso_handle
_IO_stdin_used
_end
__bss_start
main
__TMC_END__
_ITM_registerTMCloneTable
hihi
__cxa_finalize@GLIBC_2.2.5
_init
.symtab
.strtab
.shstrtab
.interp
.note.gnu.property
.note.gnu.build-id
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.init
.plt.got
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.got.plt
.data
.bss
.comment
```
##### Gambar: Hasil dari "strings chal"
`Ada sebuah kumpulan strings yang dimulai dengan format "HCS{" dan diakhiri dengan "}", itulaj flag dari soal ini`

## Flag = HCS{ctf_gjls_hadiah_elit__ayaya}







  <br>
  <br>
