
# 📱 App Ionic "Rilievi e Perizie"

Questa è un'app mobile sviluppata in **Ionic + Angular** per la gestione di rilievi fotografici e perizie tecniche, con caricamento su server e gestione di autenticazione via API REST.

---

## 🚀 Funzionalità principali

- **Login Utente**  
  ➔ Inserimento di `nome`, `cognome`, `password` → login tramite API → salvataggio token JWT.

- **Caricamento Perizia**
  - Scatto di fotografie direttamente dalla fotocamera o caricamento da galleria.
  - Possibilità di aggiungere un commento per ogni foto.
  - Salvataggio di coordinate GPS (Geolocation API).
  - Invio di foto, descrizione, coordinate e data/ora al server.

- **Autenticazione**
  - Utilizzo di **JWT** (`authToken`) salvato in `localStorage`.

- **Cloudinary**
  - Le immagini sono caricate su **Cloudinary** (servizio cloud di gestione immagini online).
  
---

## 🛠️ Stack Tecnologico

- **Ionic + Angular** (standalone components)
- **Capacitor** (per fotocamera e geolocalizzazione)
- **HttpClient** (per comunicazione API REST)
- **Cloudinary** (per il caricamento immagini)
- **Capacitor Geolocation** + **Capacitor Camera**
- **Render.com** (per ospitare il backend Node.js/Express)

---

## ⚙️ Setup ambiente

1. **Clona il progetto:**

```bash
git clone https://github.com/tuo-repo/tuo-progetto.git
cd tuo-progetto
```

2. **Installa dipendenze:**

```bash
npm install
```

3. **Installa Capacitor Plugins:**

```bash
npm install @capacitor/camera @capacitor/geolocation
npx cap sync
```

4. **Crea un file `.env`** (se usi Cloudinary):

```env
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

5. **Compila e lancia su browser:**

```bash
ionic serve
```

6. **Per provare su dispositivo Android:**

```bash
npx cap add android
npx cap open android
# oppure
ionic capacitor run android -l --external
```

*(il flag `-l` permette il Live Reload)*

---

## 🌍 Note importanti

- In ambiente **web** (`ionic serve`) gli stili possono apparire più belli grazie alla devtools Chrome Mobile View.  
  Su **mobile reale** invece, vengono applicati solo gli stili scritti correttamente dentro:
  - il file `.scss` della pagina (`login.page.scss`, `dashboard.page.scss`, ecc.)
  - o il `global.scss` globale.

- Evitare di scrivere troppi stili `inline` negli HTML (`style="..."`) per compatibilità tra web e mobile.

- Per visualizzare i log degli errori su device: 

```bash
adb logcat
```

---

## 🔥 Backend API

- **Login:** `POST /api/login`
- **Upload perizia:** `POST /api/upload-perizia`
- Autenticazione via Bearer Token nell'header.

---

## 📸 Come funziona il caricamento immagini

- Quando carichi una foto:
  - la foto viene convertita in base64,
  - viene inviata al server backend,
  - il server la carica su Cloudinary,
  - e salva l'URL Cloudinary nel database insieme ai dati della perizia.

---

## 📋 TODO / Migliorie Future

- Migliorare gestione errori utente.
- Sistema di logout e refresh del token.
- Push Notification su esito caricamento.
- UI migliorata su mobile tramite SCSS.

---

# 📞 Supporto

Se hai bisogno di aiuto puoi aprire una issue oppure contattare il team dev.  
🚀
