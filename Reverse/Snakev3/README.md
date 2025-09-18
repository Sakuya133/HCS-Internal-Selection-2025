## Snakev3 - [100 point]


> pawang ular

> ps, run dengan menggunakan command python -m http.server di directory yang sama dengan file file yang diberikan

> Author: requiiem

- Explanation
<p>Diberikan sebuah folder yang berisi file html, css, javascript, dan assembly, jika dijalankan maka akan ada game ular</p>
<img width="1139" height="1281" alt="image" src="https://github.com/user-attachments/assets/ca741153-30fa-4430-b308-4014e1dc8ba6" />

<p>Jika dilihat dari kode Javascript, kemungkinan flag ada pada kode assembly, dan didapat ssaat kita mencapai skor tertentu, namun kode assembly tersebut tidak bisa dibuka secara langsung di terminal</p>
<p>Tapi jika kita jalankan localhost dan dilihat pada file game.wasm, file tersebut akhirnya menampakan diri</p>

```
(module $game.wasm
  (memory $memory (;0;) (export "memory") 2)
  (global $__stack_pointer (;0;) (mut i32) (i32.const 66688))
  (global $score (;1;) (export "score") i32 (i32.const 1128))
  (global $integrity (;2;) (export "integrity") i32 (i32.const 1132))
  (global $seed (;3;) (export "seed") i32 (i32.const 1136))
  (global $encrypted_flag (;4;) (export "encrypted_flag") i32 (i32.const 1072))
  (global $key (;5;) (export "key") i32 (i32.const 1104))
  (global $__dso_handle (;6;) (export "__dso_handle") i32 (i32.const 1024))
  (global $__data_end (;7;) (export "__data_end") i32 (i32.const 1140))
  (global $__stack_low (;8;) (export "__stack_low") i32 (i32.const 1152))
  (global $__stack_high (;9;) (export "__stack_high") i32 (i32.const 66688))
  (global $__global_base (;10;) (export "__global_base") i32 (i32.const 1024))
  (global $__heap_base (;11;) (export "__heap_base") i32 (i32.const 66688))
  (global $__heap_end (;12;) (export "__heap_end") i32 (i32.const 131072))
  (global $__memory_base (;13;) (export "__memory_base") i32 (i32.const 0))
  (global $__table_base (;14;) (export "__table_base") i32 (i32.const 1))
  (func $__wasm_call_ctors (;0;) (export "__wasm_call_ctors")
  )
  (func $init (;1;) (export "init") (param $var0 i32)
    i32.const 0
    local.get $var0
    i32.store offset=1136
    i32.const 0
    local.get $var0
    i32.store offset=1132
    i32.const 0
    i32.const 0
    i32.store offset=1128
  )
  (func $update_on_eat (;2;) (export "update_on_eat")
    (local $var0 i32)
    i32.const 0
    i32.const 0
    i32.load offset=1128
    i32.const 9
    i32.add
    local.tee $var0
    i32.store offset=1128
    i32.const 0
    i32.const 0
    i32.load offset=1136
    local.get $var0
    i32.add
    i32.const 0
    i32.load offset=1132
    i32.const 5
    i32.rotl
    i32.xor
    i32.store offset=1132
  )
  (func $get_flag (;3;) (export "get_flag") (param $var0 i32)
    block $label1
      block $label0
        i32.const 0
        i32.load offset=1128
        i32.const 999999
        i32.ne
        br_if $label0
        i32.const 0
        i32.load offset=1132
        i32.const 1904218052
        i32.eq
        br_if $label1
      end $label0
      local.get $var0
      i32.const 31
      i32.add
      i32.const 0
      i64.load offset=1055 align=1
      i64.store align=1
      local.get $var0
      i32.const 24
      i32.add
      i32.const 0
      i64.load offset=1048
      i64.store align=1
      local.get $var0
      i32.const 16
      i32.add
      i32.const 0
      i64.load offset=1040
      i64.store align=1
      local.get $var0
      i32.const 8
      i32.add
      i32.const 0
      i64.load offset=1032
      i64.store align=1
      local.get $var0
      i32.const 0
      i64.load offset=1024
      i64.store align=1
      return
    end $label1
    local.get $var0
    i32.const 0
    i32.load8_u offset=1104
    i32.const 0
    i32.load8_u offset=1072
    i32.xor
    i32.store8
    local.get $var0
    i32.const 0
    i32.load8_u offset=1105
    i32.const 0
    i32.load8_u offset=1073
    i32.xor
    i32.store8 offset=1
    local.get $var0
    i32.const 0
    i32.load8_u offset=1106
    i32.const 0
    i32.load8_u offset=1074
    i32.xor
    i32.store8 offset=2
    local.get $var0
    i32.const 0
    i32.load8_u offset=1107
    i32.const 0
    i32.load8_u offset=1075
    i32.xor
    i32.store8 offset=3
    local.get $var0
    i32.const 0
    i32.load8_u offset=1108
    i32.const 0
    i32.load8_u offset=1076
    i32.xor
    i32.store8 offset=4
    local.get $var0
    i32.const 0
    i32.load8_u offset=1109
    i32.const 0
    i32.load8_u offset=1077
    i32.xor
    i32.store8 offset=5
    local.get $var0
    i32.const 0
    i32.load8_u offset=1110
    i32.const 0
    i32.load8_u offset=1078
    i32.xor
    i32.store8 offset=6
    local.get $var0
    i32.const 0
    i32.load8_u offset=1111
    i32.const 0
    i32.load8_u offset=1079
    i32.xor
    i32.store8 offset=7
    local.get $var0
    i32.const 0
    i32.load8_u offset=1112
    i32.const 0
    i32.load8_u offset=1080
    i32.xor
    i32.store8 offset=8
    local.get $var0
    i32.const 0
    i32.load8_u offset=1113
    i32.const 0
    i32.load8_u offset=1081
    i32.xor
    i32.store8 offset=9
    local.get $var0
    i32.const 0
    i32.load8_u offset=1114
    i32.const 0
    i32.load8_u offset=1082
    i32.xor
    i32.store8 offset=10
    local.get $var0
    i32.const 0
    i32.load8_u offset=1115
    i32.const 0
    i32.load8_u offset=1083
    i32.xor
    i32.store8 offset=11
    local.get $var0
    i32.const 0
    i32.load8_u offset=1116
    i32.const 0
    i32.load8_u offset=1084
    i32.xor
    i32.store8 offset=12
    local.get $var0
    i32.const 0
    i32.load8_u offset=1117
    i32.const 0
    i32.load8_u offset=1085
    i32.xor
    i32.store8 offset=13
    local.get $var0
    i32.const 0
    i32.load8_u offset=1118
    i32.const 0
    i32.load8_u offset=1086
    i32.xor
    i32.store8 offset=14
    local.get $var0
    i32.const 0
    i32.load8_u offset=1119
    i32.const 0
    i32.load8_u offset=1087
    i32.xor
    i32.store8 offset=15
    local.get $var0
    i32.const 0
    i32.load8_u offset=1120
    i32.const 0
    i32.load8_u offset=1088
    i32.xor
    i32.store8 offset=16
    local.get $var0
    i32.const 0
    i32.load8_u offset=1121
    i32.const 0
    i32.load8_u offset=1089
    i32.xor
    i32.store8 offset=17
    local.get $var0
    i32.const 0
    i32.load8_u offset=1122
    i32.const 0
    i32.load8_u offset=1090
    i32.xor
    i32.store8 offset=18
    local.get $var0
    i32.const 0
    i32.load8_u offset=1123
    i32.const 0
    i32.load8_u offset=1091
    i32.xor
    i32.store8 offset=19
    local.get $var0
    i32.const 0
    i32.load8_u offset=1124
    i32.const 0
    i32.load8_u offset=1092
    i32.xor
    i32.store8 offset=20
    local.get $var0
    i32.const 0
    i32.load8_u offset=1125
    i32.const 0
    i32.load8_u offset=1093
    i32.xor
    i32.store8 offset=21
    local.get $var0
    i32.const 0
    i32.load8_u offset=1126
    i32.const 0
    i32.load8_u offset=1094
    i32.xor
    i32.store8 offset=22
  )
  (data (i32.const 1024) "hey, no \e2\98\9d\ef\b8\8f no \e2\98\9d\ef\b8\8f no \e2\98\9d\ef\b8\8f yah\00")
  (data (i32.const 1072) "?&?\18\0d\0c\07&+\1c\00\12\01\17,&\1a(\02\1f\18\1f\00\00\00\00\00\00\00\00\00\00welcome_to_the_RE_club\00")
)
```
<p>Dari file tersebut dapat diambil 2 variabel untuk decode.py , encrypted_flag_offset = 1072
key_offset = 1104</p>

### decode.py

```py

wasm_file = "game.wasm"


encrypted_flag_offset = 1072
key_offset = 1104
flag_length = 100000  

with open(wasm_file, "rb") as f:
    wasm = f.read()

encrypted_flag = wasm[encrypted_flag_offset:encrypted_flag_offset + flag_length]
key = wasm[key_offset:key_offset + flag_length]


flag_bytes = bytes([b ^ k for b, k in zip(encrypted_flag, key)])


flag = flag_bytes.decode('utf-8', errors='ignore')
print("Flag:", flag)

```
<br>

### output
<img width="1565" height="596" alt="image" src="https://github.com/user-attachments/assets/eb5c8d20-d952-4cf7-9f6a-5cebf74eff87" />

## Flag = HCS{baby_s_first_wasm}








  <br>
  <br>
