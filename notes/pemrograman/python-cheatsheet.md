# Cheat Sheet Python

Ringkasan sintaks Python 3 untuk pemula: dasar, list/dict, fungsi, OOP, dan file handling.

## Daftar Isi

- [Dasar](#dasar)
- [Kondisional dan Perulangan](#kondisional-dan-perulangan)
- [String](#string)
- [List](#list)
- [Dictionary](#dictionary)
- [Tuple dan Set](#tuple-dan-set)
- [Fungsi](#fungsi)
- [OOP](#oop)
- [File Handling](#file-handling)
- [Error Handling](#error-handling)
- [Modul](#modul)

## Dasar

```python
# ini komentar
nama = "Farhan"      # str (teks)
umur = 20            # int (bilangan bulat)
tinggi = 1.7         # float (desimal)
mahasiswa = True     # bool (True / False)
kosong = None        # tidak ada nilai

print(type(umur))    # <class 'int'>
```

**Konversi tipe**

```python
int("5")      # 5
float("3.5")  # 3.5
str(10)       # "10"
bool(0)       # False (0, "", [], None dianggap False)
```

**Operator**

| Jenis | Operator | Contoh |
|---|---|---|
| Aritmatika | `+  -  *  /  //  %  **` | `7 / 2` = 3.5, `7 // 2` = 3, `7 % 2` = 1, `2 ** 3` = 8 |
| Perbandingan | `==  !=  <  >  <=  >=` | `5 == 5` → True |
| Logika | `and  or  not` | `umur > 17 and mahasiswa` |
| Keanggotaan | `in  not in` | `"a" in "apel"` → True |

**Input dan output**

```python
nama = input("Nama: ")        # input selalu berupa str
umur = int(input("Umur: "))   # ubah ke int jika perlu
print(f"Halo, {nama}! Umurmu {umur} tahun.")   # f-string
```

> Python memakai **indentasi** (biasanya 4 spasi) untuk menandai blok kode, bukan kurung kurawal.

## Kondisional dan Perulangan

```python
nilai = 85
if nilai >= 80:
    print("A")
elif nilai >= 70:
    print("B")
else:
    print("C")
```

```python
# for
for i in range(5):          # 0,1,2,3,4
    print(i)

range(1, 6)                 # 1..5
range(0, 10, 2)             # 0,2,4,6,8

# while
n = 0
while n < 3:
    print(n)
    n += 1

# break = berhenti, continue = lompat ke putaran berikutnya
for i in range(10):
    if i == 3:
        continue
    if i == 6:
        break
    print(i)

# enumerate dan zip
for idx, buah in enumerate(["apel", "jeruk"]):
    print(idx, buah)

for a, b in zip([1, 2], ["x", "y"]):
    print(a, b)
```

## String

```python
s = "  Belajar Python  "
s.strip()               # "Belajar Python"
s.upper()               # "  BELAJAR PYTHON  "
s.lower()
s.replace("Python", "AI")
s.split()               # ["Belajar", "Python"]
",".join(["a", "b"])    # "a,b"
s.startswith("  B")     # True
len(s)

t = "Python"
t[0]        # "P"
t[-1]       # "n"
t[0:3]      # "Pyt"
```

## List

Berurutan, bisa diubah, boleh berisi tipe campuran.

```python
buah = ["apel", "jeruk"]

buah.append("mangga")       # tambah di akhir
buah.insert(1, "pisang")    # sisipkan di indeks 1
buah.remove("apel")         # hapus berdasarkan nilai
buah.pop()                  # hapus dan ambil elemen terakhir

buah[0]                     # elemen pertama
buah[-1]                    # elemen terakhir
buah[0:2]                   # slicing

len(buah)
"jeruk" in buah             # True / False
sorted(buah)                # list baru yang terurut
buah.sort()                 # urutkan di tempat
buah.reverse()
```

**List comprehension**

```python
kuadrat = [x ** 2 for x in range(5)]           # [0, 1, 4, 9, 16]
genap = [x for x in range(10) if x % 2 == 0]   # [0, 2, 4, 6, 8]
```

## Dictionary

Pasangan kunci-nilai.

```python
mhs = {"nama": "Farhan", "umur": 20}

mhs["nama"]                 # "Farhan"
mhs.get("ipk", 0)           # 0 (nilai default jika kunci tidak ada)
mhs["jurusan"] = "Bisnis"   # tambah / ubah
del mhs["umur"]             # hapus

"nama" in mhs               # True (cek kunci)
mhs.keys()
mhs.values()

for kunci, nilai in mhs.items():
    print(kunci, nilai)

# dict comprehension
{x: x ** 2 for x in range(3)}   # {0: 0, 1: 1, 2: 4}
```

## Tuple dan Set

```python
koordinat = (10, 20)        # tuple: tidak bisa diubah
x, y = koordinat            # unpacking

unik = set([1, 1, 2, 3])    # set: {1, 2, 3}, tanpa duplikat
unik.add(4)
```

## Fungsi

```python
def sapa(nama, sapaan="Halo"):
    """Mengembalikan kalimat sapaan."""
    return f"{sapaan}, {nama}!"

sapa("Ani")                  # "Halo, Ani!"
sapa("Ani", sapaan="Hai")    # "Hai, Ani!"
```

```python
# jumlah argumen bebas
def jumlah(*angka):
    return sum(angka)

jumlah(1, 2, 3)              # 6

def info(**data):
    for k, v in data.items():
        print(k, v)

info(nama="Ani", umur=20)

# lambda (fungsi satu baris)
kuadrat = lambda x: x ** 2
kuadrat(4)                   # 16
```

> Fungsi tanpa `return` mengembalikan `None`.

## OOP

```python
class Hewan:
    jenis = "makhluk hidup"          # atribut class (dipakai bersama)

    def __init__(self, nama):        # konstruktor
        self.nama = nama             # atribut instance

    def bersuara(self):
        return "..."

    def __str__(self):               # tampilan saat di-print
        return f"Hewan({self.nama})"


class Kucing(Hewan):                 # pewarisan (inheritance)
    def __init__(self, nama, warna):
        super().__init__(nama)       # panggil konstruktor induk
        self.warna = warna

    def bersuara(self):              # override method induk
        return "Meong"


k = Kucing("Mimi", "putih")
print(k)                             # Hewan(Mimi)
print(k.nama, k.bersuara())          # Mimi Meong
print(isinstance(k, Hewan))          # True
```

**Encapsulation dan property**

```python
class Rekening:
    def __init__(self, saldo):
        self._saldo = saldo          # awalan _ = "jangan diubah dari luar" (konvensi)

    @property
    def saldo(self):                 # dibaca seperti atribut: rek.saldo
        return self._saldo

    def setor(self, jumlah):
        if jumlah <= 0:
            raise ValueError("Jumlah harus positif")
        self._saldo += jumlah
```

## File Handling

Selalu pakai `with` agar file otomatis tertutup, dan set `encoding="utf-8"`.

```python
# tulis (menimpa isi lama)
with open("data.txt", "w", encoding="utf-8") as f:
    f.write("baris 1\n")
    f.write("baris 2\n")

# tambah di akhir
with open("data.txt", "a", encoding="utf-8") as f:
    f.write("baris 3\n")

# baca semua
with open("data.txt", "r", encoding="utf-8") as f:
    isi = f.read()

# baca baris per baris
with open("data.txt", "r", encoding="utf-8") as f:
    for baris in f:
        print(baris.strip())
```

| Mode | Fungsi |
|---|---|
| `"r"` | Baca (default), error jika file tidak ada |
| `"w"` | Tulis, **menimpa** isi lama atau membuat file baru |
| `"a"` | Tambah di akhir file |
| `"r+"` | Baca dan tulis |
| `"rb"`, `"wb"` | Mode biner (gambar, dll.) |

**CSV dan JSON**

```python
import csv, json

# CSV
with open("data.csv", newline="", encoding="utf-8") as f:
    for baris in csv.DictReader(f):
        print(baris["nama"])

# JSON
data = {"nama": "Farhan", "skill": ["Python", "AI"]}
with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)

with open("data.json", "r", encoding="utf-8") as f:
    data = json.load(f)
```

**Path dan cek file**

```python
from pathlib import Path

p = Path("data.txt")
p.exists()                          # True / False
p.read_text(encoding="utf-8")
p.write_text("halo", encoding="utf-8")
```

## Error Handling

```python
try:
    angka = int(input("Angka: "))
    print(10 / angka)
except ValueError:
    print("Harus berupa angka")
except ZeroDivisionError:
    print("Tidak bisa dibagi nol")
else:
    print("Tidak ada error")
finally:
    print("Selalu dijalankan")

# memicu error sendiri
raise ValueError("pesan error")
```

## Modul

```python
import math
from math import sqrt
import numpy as np                  # alias

math.pi
sqrt(16)                            # 4.0

# agar kode hanya jalan saat file dijalankan langsung
if __name__ == "__main__":
    print("dijalankan langsung")
```

Install library dari terminal:

```bash
pip install numpy matplotlib
```

## Tips

- Gunakan 4 spasi untuk indentasi, jangan campur dengan tab.
- Nama variabel dan fungsi memakai `huruf_kecil_dengan_underscore`, nama class memakai `HurufBesarDiAwal`.
- Pakai virtual environment untuk tiap proyek: `python -m venv .venv`.
