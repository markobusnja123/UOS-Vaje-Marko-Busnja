# 🧪 Vaja: Supabase – Osnovna aplikacija

## 📌 Opis vaje
V tej vaji boste ustvarili preprosto spletno aplikacijo, ki uporablja **Supabase** kot backend.

Aplikacija bo omogočala:
- prikaz zapisov iz baze,
- dodajanje novih zapisov.

---

## 🎯 Cilji
Po zaključku boste znali:
- ustvariti Supabase projekt,
- ustvariti tabelo,
- uporabljati Supabase API iz JavaScript,
- rešiti osnovne težave (RLS, API ključi).

---

## 🛠️ Orodja
- Supabase (free account)
- spletni brskalnik
- HTML + JavaScript

---

# 1️⃣ Ustvari Supabase projekt

1. Pojdi na https://supabase.com  
2. Ustvari račun  
3. Klikni **New Project**  
4. Nastavi:
   - ime projekta
   - geslo
5. Počakaj ~1–2 minuti

---

# 2️⃣ Ustvari tabelo

V SQL Editorju zaženi:

```sql
create table public.notes (
  id bigint generated always as identity primary key,
  text text not null
);
```

---

# 3️⃣ Nastavi RLS (OBVEZNO!)

```sql
alter table public.notes enable row level security;

create policy "Public read notes"
on public.notes
for select
to anon
using (true);

create policy "Public insert notes"
on public.notes
for insert
to anon
with check (true);
```

---

# 4️⃣ Pridobi API podatke

Project Settings → API keys:
- anon / publishable key ustvari in kopiraj

Iz dashboard projekta pa kopiraj Project URL.

---

# 5️⃣ Aplikacija

```html
<!DOCTYPE html>
<html>
<head>
  <title>Supabase App</title>
</head>
<body>

<h1>Moje beležke</h1>

<input id="noteInput" placeholder="Vnesi tekst">
<button onclick="addNote()">Dodaj</button>

<ul id="list"></ul>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<script>
const supabaseClient = window.supabase.createClient(
  "YOUR_URL",
  "YOUR_KEY"
)

async function loadNotes() {
  const { data } = await supabaseClient.from('notes').select('*')

  const list = document.getElementById('list')
  list.innerHTML = ""

  if (data) {
    data.forEach(n => {
      const li = document.createElement("li")
      li.innerText = n.text
      list.appendChild(li)
    })
  }
}

async function addNote() {
  const input = document.getElementById('noteInput')
  const text = input.value.trim()

  if (!text) return

  await supabaseClient.from('notes').insert([{ text }])

  input.value = ""
  loadNotes()
}

loadNotes()
</script>

</body>
</html>
```

---

# 📄 Oddaja
- screenshot aplikacije
- screenshot baze
- kratek opis

---

