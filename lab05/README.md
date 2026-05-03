# Vaja: CI/CD z GitHub in Vercel

## 🎯 Cilj
Spoznati delovanje CI/CD (Continuous Integration in Continuous Deployment) z uporabo GitHuba in Vercela.

---

## 🧠 Kaj je CI/CD?

**CI (Continuous Integration)** pomeni, da razvijalci pogosto združujejo (merge) svojo kodo v skupni repozitorij. Ob vsaki spremembi se lahko avtomatsko izvajajo testi ali build.

**CD (Continuous Deployment)** pomeni, da se aplikacija po spremembah samodejno namesti (deploya) v okolje (npr. produkcija ali preview).

👉 V tej vaji:
- GitHub = CI (upravljanje kode in sprememb)
- Vercel = CD (samodejni deploy)

---

## 🧠 Kaj se naučite
- Git workflow z vejami (branching)
- Pull Requesti
- Samodejni deploy na Vercelu
- Preview vs Production

---

## ⚙️ Predpogoji
- GitHub račun
- Vercel račun
- Obstoječa aplikacija na Vercelu (lahko uporabite iz lab04)

---

## 🚀 Naloge

### 1. Ustvari novo vejo

```bash
git checkout -b update-title
```

---

### 2. Spremeni aplikacijo

Spremeni naslov aplikacije:

```text
Vercel vaja
```

v:

```text
Vercel vaja - CI/CD
```

---

### 3. Commit in push

```bash
git add .
git commit -m "Update app title for CI/CD demo"
git push -u origin update-title
```

---

### 4. Ustvari Pull Request

Na GitHubu:
- odpri repozitorij
- klikni **Compare & pull request**
- ustvari PR v vejo `main`

---

### 5. Preveri Preview (Vercel)

- odpri Vercel dashboard
- najdi **Preview Deployment**
- odpri URL

✅ preveri, ali se sprememba vidi

---

### 6. Merge

Na GitHubu:

```text
Merge Pull Request
```

---

### 7. Production deploy

- Vercel samodejno naredi deploy
- odpri produkcijski URL
- preveri spremembo

---

## 📸 Oddaja

Oddaj:

1. Screenshot Pull Requesta  
2. Preview URL  
3. Production URL  
4. Kratek odgovor:

```text
Kakšna je razlika med Preview in Production deployem?
```

---

## 💡 Razlika

- **Preview Deployment** → testna verzija (za pregled sprememb)  
- **Production Deployment** → javna verzija aplikacije  

---

## 🔥 Bonus (opcijsko)

- naredi še eno vejo
- odpri več PR-jev
- opazuj več preview deployev
- revert spremembo

---

## ✅ Povzetek

CI/CD omogoča:

- hitrejši razvoj  
- manj napak  
- avtomatske deploye  

To je standard v modernem razvoju aplikacij.
