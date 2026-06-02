# 🌊 Ponza.online — Master Workflow & Vision
*Documento operativo completo. Da condividere all'inizio di ogni nuova chat.*

---

## 🧠 Contesto — Leggi prima di tutto

Stiamo costruendo una **piattaforma di siti web verticale** per le attività dell'Isola di Ponza.

- **Dominio ombrello**: `ponza.online` (registrato su Namecheap)
- **Hosting**: GitHub Pages (gratuito, deploy automatico)
- **Account GitHub**: `euroteamintadv`
- **Site-builder**: `https://euroteamintadv.github.io/site_builder/`
- **Vision finale**: self-service completo — il cliente compila un form, il sito va live automaticamente su `sottodominio.ponza.online`

---

## 📁 Progetti Esistenti

| Sito | Repo | Stato |
|------|------|-------|
| `lamaisonfiorita.ponza.online` | `euroteamintadv/lamaisonfiorita` | ✅ Online |
| `site_builder` | `euroteamintadv/site_builder` | 🔧 In sviluppo |
| `villaolimpia.ponza.online` | `euroteamintadv/villaolimpia` | 🔜 In arrivo |
| `laguardia.ponza.online` | `euroteamintadv/laguardia` | 🔜 In arrivo |
| `ponza.online` | `euroteamintadv/ponza` | 🔜 In arrivo |

---

## 🔐 Credenziali & Accessi

### GitHub
- **Account**: `euroteamintadv`
- **URL**: `github.com/euroteamintadv`
- **Token**: conservato in gestore password (NON nel file)
- **Come generare nuovo token**:
  1. `github.com/settings/tokens`
  2. *Generate new token (classic)*
  3. Spunta: `repo` (accesso completo ai repository)
  4. Scadenza consigliata: 90 giorni
  5. Copia e salva subito in gestore password
  6. **Revocare sempre** i token esposti accidentalmente

### Namecheap
- **Dominio**: `ponza.online`
- **Pannello DNS**: `namecheap.com` → Domain List → `ponza.online` → Manage → **Advanced DNS**
- **API Namecheap**: da abilitare in Account → Profile → Tools → API Access
  - Whitelist IP richiesta
  - Endpoint: `https://api.namecheap.com/xml.response`

### Google Drive
- Cartella progetto: `site-builder/`
- Contiene: questo documento + documentazione progetti

---

## 🛠️ Stack Tecnico Attuale

```
Frontend:   HTML5 + CSS3 + Vanilla JS (single file index.html)
Font:       Google Fonts — Cormorant Garamond + Jost
Icone:      Font Awesome 6.4.0
Hosting:    GitHub Pages
Dominio:    Namecheap — ponza.online
SSL:        Let's Encrypt via GitHub Pages (automatico, ~24h)
Immagini:   Pillow (Python) — ottimizzazione locale
Video:      FFmpeg — ottimizzazione locale
```

---

## 🏗️ Architettura Vision — Site Builder Self-Service

```
Cliente apre site-builder (GitHub Pages)
        ↓
Compila form: nome attività, tipo, foto, 
              colori, testi, contatti, sottodominio
        ↓
Frontend invia dati a Backend (Railway)
        ↓
Backend Python/FastAPI:
  ├── Claude API → genera HTML sito completo
  ├── Pillow → ottimizza immagini caricate
  ├── GitHub API → crea repo + push files
  └── Namecheap API → aggiunge record CNAME
        ↓
✅ Sito live su sottodominio.ponza.online
   (HTTPS attivo entro 24h automaticamente)
```

### Stack Vision
| Layer | Tecnologia | Motivo |
|-------|-----------|--------|
| Frontend | HTML/JS (GitHub Pages) | Già esistente, zero costi |
| Backend | Python + FastAPI (Railway) | Semplice, supporta Pillow/FFmpeg |
| AI | Claude API (Anthropic) | Genera HTML su misura |
| Database | Postgres (Railway incluso) | Storico siti generati |
| Immagini | Pillow su Railway | Ottimizzazione server-side |
| Deploy | GitHub API | Crea repo + push automatico |
| DNS | Namecheap API | Aggiunge CNAME automaticamente |
| Hosting siti | GitHub Pages | Gratuito, SSL automatico |

### Costi stimati
| Servizio | Costo |
|----------|-------|
| Railway (backend) | ~$5/mese |
| GitHub Pages | Gratuito |
| Namecheap dominio | ~$15/anno |
| Claude API | Pay per use (~$0.01/sito) |
| **Totale** | **~$6/mese** |

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
--deep:        #1C2B3A;   /* Blu notte porto */
--terracotta:  #B86845;   /* Pavimento terrazzo */
--text:        #2C2420;
--text-light:  #6B5550;
--sand:        #E8DDD4;
```

### Temi Pianificati
| Tema | Palette | Adatto per |
|------|---------|-----------|
| 🌸 **Rosa Ponzese** *(fatto)* | Rosa + Bianco + Verde | B&B, case vacanza |
| 🔵 **Blu Mediterraneo** | Blu + Azzurro + Bianco | Barche, diving, sport acquatici |
| 🟡 **Giallo Limone** | Giallo + Verde + Bianco | Ristoranti, bar, trattorie |
| 🟢 **Verde Ulivo** | Verde + Beige + Marrone | Escursioni, natura, trekking |
| ⚪ **Bianco Minimal** | Bianco + Oro + Grigio | Ville lusso, case esclusive |
| 🔴 **Terracotta** | Terracotta + Bianco + Verde | Negozi, artigianato |
| 🌊 **Tramonto** | Arancio + Rosa + Blu | Hotel, resort |

Ogni tema include: palette CSS, tipografia, layout, sezioni specifiche per tipo attività.

---

## 🚀 Procedura Creazione Nuovo Sito (Manuale)

### Materiali necessari
- [ ] Foto struttura (iPhone ok, originali)
- [ ] Video breve 15-30 sec (opzionale)
- [ ] Numero WhatsApp
- [ ] Indirizzo + CIN (Codice Identificativo Nazionale)
- [ ] Testi: descrizione, servizi, tariffe
- [ ] Sottodominio desiderato (es. `villaolimpia`)

### 1. Ottimizzazione immagini
```python
pip install Pillow --break-system-packages

