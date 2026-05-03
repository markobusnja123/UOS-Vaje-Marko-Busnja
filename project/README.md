# Projektna vaja: Deploy enostavnega projekta na Vercel z dodatno konfiguracijo

## 1. Namen vaje

Namen projektne vaje je, da študent pripravi svoj lasten primer spletnega projekta in ga objavi na platformi **Vercel**.

Poudarek vaje ni na zahtevnem programiranju, ampak na razumevanju osnovnega procesa objave spletne aplikacije, dela z GitHubom, konfiguracije okolja, DNS nastavitev in uporabe dodatnih storitev, kot sta **Supabase** ali **Cloudflare**.

Projekt je lahko zelo enostaven. Pomembno je, da je pravilno pripravljen, objavljen in dokumentiran.

---

## 2. Kaj je CI/CD?

**CI/CD** pomeni avtomatiziran proces priprave, preverjanja in objave aplikacije.

### CI - Continuous Integration

CI pomeni, da se spremembe kode redno shranjujejo v skupni repozitorij, na primer GitHub. Ob vsaki spremembi se lahko samodejno preveri, ali se projekt pravilno zgradi.

Primer:

```text
sprememba kode → git commit → git push → preverjanje projekta
```

### CD - Continuous Deployment

CD pomeni, da se aplikacija po spremembi samodejno objavi na strežnik oziroma platformo, kot je Vercel.

Primer:

```text
git push → Vercel zazna spremembo → samodejni deploy → nova verzija aplikacije je dostopna prek URL-ja
```

V tej vaji bo Vercel uporabljen kot platforma za samodejni deploy.

---

## 3. Cilji projekta

Po končanem projektu zna študent:

- pripraviti enostaven spletni projekt,
- uporabiti Git in GitHub,
- povezati GitHub repozitorij z Vercelom,
- izvesti samodejni deploy,
- razumeti razliko med Preview in Production deployem,
- dodati osnovno konfiguracijo projekta,
- po želji vključiti Supabase ali Cloudflare,
- dokumentirati postopek in oddati dokazila.

---

## 4. Predpogoji

Za izvedbo vaje potrebujete:

- GitHub račun,
- Vercel račun,
- nameščen Git,
- osnovno znanje HTML/CSS/JavaScript,
- po želji Cloudflare ali Supabase račun.

Preverite, ali je Git nameščen:

```bash
git --version
```

---

## 5. Ideja projekta

Vsak študent pripravi lasten primer projekta.

Projekt je lahko zelo enostaven, na primer:

- osebna predstavitvena stran,
- stran za izmišljeno podjetje,
- stran za lokalni dogodek,
- mini dokumentacija za IT storitev,
- statusna stran za strežnik,
- landing page za aplikacijo,
- stran z navodili za uporabnike,
- enostaven katalog povezav,
- mini portal z obrazcem za kontakt,
- statična stran za interni IT oddelek.

Primer minimalne strukture projekta:

```text
moj-vercel-projekt/
├── index.html
├── style.css
├── script.js
└── README.md
```

Programiranje je lahko minimalno. Pomembnejša je pravilna konfiguracija in objava. Lahko se uproabi tudi že obstoječ projekt iz spleta, vir navedite v nogi spletne strani in v oddaji projekta. 

---

## 6. Obvezne zahteve projekta

Projekt mora vsebovati:

1. lasten GitHub repozitorij,
2. vsaj eno HTML stran,
3. osnovno oblikovanje s CSS,
4. vsaj eno spremembo narejeno prek Git workflowa,
5. deploy na Vercel,
6. dokumentiran postopek v `README.md`,
7. povezavo do produkcijske verzije aplikacije,
8. razlago uporabljene konfiguracije.

---

## 7. Priprava projekta

Ustvarite novo mapo:

```bash
mkdir moj-vercel-projekt
cd moj-vercel-projekt
```

Ustvarite osnovne datoteke:

```bash
touch index.html style.css script.js README.md
```

Primer datoteke `index.html`:

```html
<!DOCTYPE html>
<html lang="sl">
<head>
  <meta charset="UTF-8">
  <title>Moj Vercel projekt</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <h1>Moj Vercel projekt</h1>
    <p>To je enostaven projekt, objavljen na Vercelu.</p>
    <button onclick="showMessage()">Preveri delovanje</button>
    <p id="message"></p>
  </main>

  <script src="script.js"></script>
</body>
</html>
```

Primer datoteke `style.css`:

```css
body {
  font-family: Arial, sans-serif;
  background: #f4f4f4;
  margin: 0;
  padding: 40px;
}

main {
  max-width: 700px;
  margin: auto;
  background: white;
  padding: 30px;
  border-radius: 12px;
}

button {
  padding: 10px 16px;
  cursor: pointer;
}
```

Primer datoteke `script.js`:

