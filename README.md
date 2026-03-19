# 🧾 Ricevute — Receipt Tracker PWA

App progressiva per tracciare le ricevute con analisi AI (Claude Sonnet).
Scatta una foto → l'AI estrae i dati → salva e monitora le spese.

---

## 📁 Struttura del progetto

```
ricevute-pwa/
├── index.html          ← App completa (HTML + React + CSS)
├── sw.js               ← Service Worker (cache offline)
├── manifest.json       ← Manifest PWA (icona, nome, tema)
├── netlify.toml        ← Configurazione Netlify
├── .gitignore
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── icon-maskable-512.png
│   └── apple-touch-icon.png
└── README.md
```

---

## 🚀 Setup iniziale (una volta sola)

### 1. Crea il repository su GitHub

1. Vai su [github.com/new](https://github.com/new)
2. Nome: `ricevute-pwa`
3. Lascia **Public** o metti **Private** (Netlify funziona con entrambi)
4. **Non** aggiungere README o .gitignore (li abbiamo già)
5. Clicca **Create repository**

### 2. Carica i file sul repository

**Opzione A — Da browser (più semplice):**
1. Nella pagina del repo vuoto, clicca **"uploading an existing file"**
2. Trascina TUTTI i file e cartelle del progetto
3. Clicca **Commit changes**

**Opzione B — Da terminale:**
```bash
cd ricevute-pwa
git init
git add .
git commit -m "Prima versione"
git branch -M main
git remote add origin https://github.com/TUO-USERNAME/ricevute-pwa.git
git push -u origin main
```

### 3. Collega Netlify al repository

1. Vai su [app.netlify.com](https://app.netlify.com) e accedi (o crea account gratis)
2. Clicca **"Add new site"** → **"Import an existing project"**
3. Scegli **GitHub** e autorizza l'accesso
4. Seleziona il repo `ricevute-pwa`
5. Nelle impostazioni di build:
   - **Branch to deploy:** `main`
   - **Build command:** *(lascia vuoto)*
   - **Publish directory:** `.`
6. Clicca **Deploy site**

Netlify ti assegna un URL tipo `random-name-123.netlify.app`.
Puoi rinominarlo in **Site settings → Domain management → Change site name**
(es. `le-mie-ricevute.netlify.app`).

### 4. Installa l'app sul telefono

- **iPhone:** Apri l'URL in Safari → icona condivisione → "Aggiungi alla schermata Home"
- **Android:** Apri l'URL in Chrome → comparirà automaticamente il banner "Installa"

### 5. Configura l'API key

Nell'app, vai su ⚙️ **Impostazioni** e inserisci la tua API key Anthropic.
La chiave resta salvata solo sul tuo dispositivo (localStorage).

---

## 🔄 Come aggiornare l'app

Quando modifichi il codice con Claude:

1. Claude ti dà i file aggiornati
2. Sostituisci i file nel tuo repo GitHub (upload da browser o `git push`)
3. Netlify rileva il commit e fa il deploy automatico (~30 secondi)
4. L'app sul telefono si aggiorna al prossimo avvio

**Da browser GitHub:**
1. Apri il file da modificare nel repo
2. Clicca l'icona matita (✏️ Edit)
3. Incolla il nuovo contenuto
4. Clicca **Commit changes**
5. Netlify deploya in automatico

**Da terminale:**
```bash
# Dopo aver sostituito i file
git add .
git commit -m "Aggiornamento: descrizione della modifica"
git push
```

---

## 💡 Note

- **Nessun server richiesto** — è tutto statico (HTML/JS/CSS)
- **Dati locali** — le ricevute restano in localStorage sul dispositivo
- **Offline** — la shell dell'app funziona anche senza connessione
- **API Anthropic** — serve connessione solo per l'analisi AI delle foto
- **Gratis** — Netlify free tier è più che sufficiente per uso personale