from PIL import Image, ImageOps
img = ImageOps.exif_transpose(Image.open(path))
if img.width > 1920:
    ratio = 1920 / img.width
    img = img.resize((1920, int(img.height * ratio)), Image.LANCZOS)
img.convert('RGB').save(path, 'JPEG', quality=82, optimize=True, progressive=True)
# Risultato atteso: -70/85% di peso
```

### 2. Ottimizzazione video
```bash
ffmpeg -i input.mov \
  -vf "scale=1280:720" \
  -c:v libx264 -crf 28 -preset slow \
  -profile:v baseline -level 3.1 \
  -pix_fmt yuv420p -r 24 -an \
  -movflags +faststart \
  hero.mp4
# Risultato atteso: -85/90% di peso
```

### 3. Struttura repo
```
repo-name/
├── index.html              # Tutto in un file
├── CNAME                   # sottodominio.ponza.online
├── PONZA_ONLINE_MASTER.md  # Questo documento
├── hero.mp4                # (opzionale)
└── images/
    ├── hero_*.jpeg
    └── *.jpeg
```

### 4. Creare repo GitHub
```bash
# Crea repo via API
curl -X POST \
  -H "Authorization: token TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name":"REPO_NAME","description":"...","private":false}' \
  https://api.github.com/user/repos

# Push
git init && git checkout -b main
git add . && git commit -m "🌸 Launch"
git remote add origin https://TOKEN@github.com/euroteamintadv/REPO_NAME.git
git push -u origin main
```

### 5. GitHub Pages
1. `github.com/euroteamintadv/REPO_NAME/settings/pages`
2. Source → **Deploy from a branch** → **main** → **/ (root)** → Save
3. Custom domain → `sottodominio.ponza.online` → Save
4. Attendere SSL (~24h) → spuntare **Enforce HTTPS**

### 6. DNS Namecheap (Manuale)
1. `namecheap.com` → Domain List → `ponza.online` → Manage → **Advanced DNS**
2. Add New Record:

| Type | Host | Value |
|------|------|-------|
| `CNAME Record` | `sottodominio` | `euroteamintadv.github.io` |

3. Verifica: `dnschecker.org/#CNAME/sottodominio.ponza.online`

### 7. DNS Namecheap (Semi-automatico)
```python
# Prerequisiti: abilitare API su Namecheap + whitelist IP
import requests

NAMECHEAP_API_KEY = "..."  # Da variabile ambiente
NAMECHEAP_USER = "..."
CLIENT_IP = "..."  # IP whitelistato

def add_cname(subdomain, value="euroteamintadv.github.io"):
    # Prima ottieni i record esistenti
    params = {
        "ApiUser": NAMECHEAP_USER,
        "ApiKey": NAMECHEAP_API_KEY,
        "UserName": NAMECHEAP_USER,
        "ClientIp": CLIENT_IP,
        "Command": "namecheap.domains.dns.getHosts",
        "SLD": "ponza",
        "TLD": "online"
    }
    r = requests.get("https://api.namecheap.com/xml.response", params=params)
    # Poi aggiungi il nuovo record CNAME ai record esistenti
    # (Namecheap API sostituisce tutti i record, non aggiunge)
    print(f"CNAME {subdomain} → {value} aggiunto")

add_cname("villaolimpia")
```

> ⚠️ **Nota**: Namecheap API richiede IP whitelistato e sovrascrive tutti i record DNS. Usare con cautela — fare sempre backup dei record esistenti prima.

---

## 📸 Best Practice Immagini

| Uso | Dimensione | Note |
|-----|-----------|------|
| Hero foto | 1920×1080 max | Ken Burns per movimento |
| Hero video | 1280×720, 24fps, no audio | Max 15 sec, MP4 H.264 |
| Gallery | 1920px larghezza | JPEG progressivo q82 |
| About accent | 800px | Bordo bianco 6px |

**Ken Burns CSS:**
```css
@keyframes kenburns {
  0%   { transform: scale(1.08) translateX(0px); }
  100% { transform: scale(1.0) translateX(-20px); }
}
.hero-bg { animation: kenburns 12s ease-in-out infinite alternate; }
```

---

## 🔄 Workflow Aggiornamenti

```bash
git add .
git commit -m "📝 Descrizione modifica"
git pull --rebase origin main
git push origin main
```
**Regola**: raggruppare sempre più modifiche in un unico push.

---

## ✅ Checklist Pre-Launch

- [ ] Immagini ottimizzate (-70% minimo)
- [ ] Nessun placeholder rimasto (numeri, testi)
- [ ] Email rimossa (solo WhatsApp)
- [ ] CIN inserito nei contatti
- [ ] CNAME file nel repo
- [ ] GitHub Pages attivo su main
- [ ] DNS CNAME su Namecheap
- [ ] HTTPS attivo 🔒
- [ ] Test Safari mobile
- [ ] WhatsApp floating button funzionante
- [ ] `PONZA_ONLINE_MASTER.md` nel repo

---

## 💬 Frase di Avvio Nuova Chat

```
Leggi PONZA_ONLINE_MASTER.md e riprendi da lì.
Nuovo progetto: [nome]
Sottodominio: [nome].ponza.online
```

---

*Ultimo aggiornamento: Giugno 2026*
