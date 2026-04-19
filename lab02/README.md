# 🧪 Vaja: Cloudflare Worker – API posrednik

## 📌 Opis vaje
V tej vaji boste ustvarili in objavili svoj prvi **Cloudflare Worker**, ki deluje kot preprost API.

Worker bo:
- vračal JSON podatke,
- uporabljal query parametre,
- klical zunanji API (quote storitev).

---

## 🎯 Cilji
Po zaključku vaje boste znali:
- ustvariti Cloudflare Worker,
- objaviti serverless funkcijo,
- obdelati HTTP zahteve (request),
- vračati odgovore (response),
- uporabljati query parametre,
- integrirati zunanji API.

---

## 🛠️ Orodja
- Cloudflare (brezplačen račun)
- spletni brskalnik

---

## 📝 Navodila

### 1️⃣ Ustvarjanje Workerja
1. Odprite Cloudflare Dashboard  
2. Izberite **Workers & Pages**  
3. Kliknite **Create application**  
4. Izberite **Worker**  
5. Izberite **Continue with Github**

Izberite svoj github repozitorij, kjer naj bo v datoteki index.js dosegljiva spodnja koda.

---

### 2️⃣ Dodajanje kode

Ustvarite datoteko index.js:

```js
export default {
  async fetch(request) {
    const url = new URL(request.url)

    if (url.pathname === "/") {
      return new Response(
        `
        <h1>Cloudflare Worker API</h1>
        <p>Uporabi naslednje poti:</p>
        <ul>
          <li>/api/time</li>
          <li>/api/hello?name=Ana</li>
          <li>/api/quote</li>
        </ul>
        `,
        { headers: { "content-type": "text/html" } }
      )
    }

    if (url.pathname === "/api/time") {
      return Response.json({
        time: new Date().toISOString()
      })
    }

    if (url.pathname === "/api/hello") {
      const name = url.searchParams.get("name") || "guest"
      return Response.json({
        message: `Hello ${name}`
      })
    }

  if (url.pathname === "/api/quote") {
    try {
      const res = await fetch("https://zenquotes.io/api/random")
      const data = await res.json()

      return Response.json({
        quote: data[0].q,
        author: data[0].a
      })
    } catch (e) {
      return Response.json(
        { error: "Quote API error" },
        { status: 500 }
      )
    }
  }

    return new Response("Not found", { status: 404 })
  }
}
```

Ustvarite še datoteko wrangler.jsonc

```js
{
  "$schema": "node_modules/wrangler/config-schema.json",
  "name": "cloudflare-worker-api",
  "main": "index.js",
  "compatibility_date": "2026-04-15"
}
```

Ti dve datoteki morajo biti dostopne in objavljene na vašem Github repozitoriju, ki ga boste povezali s Cloudflare.
---

### 3️⃣ Objava (Deploy)

1. Kliknite **Deploy**
2. Počakajte, da se Worker objavi
3. Odprite URL (npr.):
```
https://ime-workerja.uporabnik.workers.dev
```

---

### 4️⃣ Testiranje

#### Osnovna stran
```
/
```

#### Trenutni čas
```
/api/time
```

#### Pozdrav
```
/api/hello?name=Robi
```

#### Naključni quote
```
/api/quote
```

---

## 🧠 Naloga

### Obvezno
- uspešno deployajte Worker
- preizkusite vse API poti

### Dodatno (izberite vsaj eno)
- spremenite JSON odgovor
- dodajte novo pot `/api/student`
- spremenite pozdrav

---

## 📄 Oddaja
- URL Workerja
- screenshot začetne strani
- screenshot `/api/quote`
- kratek opis spremembe

---

## 🚀 Bonus
- dodajte novo pot npr. `/api/timezone` in uporabite kak javni API za pridobivanje podatkov.