# 🤖 AI Agent Factory — MCQ Quiz Website

## 📝 Website Kya Hai?

Yeh ek **MCQ Quiz website** hai jisme **3 Parts** hain:

| Part | Questions | Time |
|------|-----------|------|
| **Part 1** 📘 | 31 MCQs | 15 Minutes |
| **Part 2** 📕 | 100 MCQs | 45 Minutes |
| **Part 3** 📗 🔴 Hard | 50 MCQs | 25 Minutes |

Students browser mein kholenge → **Home Screen** par teeno parts dikhenge → jis part ka karna hai us par click karein → MCQ solve karein → result final mein aata hai.

---

## 🚀 Deploy Kaise Karein?

### Netlify (Sabse Easy):
1. [app.netlify.com/drop](https://app.netlify.com/drop) par jao
2. `index.html` file ko drag & drop karo
3. Milne wala link students ko share karo

### Vercel:
1. [vercel.com](https://vercel.com) par jao
2. Drag & drop `index.html`
3. File ka naam **`index.html`** hona chahiye

> ⚠️ **File name IMPORTANT hai:** File ka naam **`index.html`** rakhna zaroori hai. Agar koi aur naam rakha to 404 error aayega.

---

## 🧠 Website Kaise Kaam Karti Hai?

```
👥 ONLINE COUNTER (top par har screen pe)
   ├── Real-time: kitne log online hain
   └── Firebase Realtime Database se update

🏠 HOME SCREEN
   ├── 📘 Part 1 (31 Qs — 15 min)
   ├── 📕 Part 2 (100 Qs — 45 min)
   └── 📗 Part 3 (50 Qs — 25 min) 🔴 Hard
           │
           ▼
   📝 QUIZ SCREEN
   ├── 1 option click → turant result
   │   ✅ Correct = green
   │   ❌ Wrong = red + correct answer green
   ├── Next button (No Previous)
   └── Timer countdown
           │
           ▼
   🏁 RESULTS SCREEN
   ├── Score %, Correct/Wrong/Skipped
   ├── 🔄 Retry same part
   └── 🏠 Back to Home (doosra part select karne ke liye)
```

---

## 🔧 Website Mein Change Kaise Karein?

### 🟢 Questions / Options Badalna (Part 1)

`index.html` file ko **Notepad ya VS Code** mein kholo. **Ctrl+F** karo aur yeh dhundho:

```
const Q1 = [
```

Yahan Part 1 ke 31 questions hain. Har question kuch yun dikhta hai:

```javascript
{ id:1, txt:"A developer built an AI agent...",
  opts:["Option A","Option B","Option C","Option D"], ans:2 },
```

### 🟢 Questions / Options Badalna (Part 2)

Ctrl+F karo:

```
const Q2 = [
```

Yahan Part 2 ke 100 questions hain.

### 🟢 Questions / Options Badalna (Part 3)

Ctrl+F karo:

```
const Q3 = [
```

Yahan Part 3 ke 50 questions hain.

**Samjhao:**
- `id` → question number
- `txt` → question text
- `opts` → 4 options (["A","B","C","D"])
- `ans` → correct answer index (**0 = A, 1 = B, 2 = C, 3 = D**)

😊 **Example:** Correct answer "Option C" rakhna hai to `ans:2` karo (0-based hai).

---

### 🟢 Timer ka time badalna

Ctrl+F karo `timeLeft =`

| Code | Kya hai |
|------|---------|
| `timeLeft = 900` | ⏱ Part 1 — 15 minutes (900 sec) |
| `timeLeft = 2700` | ⏱ Part 2 — 45 minutes (2700 sec) |
| `timeLeft = 1500` | ⏱ Part 3 — 25 minutes (1500 sec) |

Seconds mein value change karo:
- 10 min → `600`
- 20 min → `1200`
- 30 min → `1800`
- 45 min → `2700`
- 60 min → `3600`

---

### 🟢 Colors / Theme change karna

Background color badalni hai? Ctrl+F karo `background: linear-gradient`

```
background: linear-gradient(135deg, #e8eaff 0%, #f5f3ff 100%);
```

Yeh primary background hai. Ise apni pasand ke color se replace karo.
- Purple theme → `#e8eaff` aur `#f5f3ff` ki jagah `#f3e8ff` aur `#fff5f5`
- Green theme → `#ecfdf5` aur `#f0fdf4`

Primary purple color (`#6c63ff`) ko bhi change kar sakte ho — poori file mein iska replace kardo.

---

### 🟢 Part 3 Add Karna (Aur MCQs ho to)

✅ **Part 3 already added hai** — 50 MCQs with 25 minutes.

Aur zyada MCQs add karne hain to `const Q3 = [...]` array mein naye objects add karo.

---

### 🟢 Title change karna hai?

Ctrl+F karo `AI Agent Factory` aur replace karo naye naam se.

### 🟢 "Correct Answer!" / "Wrong Answer!" text change karna hai?

Ctrl+F karo `Correct Answer!` aur `Wrong Answer!` — dono jagah replace ho jayenge.

---

### 🔴 Advanced Changes

**👥 Online Counter (Firebase):** Website ke top par har screen pe **"X online — preparing"** dikhta hai — real-time!

✅ **Already setup hai** — Firebase config keys daal di gayi hain. Kaam karta rahega.

Agar apna khud ka Firebase project banana ho to:
1. [console.firebase.google.com](https://console.firebase.google.com) par jao
2. **Create a project** → naam do (Google Analytics off kar do)
3. **Realtime Database** → **Create Database** → **Start in test mode**
4. **Project Settings** (⚙️) → **General** → **Your apps** → **Web app** (`</>` icon)
5. Config copy karo aur `index.html` mein `FIREBASE_CONFIG` object mein paste karo
6. Deploy karo — ab online counter kaam karega!

**Explanation add karni hai?** Feedback currently bas "Correct/Wrong Answer" show karta hai. Agar explanation bhi dikhana hai to:
1. `const EXP = {...}` wala object banao
2. `handleAnswer` function mein `EXP[q.id]` use karo
3. `fb.innerHTML` mein explanation bhi append karo

**Previous button wapas chahiye?** Front-end mein button add karo aur JS mein click handler lagao.

---

## 📁 Files

| File | Kya Hai |
|------|---------|
| `index.html` | ✅ **Main file** — Part 1 + 2 + 3 + Online Counter, sab isi mein hai (yhi deploy hoti hai) |
| `AI_Agent_Factory_MCQs_Explained.md` | 📘 Explanations notes (source) |
| `100 MCQS.md` | 📕 Part 2 ke questions (source) |
| `richtext_converted_to_markdown.md` | 📗 Part 3 ke questions (source) |
| `README.md` | 📖 Yeh file |

---

## 🔀 Answer Distribution (Important!)

Part 2 aur Part 3 ke questions mein **answers properly shuffle kiye gaye hain** taake students pattern se correct answer na guess kar saken.

### Part 2
| Letter | Count |
|--------|-------|
| **A** | 25 |
| **B** | 25 |
| **C** | 25 |
| **D** | 25 |

Har option ka **exact 25** correct answers hain — bilkul balanced! ✅

### Part 3
| Letter | Count |
|--------|-------|
| **A** | 13 |
| **B** | 12 |
| **C** | 13 |
| **D** | 12 |

Options ki length bhi equal rakhi gayi hai taake length dekh kar answer guess na kar saken. ✅

---

## ⚡ Quick Tips

- Code **bilkul mat todo** — sirf upar bataye gaye parts change karo
- Koi change karne se pehle **original file ka backup** rakh lo
- Change karne ke baad browser mein **Ctrl+F5** karo (hard refresh)
- Koi problem ho to mujhse pooch lo! 😊
