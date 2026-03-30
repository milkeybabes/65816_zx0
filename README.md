# 65816 ZX0 Decompressor (SNES / Super Famicom)

A high-performance **ZX0 decompressor written in 65816 assembly**, designed primarily for the **SNES / Super Famicom**, but easily adaptable to other 65816-based systems.

This implementation focuses on:
- Clean structure
- Practical integration
- Efficient execution
- Readability for developers

---

## 🚀 Features

- ⚡ Optimized for 65816 (16-bit where it matters)
- 🧠 Designed with SNES banking in mind
- 🔧 Written for **64tass** (easily portable to other assemblers)
- 📦 Supports standard ZX0 compressed data
- 🧩 Clean macro usage for portability
- 📉 Competitive cycle performance

---

## 📊 Performance

Typical decompression performance (real-world test):

- ~529,000 cycles for full data block
- Well within acceptable limits for frame-based or staged loading

Performance will vary depending on:
- Data entropy
- Literal vs copy balance
- Memory layout

---

## 🛠 Requirements

- 65816 CPU
- Assembler: **64tass**
- Basic macro support (can be adapted for other assemblers)

---
## 📁 Project Calling



---

## ⚙️ Integration

### 1. Include the source; you can remove/modify the macros to suit your system. Left here to keep the source readable
##  2. We decompress to RAM UNPACK_BUFFER; the source data, normally in ROM, can also be in RAM if desired. Source data doesn't traverse banks.
```asm

.include "65815_zc0_unpacker.asm"


; unpacker for ZX0 as this will be new compressions

  LongAI	; Be Sure pass I in 16bits, A can be 8bits
	LDX	#<>lz_test	; small test data word offset
	LDA	#`lz_test	; A is the bank number $80 - $xx 
	JSR	ZX0_DECOMPRESS_V2

```
## 📚 ZX0 References

Original ZX0 project and documentation:

https://github.com/einar-saukas/ZX0

Additional notes:
- Different ZX0 encoders may produce slightly different bitstreams
- All compliant streams should decompress correctly with this implementation

---

## 📜 License

This project is licensed under the MIT License.

## 🙏 Attribution

If you use this code in your project, a credit or mention is greatly appreciated.

## ⭐ Final Thoughts

This project aims to provide a **practical, high-quality 65816 decompressor**
that fits naturally into real development pipelines.




