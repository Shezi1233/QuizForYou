# 🤖 AI Agent Factory — MCQ Quiz Website

## 📝 Ye Website Kya Hai?

Yeh ek **MCQ Quiz website** hai jo **AI Agent Factory** course ke 31 questions par based hai. Students browser mein kholein aur MCQ solve karein — result final mein aata hai.

## 🚀 Deploy Kaise Karein?

### Netlify (Sabse Easy):
1. [app.netlify.com/drop](https://app.netlify.com/drop) par jao
2. `index.html` file ko drag & drop karo
3. Milne wala link students ko share karo

### Vercel:
1. [vercel.com](https://vercel.com) par jao
2. Drag & drop `index.html`
3. File ka naam **`index.html`** hona chahiye

> ⚠️ **File name IMPORTANT hai:** Agar Vercel / Netlify par deploy karna hai to file ka naam **`index.html`** rakhna zaroori hai. `mcq-quiz.html` rakhoge to 404 error aayega.

---

## 🔧 Website Mein Change Kaise Karein?

### 🟢 Simple Changes (Options, Questions, Timer, Colors)

#### Questions / Options badalna
`index.html` file ko **Notepad ya VS Code** mein kholo. **Ctrl+F** karo aur yeh dhundho:

```
const Q = [
```

Yahan se saare questions hain. Har question kuch yun dikhta hai:

```javascript
{ id:1, mod:"Module 1 — Foundations", top:"Human Oversight",
  txt:"A developer built an AI agent to review legal contracts...",
  opts:["Option A","Option B","Option C","Option D"], ans:2 },
```

**Samjhao:**
- `id` → question number
- `mod` → module name
- `top` → topic name
- `txt` → question text
- `opts` → 4 options (["A","B","C","D"])
- `ans` → correct answer index (**0 = A, 1 = B, 2 = C, 3 = D**)

😊 **Example:** Correct answer "Option C" rakhna hai to `ans:2` karo (0-based hai).

---

#### Timer ka time badalna (15 minute)
Ctrl+F karo `timeLeft = 900`

`900` seconds hai (15 × 60 = 900). Change karo jo time chahiye:
- 10 min → `600`
- 20 min → `1200`
- 30 min → `1800`

---

#### Colors / Theme change karna
Background color badalni hai? Ctrl+F karo `background: linear-gradient`

```
background: linear-gradient(135deg, #e8eaff 0%, #f5f3ff 100%);
```

Yeh primary background hai. Isko apni pasand ke color se replace karo.
- Purple theme → `#e8eaff` aur `#f5f3ff` ki jagah `#f3e8ff` aur `#fff5f5`
- Green theme → `#ecfdf5` aur `#f0fdf4`

Primary purple color (`#6c63ff`) ko bhi change kar sakte ho — poori file mein iska replace kardo.

---

### 🟡 Moderate Changes

#### Questions ki total count change karni hai?
1. Naye question add karo `const Q = [...]` array mein
2. Ctrl+F karo `const TOTAL = Q.length;` — yeh automatically count lega
3. Koi number change karne ki zaroorat nahi

#### Title change karna hai?
Ctrl+F karo `AI Agent Factory` aur replace karo naye naam se.

#### "Correct Answer!" / "Wrong Answer!" text change karna hai?
Ctrl+F karo: `Correct Answer!` aur `Wrong Answer!` — dono jagah replace ho jayenge.

---

### 🔴 Advanced Changes (JS wale)

**Explanation add karni hai?** Currently feedback bas "Correct/Wrong Answer" show karta hai. Agar explanation bhi dikhana hai to:

1. `const EXP = {...}` wala object add karo (jaisa pehle the)
2. `handleAnswer` function mein `EXP[q.id]` use karo
3. `fb.innerHTML` mein explanation bhi append karo

**Previous button wapas chahiye?** `nav` div mein ek Previous button add karo aur usme click handler lagao.

---

## 📁 Files

| File | Kya Hai |
|------|---------|
| `index.html` | ✅ Main website file (yhi deploy hoti hai) |
| `AI_Agent_Factory_MCQs_Explained.md` | 📘 Explanations notes |
| `README.md` | 📖 Yeh file |

---

## ⚡ Quick Tips

- Code **bilkul mat todo** — sirf upar bataye gaye parts change karo
- Koi change karne se pehle **original file ka backup** rakh lo
- Change karne ke baad browser mein **Ctrl+F5** karo (hard refresh)
- Koi problem ho to mujhse pooch lo! 😊