```javascript
function showMessage() {
  document.getElementById("message").innerText = "Aplikacija deluje.";
}
```

---

## 8. Inicializacija Git repozitorija

Inicializirajte Git:

```bash
git init
```

Dodajte datoteke:

```bash
git add .
```

Naredite prvi commit:

```bash
git commit -m "Initial project setup"
```

---

## 9. Povezava z GitHubom

Na GitHubu ustvarite nov repozitorij.

Nato lokalni projekt povežite z GitHub repozitorijem:

```bash
git remote add origin https://github.com/UPORABNISKO_IME/IME_REPOZITORIJA.git
```

Preimenujte glavno vejo v `main`:

```bash
git branch -M main
```

Pošljite projekt na GitHub:

```bash
git push -u origin main
```

---

## 10. Deploy na Vercel

Na Vercelu:

1. izberite **Add New Project**,
2. povežite GitHub račun,
3. izberite svoj repozitorij,
4. preverite nastavitve projekta,
5. kliknite **Deploy**.

Po uspešnem deployu dobite produkcijski URL, na primer:

```text
https://moj-vercel-projekt.vercel.app
```

Ta URL vključite v oddajo.

---

## 11. CI/CD workflow

Ko je GitHub repozitorij povezan z Vercelom, se deploy izvaja samodejno.

Če spremenite kodo in jo pošljete na GitHub:

```bash
git add .
git commit -m "Update homepage content"
git push
```

Vercel samodejno zazna spremembo in izvede nov deploy.

---

## 12. Preview in Production deploy

### Production deploy

Production deploy je javna verzija aplikacije. Običajno nastane iz veje `main`.

Primer:

```bash
git push origin main
```

Rezultat je nova produkcijska verzija aplikacije.

### Preview deploy

Preview deploy je testna verzija aplikacije. Nastane, ko delate na drugi veji ali Pull Requestu.

Primer:

```bash
git checkout -b update-content
```

```bash
git add .
git commit -m "Update page content"
git push -u origin update-content
```

Vercel za to vejo pripravi ločen Preview URL.

---

## 13. Priporočen Git workflow

Za vajo uporabite naslednji postopek:

```text
main branch → nova veja → sprememba → push → preview deploy → merge → production deploy
```

Ukazi:

```bash
git checkout -b update-content
```

```bash
git add .
git commit -m "Update content"
git push -u origin update-content
```

Nato lahko na GitHubu ustvarite Pull Request in ga združite v `main`.

Pull Request ni nujen za deploy, je pa priporočljiv, ker omogoča bolj realen razvojni proces.

---

## 14. Dodatna konfiguracija na Vercelu

V projektu morate prikazati vsaj eno dodatno konfiguracijo.

Izberite vsaj eno izmed spodnjih možnosti.

---

### Možnost A: Environment variables

Dodajte okoljsko spremenljivko v Vercelu.

Primer:

```text
SITE_NAME=Moj Vercel projekt
```

V Vercelu jo nastavite pod:

```text
Project Settings → Environment Variables
```

Če uporabljate navaden statični HTML, lahko v README razložite, da environment variables niso neposredno vidne v brskalniku, razen če uporabljate framework ali build proces.

Primer razlage:

```text
Environment variables se uporabljajo za konfiguracijo aplikacije brez zapisovanja občutljivih podatkov neposredno v kodo.
```

---

### Možnost B: Custom domain z DNS

Če imate lastno domeno, lahko projekt povežete z lastno domeno.

Primer:

```text
projekt.mojadomena.si
```

V Vercelu dodate domeno pod:

```text
Project Settings → Domains
```

Nato pri DNS ponudniku nastavite zapis, ki ga zahteva Vercel.

Primer DNS zapisa:

```text
Type: CNAME
Name: projekt
Value: cname.vercel-dns.com
```

Če nimate svoje domene, lahko ta del opišete teoretično in priložite screenshot nastavitev v Vercelu.

---

### Možnost C: Cloudflare DNS

Če uporabljate Cloudflare, lahko domeno upravljate prek Cloudflare DNS.

Primer postopka:

1. domeno dodate v Cloudflare,
2. preverite nameserverje,
3. dodate DNS zapis za Vercel,
4. preverite, ali domena kaže na Vercel projekt.

Primer DNS zapisa:

```text
Type: CNAME
Name: app
Target: cname.vercel-dns.com
Proxy status: DNS only
```

Za začetno konfiguracijo je priporočljivo uporabiti **DNS only**, da lažje preverite delovanje povezave med domeno in Vercelom.

---

### Možnost D: Supabase kot zunanja storitev

Namesto Cloudflare lahko uporabite Supabase kot zunanjo storitev.

Možni primeri:

- obrazec za kontakt,
- seznam sporočil,
- enostaven seznam nalog,
- mini statusna tabela,
- zbiranje prijav na dogodek.

