# 🌸 Workflow — Siti Web Ponza.online
*Documentazione operativa per la creazione e gestione dei siti del progetto Ponza.online*

---

## 📁 Progetti

| Sito | Repo GitHub | Stato |
|------|-------------|-------|
| `lamaisonfiorita.ponza.online` | `euroteamintadv/lamaisonfiorita` | ✅ Online |
| `villaolimpia.ponza.online` | `euroteamintadv/villaolimpia` | 🔜 In arrivo |
| `laguardia.ponza.online` / `guardia.ponza.online` | `euroteamintadv/laguardia` | 🔜 In arrivo |
| `ponza.online` | `euroteamintadv/ponza` | 🔜 In arrivo |

---

## 🛠️ Stack Tecnico

- **Frontend**: HTML5 + CSS3 + Vanilla JS (single file `index.html`)
- **Font**: Google Fonts — Cormorant Garamond + Jost
- **Icone**: Font Awesome 6.4.0
- **Hosting**: GitHub Pages (gratuito)
- **Dominio**: Namecheap — `ponza.online`
- **SSL**: Let's Encrypt via GitHub Pages (automatico)

---

## 🎨 Design System — Palette "Casa Rosa di Ponza"

```css
--rosa:        #D97B6A;   /* Rosa ponzese — primary */
--rosa-dark:   #B85C4A;   /* Rosa antico — hover */
--rosa-light:  #F2C4B8;   /* Rosa chiaro — accenti */
--rosa-pale:   #FBF0ED;   /* Rosa pallido — backgrounds */
--bianco:      #F8F4F0;   /* Bianco calce */
--bianco-puro: #FFFFFF;
--verde:       #2B4A1E;   /* Verde persiane */
--deep:        #1C2B3A;   /* Blu notte porto — header/footer */
--terracotta:  #B86845;   /* Pavimento terrazzo */
--text:        #2C2420;
--text-light:  #6B5550;
--sand:        #E8DDD4;
```

**Ispirazione**: facciata rosa, persiane verde scuro, pavimento in cotto, muri bianchi calce — architettura tradizionale ponzese.

---

## 🚀 Procedura Creazione Nuovo Sito

### 1. Preparazione materiali
- [ ] Raccogliere foto dalla struttura (iPhone ok)
- [ ] Raccogliere eventuale video (15-30 sec)
- [ ] Numero WhatsApp
- [ ] Indirizzo e CIN (Codice Identificativo Nazionale)
- [ ] Testi: descrizione, servizi, tariffe

### 2. Ottimizzazione immagini
```python
# Pillow — installazione
pip install Pillow --break-system-packages

# Parametri ottimizzazione
MAX_WIDTH = 1920px
QUALITY = 82
FORMAT = JPEG progressivo
# Risultato atteso: -70/85% di peso
```

### 3. Ottimizzazione video (se presente)
```bash
ffmpeg -i input.mov \
  -vf "scale=1280:720" \
  -c:v libx264 \
  -crf 28 \
  -preset slow \
  -profile:v baseline \
  -level 3.1 \
  -pix_fmt yuv420p \
  -r 24 \
  -an \
  -movflags +faststart \
  hero.mp4
# Risultato atteso: -85/90% di peso
```

### 4. Struttura file
```
repo-name/
├── index.html        # Tutto in un file
├── CNAME             # sottodominio.ponza.online
├── hero.mp4          # (opzionale) video hero ottimizzato
└── images/
    ├── hero_*.jpeg
    ├── gallery_*.jpeg
    └── ...
```

### 5. Creare repo su GitHub
```bash
# Via API
curl -X POST \
  -H "Authorization: token TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name":"REPO_NAME","description":"...","private":false}' \
  https://api.github.com/user/repos

# Push iniziale
git init
git checkout -b main
git add .
git commit -m "🌸 Launch: Nome Sito"
git remote add origin https://TOKEN@github.com/euroteamintadv/REPO_NAME.git
git push -u origin main
```

### 6. Configurare GitHub Pages
1. Vai su `github.com/euroteamintadv/REPO_NAME/settings/pages`
2. Source → **Deploy from a branch**
3. Branch → **main** → **/ (root)** → **Save**
4. Custom domain → inserisci `sottodominio.ponza.online` → **Save**
5. Attendere certificato SSL (fino a 24h) poi spuntare **Enforce HTTPS**

### 7. Configurare DNS su Namecheap
1. `namecheap.com` → Domain List → `ponza.online` → **Manage**
2. Tab **Advanced DNS** → **Add New Record**

| Type | Host | Value |
|------|------|-------|
| `CNAME Record` | `sottodominio` | `euroteamintadv.github.io` |

3. Propagazione: 15 min — 2 ore
4. Verifica: `dnschecker.org/#CNAME/sottodominio.ponza.online`

---

## 🔄 Workflow Aggiornamenti

```bash
# Modifiche al sito
git add .
git commit -m "📝 Descrizione modifica"
git pull --rebase origin main
git push origin main
```

**Regola**: raggruppare sempre più modifiche in un unico push.

---

## 📸 Best Practice Immagini

| Uso | Dimensione consigliata | Note |
|-----|----------------------|------|
| Hero foto | 1920×1080 | Ken Burns effect per movimento |
| Hero video | 1280×720, 24fps, no audio | Max 15 sec, MP4 H.264 |
| Gallery | 1920px larghezza max | JPEG progressivo |
| About accent | 800px | Bordo bianco 6px |

**Hero effect Ken Burns** (CSS):
```css
@keyframes kenburns {
  0%   { transform: scale(1.08) translateX(0px); }
  100% { transform: scale(1.0) translateX(-20px); }
}
.hero-bg {
  animation: kenburns 12s ease-in-out infinite alternate;
}
```

---

## 🔐 Sicurezza

- **Token GitHub**: conservare in gestore password (1Password, Bitwarden, Portachiavi macOS)
- **Mai** condividere token in chat, email o file nel repo
- Rigenerare sempre il token dopo esposizione accidentale
- Usare `gh auth login` per autenticazione permanente da terminale

---

## 📋 Checklist Pre-Launch

- [ ] Tutte le immagini ottimizzate (-70% minimo)
- [ ] Nessun link o numero placeholder rimasto
- [ ] Email rimossa (contatti solo via WhatsApp)
- [ ] CIN inserito nella sezione contatti
- [ ] CNAME file presente nel repo
- [ ] GitHub Pages attivo su branch main
- [ ] DNS CNAME configurato su Namecheap
- [ ] HTTPS attivo (lucchetto 🔒 nel browser)
- [ ] Test su mobile (Safari + Chrome)
- [ ] WhatsApp floating button funzionante

---

*Ultimo aggiornamento: Maggio 2025 — lamaisonfiorita.ponza.online*
