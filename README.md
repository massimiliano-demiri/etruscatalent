# Etrusca Talent – modulo di candidatura

Sito statico di una sola pagina (`index.html`) con il modulo di candidatura per il casting di Etrusca Talent (Perugia). Nessuna build, nessun framework, nessuna dipendenza. Funziona con Netlify Forms e Cloudinary, entrambi nei piani gratuiti.

## Cosa fa
- Raccoglie dati, parametri, esperienze e disponibilità delle candidate.
- Comprime le foto nel browser (max 1600px, JPEG) per restare sotto il limite di ~8 MB di Netlify Forms.
- Carica il video (max 100 MB) su Cloudinary e invia a Netlify solo il link; in alternativa la candidata può incollare un link.

## Pubblicare su Netlify
1. Su Netlify: **Add new site** → **Import an existing project** → **GitHub** e scegli questa repo.
2. Lascia **vuoti** *Build command* e *Publish directory* (il file `netlify.toml` imposta già `.`).
3. Premi **Deploy**. Netlify rileva il modulo `candidatura` al primo deploy.

## Notifiche email
In Netlify: **Site configuration** → **Forms** → **Form notifications** → **Add notification** → **Email notification**, scegli il form `candidatura` e inserisci l'indirizzo che riceverà le candidature.

## Cloudinary (video)
1. Crea un account gratuito su [cloudinary.com](https://cloudinary.com) e annota il **Cloud name** (nella Dashboard).
2. **Settings** → **Upload** → **Upload presets** → **Add upload preset**:
   - *Signing mode*: **Unsigned**
   - *Folder*: una cartella dedicata, ad esempio `etrusca-talent-video`
   - *Allowed formats*: solo formati video (es. `mp4, mov, webm, m4v, avi`)
3. Salva e annota il nome del preset.

## Dove sostituire CLOUD_NAME e UPLOAD_PRESET
In cima allo `<script>` di `index.html` sostituisci:

```js
const CLOUD_NAME = 'IL_TUO_CLOUD_NAME';
const UPLOAD_PRESET = 'IL_TUO_UPLOAD_PRESET';
const MAX_VIDEO_MB = 100;
```

Non sono segreti: non inserire mai la API secret di Cloudinary nel sito.

## Da personalizzare
- Nel testo del consenso privacy in `index.html` sostituisci `info@tuodominio.it` con l'email reale.
