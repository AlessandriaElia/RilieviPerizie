# Progetto “Rilievi e Perizie”

Una soluzione per la gestione e archiviazione digitale delle perizie assicurative, composta da:
- **Web App Admin** (supervisione e gestione utenti/perizie)
- **App Mobile Android** (upload rilievi sul campo)

## 🎯 Obiettivo
Consentire a un’azienda di assicurazioni di archiviare in tempo reale su un server le fotografie e i dati di rilievi/perizie eseguite dai propri dipendenti.

## 📦 Struttura del Progetto

```
/backend          # Server Express.js e API
  ├─ routes       # Route per login, utenti, perizie
  ├─ controllers  # Logica delle API
  ├─ models       # Definizione schemi MongoDB
  └─ .env         # Variabili d’ambiente (MongoDB URI, JWT_SECRET, Cloudinary, ecc.)

/mobile           # App Ionic/Angular
  ├─ src/app
  │   ├─ login         # Pagina login
  │   ├─ dashboard     # Pagina per upload perizie
  │   └─ ...           # Altri componenti
  ├─ global.scss      # Stili globali
  └─ capacitor.config.json

README.md           # Questo file
```

## 🚀 Funzionalità Principali

### Web App Admin
- **Tecnologie:** Node.js, Express, MongoDB Atlas, Render.com  
- Creazione e gestione utenti (ruoli ADMIN/USER)  
- Login con password iniziale o Google OAuth  
- Dashboard con mappa (Google Maps) di tutte le perizie  
- Filtro per operatore, modifica descrizioni e commenti  
- Calcolo percorso e tempo di viaggio per ogni perizia  

### App Mobile Android
- **Tecnologie:** Angular, Ionic, Capacitor  
- Login operatore con JWT  
- Scatto o selezione di foto (Capacitor Camera)  
- Acquisizione automatica di coordinate GPS e data/ora  
- Upload perizia (descrizione, foto, coordinate, token)  
- Archiviazione immagini su Cloudinary  

## 🔧 Setup e Installazione

### Backend (Express.js)
1. Clona il repo e vai in `/backend`
2. Crea `.env` con:
   ```
   MONGODB_URI=<uri_mongo_atlas>
   DBNAME=RILIEVI
   JWT_SECRET=<chiave_jwt>
   CLOUDINARY_CLOUD_NAME=<cloud_name>
   CLOUDINARY_API_KEY=<api_key>
   CLOUDINARY_API_SECRET=<api_secret>
   ```
3. Installa dipendenze e avvia:
   ```bash
   npm install
   npm start
   ```

### Mobile (Ionic)
1. Clona il repo e vai in `/mobile`
2. Installa dipendenze:
   ```bash
   npm install
   ```
3. Per sviluppo web:
   ```bash
   ionic serve
   ```
4. Per build Android:
   ```bash
   ionic build
   npx cap add android
   npx cap copy android
   npx cap open android
   ```
   Attiva **Debug USB** sul dispositivo e premi ▶️ in Android Studio.

## 🌍 Note Importanti
- Scrivi stili personalizzati nei file `.scss` delle pagine o in `global.scss`.
- Non usare classi Bootstrap su mobile: usa attributi Ionic (`color="primary"`).
- Per debug su device: `adb logcat`.

## 🛠️ To-Do Futuri
- Refresh token / logout
- PWA per accesso da browser mobile
- Notifiche push
- Reportistica avanzata

---

**License:** Progetto didattico privato, non commerciale.
