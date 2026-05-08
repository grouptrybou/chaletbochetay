# Handleiding – Website Chalet Bochetay online zetten

---

## Optie 1 – Uploaden via Plesk (aanbevolen)

### Wat heb je nodig?
- Toegang tot je Plesk-hostingpanel (URL + wachtwoord van je hosting)
- De map `_plesk/bochetay/` van op je computer

### Stappen

1. **Log in op Plesk**
   - Ga naar de URL van je hostingpanel (bv. `https://jouwserver.be:8443`)
   - Vul je gebruikersnaam en wachtwoord in

2. **Ga naar Bestandsbeheer**
   - Klik op je domein (bv. `chaletbochetay.be`)
   - Klik op **"Bestandsbeheer"** of **"File Manager"**

3. **Navigeer naar de juiste map**
   - Open de map `httpdocs` (dit is de publieke map van je website)
   - Als er al bestanden in staan (bv. een oude WordPress of standaardpagina), verwijder die eerst

4. **Upload de bestanden**
   - Klik op **"Upload"** of **"Bestanden uploaden"**
   - Selecteer **alle bestanden** uit de map `_plesk/bochetay/` op je computer:
     - `index.html`, `menu.html`, `offres.html`, `evenements.html`
     - `logo2 inv-01.svg`
     - Alle `.jpg` en `.png` afbeeldingen
     - `.htaccess`
   - Wacht tot alles geüpload is

5. **Controleer de website**
   - Ga naar `https://chaletbochetay.be` in je browser
   - De homepage moet automatisch laden (dankzij `index.html`)

6. **HTTPS activeren (als nog niet actief)**
   - Ga in Plesk naar **SSL/TLS-certificaten**
   - Klik op **"Let's Encrypt"** en activeer gratis SSL
   - Uncomment daarna de HTTPS-regels in `.htaccess`:
     ```
     RewriteEngine On
     RewriteCond %{HTTPS} off
     RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
     ```

---

## Optie 2 – Via GitHub + GitHub Pages (gratis hosting)

### Wat heb je nodig?
- Een gratis GitHub-account op [github.com](https://github.com)
- De map `_github/` van op je computer

### Stappen

#### Stap 1 – GitHub-account aanmaken
1. Ga naar [github.com/join](https://github.com/join)
2. Maak een gratis account aan

#### Stap 2 – Nieuwe repository aanmaken
1. Klik rechtsboven op **"+"** → **"New repository"**
2. Geef het een naam, bv. `chalet-bochetay`
3. Zet op **"Public"** (nodig voor gratis GitHub Pages)
4. Klik op **"Create repository"**

#### Stap 3 – Bestanden uploaden
1. Klik in je nieuwe repository op **"uploading an existing file"**
2. Sleep de volledige inhoud van de map `_github/bochetay/` naar het uploadvenster:
   - `index.html`, `menu.html`, `offres.html`, `evenements.html`
   - `logo2 inv-01.svg`
   - Alle `.jpg` en `.png` afbeeldingen
3. Scroll naar beneden → klik **"Commit changes"**

#### Stap 4 – GitHub Pages activeren
1. Ga naar **Settings** (tandwiel bovenaan de repository)
2. Klik links op **"Pages"**
3. Onder **"Branch"**: selecteer `main` en map `/` (root)
4. Klik op **"Save"**
5. Na 1–2 minuten is de site live op:
   `https://jouwgebruikersnaam.github.io/chalet-bochetay/`

#### Eigen domeinnaam koppelen (optioneel)
1. Ga naar **Settings → Pages → Custom domain**
2. Vul in: `chaletbochetay.be`
3. Ga daarna naar je domeinbeheerder en voeg een **CNAME-record** toe:
   - Naam: `www`
   - Waarde: `jouwgebruikersnaam.github.io`
4. Voor het hoofddomein (zonder www): voeg 4 **A-records** toe met de GitHub IP's:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

---

## Inhoud bijwerken

Wanneer je teksten of afbeeldingen wilt aanpassen:

1. Pas de bestanden aan in de originele werkmap
2. Kopieer de gewijzigde bestanden opnieuw naar `_plesk/bochetay/` of `_github/bochetay/`
3. Upload ze opnieuw via Plesk (bestaand bestand wordt overschreven) of GitHub

> **Tip:** Bij Plesk kan je ook direct bewerken via de ingebouwde teksteditor in Bestandsbeheer.

---

## Overzicht bestanden

| Bestand | Wat is het? |
|---|---|
| `index.html` | Homepage |
| `menu.html` | Menukaart |
| `offres.html` | Wekelijkse aanbiedingen |
| `evenements.html` | Evenementen |
| `logo2 inv-01.svg` | Logo (gebruikt overal) |
| `Mosselen.jpg` | Foto mosselen |
| `Cote a l os.jpg` | Foto côte à l'os |
| `Klaas Trybou.jpg` | Foto chef |
| `pexels-*.jpg` | Overige food-foto's |
| `ChatGPT-Image-*.png` | Hero-achtergrond homepage |
| `.htaccess` | Serverinstellingen (Plesk) |