Minimalna tabela v Supabase:

```sql
create table messages (
  id bigint generated by default as identity primary key,
  name text,
  message text,
  created_at timestamp with time zone default now()
);
```

Pri Supabase morate paziti na varnostne nastavitve, predvsem na **Row Level Security (RLS)**.

Za osnovni test lahko pripravite politiko za branje:

```sql
alter table messages enable row level security;
```

```sql
create policy "Allow public read"
on messages
for select
using (true);
```

Za produkcijske projekte javni zapis v bazo brez omejitev ni priporočljiv. Če omogočite javni vnos, morate znati razložiti varnostna tveganja.

---

### Možnost E: Cloudflare Web Analytics

Projekt lahko nadgradite z osnovno analitiko prek Cloudflare Web Analytics, v kolikor imate povezano domeno. Opcijsko lahko povežete tudi z Google Analytics namesto Cloudflare Web Analytics. 

Dodate lahko:

- spremljanje obiskov,
- osnovne metrike,
- pregled prometa brez piškotkov.

V README opišite:

```text
Cloudflare Web Analytics omogoča osnovno spremljanje obiska spletne strani brez zahtevne konfiguracije.
```

---

## 15. Priporočena izbira

Ker je poudarek na konfiguraciji, je priporočena kombinacija:

```text
Vercel deploy + GitHub CI/CD + Cloudflare DNS + environment variables
```

Druga dobra možnost:

```text
Vercel deploy + GitHub CI/CD + Supabase tabela + RLS razlaga
```

Ni potrebno, da uporabite vse možnosti. Dovolj je, da izberete eno ali dve dodatni konfiguraciji in ju dobro dokumentirate.

---

## 16. Dokumentacija projekta

V svojem `README.md` opišite:

```markdown
# Ime projekta

## Opis
Kratek opis projekta.

## Uporabljene tehnologije
- HTML
- CSS
- JavaScript
- GitHub
- Vercel
- Cloudflare ali Supabase

## Deploy
Production URL:
https://...

## CI/CD
Opis, kako se izvede samodejni deploy.

## Dodatna konfiguracija
Opis DNS, environment variables, Supabase ali Cloudflare nastavitev.

## Težave
Opišite težave, na katere ste naleteli, in kako ste jih rešili.
```

---

## 17. Oddaja projekta

Oddati morate:

1. povezavo do GitHub repozitorija,
2. povezavo do Vercel produkcijske aplikacije,
3. screenshot uspešnega deploya v Vercelu,
4. screenshot GitHub commitov ali Pull Requesta,
5. opis dodatne konfiguracije,
6. kratek odgovor na vprašanja za razmislek.

---

## 18. Vprašanja za razmislek

Odgovorite na naslednja vprašanja:

1. Kaj pomeni CI/CD?
2. Kaj se zgodi, ko naredite `git push`?
3. Kakšna je razlika med Preview in Production deployem?
4. Zakaj je koristno uporabljati GitHub skupaj z Vercelom?
5. Kaj so environment variables?
6. Zakaj DNS konfiguracija spada med pomembne sistemske naloge?
7. Kakšna so varnostna tveganja, če je Supabase tabela javno zapisljiva?
8. Kaj bi bilo treba dodati, če bi projekt postal produkcijska aplikacija?

---

## 19. Ocenjevalni kriteriji

| Kriterij | Točke |
|---|---:|
| GitHub repozitorij je pravilno pripravljen | 10 |
| Projekt je uspešno objavljen na Vercelu | 20 |
| CI/CD workflow je prikazan in dokumentiran | 20 |
| Dodatna konfiguracija je izvedena ali dobro razložena | 20 |
| README dokumentacija je urejena | 20 |
| Odgovori na vprašanja za razmislek | 10 |
| **Skupaj** | **100** |

---

## 20. Minimalni pričakovani rezultat

Minimalno uspešna oddaja vsebuje:

```text
GitHub repozitorij + Vercel URL + README + screenshot deploya
```

Boljša oddaja vsebuje še:

```text
Preview deploy + custom domain ali Cloudflare DNS + razlaga konfiguracije
```

Odlična oddaja vsebuje:

```text
Vercel + GitHub workflow + Cloudflare DNS + Supabase ali environment variables + dobra dokumentacija
```

---

## 21. Povzetek

V tej projektni vaji pripravite lasten enostaven projekt, ga objavite na Vercelu in dokumentirate konfiguracijo.

Glavni poudarek je na:

- GitHub workflowu,
- samodejnem deployu,
- Vercel konfiguraciji,
- DNS oziroma dodatnih storitvah,
- razumevanju osnovnega CI/CD procesa.

Programiranje je lahko minimalno. Pomembno je, da znate projekt pripraviti, povezati, objaviti in razložiti konfiguracijo.
