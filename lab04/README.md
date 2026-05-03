# Vaja: Osnovni deploy statične ali JavaScript aplikacije na Vercel

## Namen vaje
Namen vaje je, da študent pripravi preprosto spletno aplikacijo, jo objavi v GitHub repozitorij, poveže z Vercelom in uspešno izvede produkcijski deploy.

Pri vaji študent spozna:
- osnovno strukturo enostavne spletne aplikacije,
- uporabo Git in GitHub,
- povezavo GitHub repozitorija z Vercelom,
- postopek avtomatskega deploya,
- preverjanje delovanja aplikacije v produkciji.

---

## Učni cilji
Po zaključeni vaji bo študent znal:
- pripraviti enostavno statično ali JavaScript aplikacijo,
- ustvariti GitHub repozitorij in vanj naložiti projekt,
- povezati repozitorij z Vercelom,
- izvesti deploy aplikacije,
- preveriti produkcijski URL in delovanje aplikacije.

---

## Zahteve
Študent potrebuje:
- nameščen **Git**,
- uporabniški račun na **GitHub**,
- uporabniški račun na **Vercel**,
- poljuben urejevalnik kode,
- nameščen **Node.js** samo v primeru, če izdela JavaScript projekt z razvojnim strežnikom ali build korakom.

---

## Opis naloge
Pripravite enostavno spletno aplikacijo. Aplikacija je lahko:
- čista statična HTML/CSS/JS stran, ali
- preprost JavaScript projekt.

Lahko uporabite kar HTML5UP predlogo.

Aplikacija naj vsebuje vsaj:
- naslov strani,
- kratek opis,
- en interaktiven element v JavaScriptu.

Primeri interaktivnega elementa:
- gumb, ki spremeni besedilo,
- števec klikov,
- prikaz trenutnega časa,
- preprost obrazec brez backenda.

Nato:
1. projekt naložite na GitHub,
2. GitHub repozitorij povežite z Vercelom,
3. izvedite deploy,
4. preverite, ali aplikacija deluje na produkcijskem URL-ju,
5. oddajte povezavo do GitHub repozitorija in povezavo do objavljene aplikacije.

---

## Predlagana struktura projekta
Za najbolj enostavno izvedbo lahko uporabite naslednjo strukturo:

```text
vercel-vaja/
├── index.html
├── style.css
└── script.js
```

---

## Primer enostavne aplikacije

### `index.html`
```html
<!DOCTYPE html>
<html lang="sl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vercel vaja</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>Moja prva aplikacija na Vercelu</h1>
    <p id="opis">To je enostavna vaja za deploy spletne aplikacije.</p>
    <button id="btn">Klikni me</button>
  </div>

  <script src="script.js"></script>
</body>
</html>
```

### `style.css`
```css
body {
  font-family: Arial, sans-serif;
  background: #f4f4f4;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 700px;
  margin: 80px auto;
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  text-align: center;
}

button {
  padding: 12px 20px;
  border: none;
  background: #111827;
  color: white;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  opacity: 0.9;
}
```

### `script.js`
```javascript
document.getElementById("btn").addEventListener("click", function () {
  document.getElementById("opis").textContent = "Gumb deluje in JavaScript se je uspešno izvedel.";
});
```

---

## Navodila za delo

### 1. Ustvarite mapo projekta
```bash
mkdir moja-vercel-vaja
cd moja-vercel-vaja
```

V mapo dodajte datoteke:
- `index.html`
- `style.css`
- `script.js`

Vanjo prilepite primer kode ali izdelajte svojo različico.

---

### 2. Inicializirajte Git repozitorij
```bash
git init
```

Dodajte datoteke in naredite prvi commit:
```bash
git add .
git commit -m "Initial commit"
```

---

### 3. Ustvarite GitHub repozitorij
Na GitHubu ustvarite nov repozitorij, na primer:

```text
moja-vercel-vaja
```

Nato povežite lokalni projekt z GitHub repozitorijem:
```bash
git remote add origin https://github.com/UPORABNISKO_IME/moja-vercel-vaja.git
git branch -M main
git push -u origin main
```

---

### 4. Povežite projekt z Vercelom
1. Odprite Vercel.
2. Prijavite se.
3. Izberite **Add New Project**.
4. Povežite svoj GitHub račun, če še ni povezan.
5. Izberite repozitorij `moja-vercel-vaja`.
6. Kliknite **Deploy**.

Pri enostavni statični aplikaciji običajno ni treba spreminjati dodatnih nastavitev.

---

### 5. Preverite produkcijski deploy
Po uspešnem deployu Vercel ustvari javni URL, na primer:

```text
https://moja-vercel-vaja.vercel.app
```

Preverite:
- ali se stran odpre,
- ali se prikaže naslov,
- ali gumb deluje,
- ali ni napak v prikazu.

---

## Kaj mora študent oddati
Študent odda:
1. povezavo do **GitHub repozitorija**,
2. povezavo do **Vercel produkcijskega URL-ja**,
3. kratek opis težav ali opažanj pri deployu.

---

## Merila za ocenjevanje

### Osnovni del
- projekt vsebuje zahtevane datoteke,
- aplikacija se pravilno odpre lokalno,
- projekt je objavljen na GitHubu,
- projekt je uspešno deployan na Vercel,
- produkcijski URL deluje.

### Dodatne točke
- lepši vizualni izgled,
- dodatna JavaScript funkcionalnost,
- urejen README v repozitoriju,
- smiselna struktura projekta.

---

## Možne težave

### 1. Aplikacija na Vercelu ne prikazuje sprememb
Možen vzrok:
- spremembe niso bile commitane ali pushane na GitHub.

Preveri:
```bash
git status
git add .
git commit -m "Update app"
git push
```

### 2. Napačna začetna datoteka
Možen vzrok:
- manjka `index.html`.

Rešitev:
- preverite, da je v korenski mapi projekta datoteka `index.html`.

### 3. CSS ali JavaScript se ne naložita
Možen vzrok:
- napačna pot do datoteke.

Preverite povezave:
```html
<link rel="stylesheet" href="style.css">
<script src="script.js"></script>
```

---

## Razmislek po vaji
Po zaključeni vaji naj študent razmisli:
- Kaj je razlika med lokalnim odpiranjem datoteke in produkcijskim deployom?
- Kaj se zgodi, ko spremeni datoteko in naredi nov push na GitHub?
- Zakaj je povezava med GitHubom in Vercelom uporabna?
- Katere vrste projektov bi še lahko objavili na ta način?
