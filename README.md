# superai-ss6-mh3-fahmai-rag

# 🤖 MH3 — FahMai RAG Challenge

**Super AI Engineer Season 6 | Mini Hackathon 3**

ระบบ Retrieval-Augmented Generation (RAG) สำหรับตอบคำถามภาษาไทย
ด้วย BGE-M3 multilingual embeddings และ ensemble voting across prompt styles

---

## 📊 Result

| Metric | Value |
|--------|-------|
| Score | 0.85000 |
| Rank | 268 |

---

## 🔧 Tech Stack

`Python` · `sentence-transformers (BGE-M3)` · `LangChain` · `Typhoon API` · `Google Colab`

---

## 🏗️ Approach

### 1. Embedding — BGE-M3
ใช้ `BAAI/bge-m3` ผ่าน `sentence-transformers` (ไม่ใช่ FlagEmbedding)
เป็น improvement ที่ใหญ่ที่สุดตลอด pipeline เนื่องจาก BGE-M3 รองรับภาษาไทยได้ดี

### 2. Ensemble Voting Across 3 Prompt Styles

```
Prompt Style 1: Analytical    — วิเคราะห์เชิงเหตุผล
Prompt Style 2: Keyword-focus — เน้นคำสำคัญ
Prompt Style 3: Chain-of-Thought — คิดทีละขั้น
```

ใช้ majority vote ข้าม 3 styles แทนการใช้ style เดียว
→ ช่วยลด variance และ hallucination

### 3. NOT RELATED Heuristic
กรองคำถามที่ไม่เกี่ยวกับ context ออกก่อน
(การลบ heuristic นี้ทำให้ score ถดถอยทันที)

### 4. Reranker — ไม่ใช้
Cross-encoder reranker ที่ train บน English ทำให้ score แย่ลง
ในบริบท Thai document → ตัดออกจาก pipeline

---

## 💡 Key Learnings

- **BGE-M3** คือ single biggest improvement ใน RAG pipeline นี้
- **Ensemble ข้าม prompt styles** ดีกว่า ensemble ข้าม models
- **Heuristics ที่ดูเหมือนลบได้** มักจำเป็นกว่าที่คิด — ทดสอบก่อนลบเสมอ
- **Reranker อาจทำให้แย่ลง** ถ้า train domain ไม่ตรง

---

## 📁 Files

```
mh3-colab.py
```

---
