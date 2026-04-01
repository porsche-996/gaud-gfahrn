# Guad Gfahrn – Website Featuresheet
**Stand:** April 2026 | **Version:** v20 | **Dateien:** index.html · style.css · main.js

---

## 1. Frontend-Features

### 1.1 Allgemeines Design & UX
- Premium Dark-Mode Design (Gold `#C9A84C` / Dunkel `#0A0A0C`)
- Vollständiger **Light/Dark-Mode** Toggle mit persistenter Speicherung
- **Responsives Layout** – optimiert für Desktop, Tablet und Mobile
- Smooth Scroll, Reveal-Animationen beim Scrollen
- Sticky Navigation mit Blur-Effekt
- Floating Telefon-Button (immer sichtbar auf Mobile)
- SEO-Metadaten, Open Graph (WhatsApp/Facebook-Vorschau), Schema.org (TaxiService)
- Favicon + Apple Touch Icon als SVG

### 1.2 Mehrsprachigkeit
9 vollständig übersetzte Sprachen mit Flaggen-Dropdown:

| Kürzel | Sprache   | Kürzel | Sprache   |
|--------|-----------|--------|-----------|
| DE     | Deutsch   | ES     | Español   |
| EN     | English   | PL     | Polski    |
| TR     | Türkçe    | RU     | Русский   |
| IT     | Italiano  | TL     | Tagalog   |
| FR     | Français  |        |           |

Alle UI-Texte, Fehlermeldungen, Platzhalter, Modal-Inhalte und Buchungsbestätigungen sind vollständig übersetzt. Sprachwechsel funktioniert live ohne Seitenreload.

### 1.3 Preisrechner / Buchungsformular

#### Routeneingabe
- Dynamische **Haltestellen-Liste** (Start + Ziel + beliebig viele Zwischenziele)
- **Adress-Autocomplete** via OpenStreetMap Nominatim (ohne Cookies, DSGVO-konform)
- IATA-Flughafencode-Erkennung (→ automatische Namensauflösung)
- Live-Routenberechnung via **Geoapify Routing API** (nur bei Cookie-Zustimmung)
- Bei Cookie-Ablehnung: **Luftlinien-Schätzung** (× 1,35 Straßenfaktor) als Fallback
- Interaktive **Leaflet-Karte** mit Goldfarbe-Route und beschrifteten Markers
- Routenübersicht-Bar: Start → Ziel, Distanz, Fahrzeit

#### Rückfahrt
- Auffälliger **Toggle-Card** mit animiertem Switch (Gold-Design)
- Separates Datum + Uhrzeit für Rückfahrt
- Option: **Abweichendes Rückfahrt-Ziel** mit eigenem Adressfeld + Autocomplete
- Bei abweichendem Ziel: API berechnet komplette Hin+Rück-Strecke korrekt
- Routenvisualisierung zeigt auch Rückweg auf der Karte

#### Flugdaten-Integration
- Automatische Fluginfo-Box wenn Start oder Ziel ein Flughafen ist
- Eingabe: Flugnummer, Herkunftsflughafen (IATA-Autocomplete), Landezeit
- **Automatische Abholzeitberechnung**: Landung + 45 Min. (Passkontrolle + Gepäck)
- Flugverfolgungshinweis (Verspätungsanpassung)
- Separate Felder für Hin- und Rückflug

#### Fahrzeugklassen (7 Klassen)

| Klasse            | Grundpreis | Inkl. km | Extra/km | Max. Pax | Max. Koffer |
|-------------------|-----------|----------|----------|----------|-------------|
| Economy           | 189 €     | 60 km    | 2,40 €   | 3        | 2           |
| Economy Green     | 204 €     | 60 km    | 2,45 €   | 3        | 2           |
| Business Class    | 219 €     | 60 km    | 2,60 €   | 3        | 2           |
| Business Class XL | 229 €     | 60 km    | 2,60 €   | 5        | 5           |
| Business Class XXL| 239 €     | 60 km    | 2,60 €   | 7        | 7           |
| Premium Green     | 249 €     | 60 km    | 2,70 €   | 2        | 2           |
| Premium VIP       | 319 €     | 60 km    | 4,50 €   | 2        | 2           |

- **Auto-Upgrade**: Fahrzeugklasse wird automatisch angepasst wenn Passagier-/Gepäckzahl das Fahrzeug überschreitet
- Fahrzeugbilder + Beschreibungen pro Klasse
- Preisanzeige: großer Goldpreis, erscheint nach Routenberechnung

#### Datum & Zeit
- Datumsfeld mit automatischer Mindestdatum-Validierung
- Rückfahrt-Datum frühestens: Abholzeit + Fahrzeit + 15 Min. Puffer
- Validierung verhindert Rückfahrt-Datum in der Vergangenheit

#### Kundendaten
- Pflichtfelder: Vor- & Nachname, **Handynummer** (mit Hinweis: nur Mobilnummern), E-Mail
- Telefonnummer-Validierung (min. 6 Ziffern, erlaubt +, -, Leerzeichen)
- E-Mail-Validierierung (Format-Check)

#### Sonderwünsche (Checkboxen)
- 🪑 Kindersitz Baby (0–13 kg)
- 🪑 Kindersitz Kleinkind (9–18 kg)
- 🪑 Kindersitz Kind (15–36 kg)
- 🐾 Haustier *(nur in Transportbox)*
- 🧳 Sperrgepäck
- 🌅 Abfahrt vor 5:00 Uhr
- 🏢 Geschäftskunde *(öffnet Geschäftskunden-Block)*
- 💬 Sonstiges *(öffnet Kommentarfeld)*

#### Geschäftskunden-Block
Wird sichtbar wenn „Geschäftskunde" angehakt:
- Toggle: **Rechnungsadresse angeben** (eingeklappt, öffnet per Klick)
- Rechnungsadresse (Pflichtfeld, Freitextfeld mehrzeilig)
- **Steuernummer / USt-IdNr.** (optional, für internationale Kunden)
- **CC-E-Mails für Rechnungsstellung**: beliebig viele E-Mail-Adressen per ＋-Button hinzufügbar, einzeln entfernbar

#### Aktionsbuttons
Nach Preisberechnung erscheinen zwei Buttons nebeneinander:
- **✉️ Unverbindlich anfragen** – öffnet Anfrage-Modal
- **🔒 Verbindlich bestellen** – startet Buchungsprozess mit Zahlungsauswahl

### 1.4 Unverbindliche Anfrage (Modal)
- Felder: Name (Pflicht), E-Mail (Pflicht), Handynummer (optional), Nachricht (Pflicht)
- Vorausfüllung mit bereits eingegebenen Kundendaten
- Öffnet nach Validierung das **Standard-E-Mail-Programm** mit vorformulierter Mail an `info@guadgfahrn.de`
- Funktioniert auch **ohne Cookie-Zustimmung**
- Vollständig in 9 Sprachen übersetzt

### 1.5 Sprachwarnung
Bei jeder Sprache außer Deutsch erscheint vor den Buchungsbuttons ein goldgelber Warnhinweis:

> „Der Fahrer spricht möglicherweise nicht Ihre gewählte Sprache. Bitte stellen Sie sicher, dass Sie auf Deutsch oder Englisch kommunizieren können."

In der jeweiligen Landessprache formuliert. Erscheint/verschwindet live beim Sprachwechsel.

### 1.6 Kundenkonto (Login-System)

#### Funktionsumfang
- **Login** (E-Mail + Passwort), **Registrierung** (Name, E-Mail, Telefon, Passwort), **Passwort vergessen** (Formular-Stub)
- Login-Button in der Navigation, zeigt nach Login den Vornamen
- **Formular-Vorausfüllung**: nach Login werden Name, E-Mail und Telefon automatisch ins Buchungsformular übertragen
- Abmelden löscht die Session

#### Technische Details (aktuell: Frontend-only)
- Nutzerdaten werden in `localStorage` gespeichert (`gg_users`, `gg_auth_user`)
- Passwörter werden im Klartext lokal gespeichert → **erfordert echtes Backend für Produktivbetrieb**
- Passwort-Vergessen-Funktion ist ein UI-Stub ohne Backend-Anbindung

### 1.7 Modals & rechtliche Seiten
Alle vollständig übersetzt, dynamisch aus i18n-Daten gerendert:
- **Impressum** (§ 5 TMG)
- **Datenschutzerklärung** (DSGVO, Cookies, externe Dienste, Betroffenenrechte)
- **AGB** (Zahlungsbedingungen, Stornierung, Haftung)
- **Zahlungsart-Modal** (Bargeld / EC-Karte beim Fahrer)

### 1.8 Cookie-Banner (DSGVO)
- Erscheint beim ersten Besuch nach 800 ms
- Buttons: **✓ Akzeptieren** / **✕ Ablehnen**
- Entscheidung wird in `localStorage` gespeichert (`gg_cookie_consent`)

**Bei Zustimmung:** Google Fonts werden geladen, Karte + Routing funktionieren vollständig

**Bei Ablehnung:**
- Google Fonts → Systemschriften als Fallback
- Interaktive Karte → nicht geladen (CARTO-Tiles bleiben blockiert)
- Geoapify Routing API → blockiert
- Adress-Autocomplete (Nominatim) → läuft weiter (berechtigtes Interesse, Art. 6 Abs. 1 lit. f DSGVO)
- Routenberechnung → Luftlinien-Schätzung × 1,35
- Buchung & Anfrage → weiterhin vollständig möglich

---

## 2. Backend & Externe Dienste

### 2.1 Externe APIs (bereits eingebunden)

| Dienst | Zweck | Consent nötig | Kosten |
|--------|-------|--------------|--------|
| **OpenStreetMap Nominatim** | Adress-Autocomplete, Geocoding | Nein (berecht. Interesse) | Kostenlos |
| **Geoapify Routing API** | Streckenberechnung, Route auf Karte | Ja | Free: 3.000 Anfragen/Tag |
| **Leaflet.js** | Interaktive Karte (Open Source) | Ja | Kostenlos |
| **CARTO** | Kartenkacheln (Tiles) | Ja | Kostenlos (Fair Use) |
| **Google Fonts** | Schriftarten (DM Sans, Playfair Display) | Ja | Kostenlos |
| **EmailJS** | E-Mail-Versand (Buchungsbestätigung) | Nein (Vertragserfüllung) | Free: 200 Mails/Monat |

### 2.2 EmailJS (Buchungsversand)

**Status:** Konfiguriert, aber noch nicht mit echten Zugangsdaten versehen.

Zwei E-Mail-Templates vorgesehen:
- `order_encrypted` → an Betreiber (verschlüsselte Buchungsdaten)
- `order_confirm` → an Kunden (Buchungsbestätigung)

**Konfiguration** (in `main.js` einzutragen):
```javascript
const EMAILJS_CONFIG = {
  publicKey:         'DEIN_EMAILJS_PUBLIC_KEY',
  serviceId:         'DEIN_SERVICE_ID',
  templateOperator:  'order_encrypted',
  templateCustomer:  'order_confirm',
};
```

**Schritte zur Aktivierung:**
1. Konto anlegen auf [emailjs.com](https://www.emailjs.com)
2. E-Mail-Service verknüpfen (Gmail, SMTP, etc.)
3. Zwei Templates anlegen (Betreiber + Kunde)
4. Public Key + Service ID in `main.js` eintragen

### 2.3 Supabase (Buchungsdatenbank)

**Status:** Vorbereitet, aber noch nicht mit echten Zugangsdaten versehen.

Buchungen werden als JSON-Payload in eine Supabase-Tabelle geschrieben. Dient als zentrales Buchungs-Backend / FleetDesk-Ersatz.

**Konfiguration** (in `main.js` einzutragen):
```javascript
const SUPABASE_URL  = 'DEIN_SUPABASE_URL';
const SUPABASE_ANON = 'DEIN_SUPABASE_ANON_KEY';
```

**SQL zum Anlegen der Tabelle:**
```sql
CREATE TABLE buchungen_incoming (
  id         uuid DEFAULT gen_random_uuid() PRIMARY KEY,
  ext_id     text UNIQUE NOT NULL,
  payload    jsonb NOT NULL,
  created_at timestamptz DEFAULT now(),
  processed  boolean DEFAULT false
);
ALTER TABLE buchungen_incoming ENABLE ROW LEVEL SECURITY;
CREATE POLICY "anon_insert" ON buchungen_incoming
  FOR INSERT TO anon WITH CHECK (true);
CREATE POLICY "anon_select" ON buchungen_incoming
  FOR SELECT TO anon USING (processed = false);
```

**Schritte zur Aktivierung:**
1. Kostenloses Konto auf [supabase.com](https://supabase.com) (Region: eu-central-1 für DSGVO)
2. Neues Projekt anlegen → SQL ausführen
3. Settings → API → Project URL + anon key in `main.js` eintragen

**Fallback ohne Supabase:** Buchungen werden in `localStorage` zwischengespeichert (`fleetdesk_003_queue`) bis Verbindung verfügbar ist.

### 2.4 Buchungs-Payload (Datenstruktur)
Jede Buchung enthält folgende Felder:

```
order_id, fahrtart, abholort, zielort, rueckfahrt_ziel,
zwischenziele, abholdatum, abholzeit, rueckfahrt_bool,
rueckfahrtdatum, rueckfahrtzeit, fahrzeugklasse, passagiere,
koffer, sonderwuensche, flug_nummer, flug_abflughafen,
flug_ankunft, zahlungsart, stunden (null), fahrttyp,
kunde_name, kunde_telefon, kunde_email, sprache,
geschaeftskunde { invoiceAddr, taxNumber, ccEmails }
```

### 2.5 Noch benötigte Backend-Komponenten

| Komponente | Priorität | Beschreibung |
|-----------|-----------|--------------|
| **Echtes Auth-Backend** | Hoch | Nutzerdaten dürfen nicht im localStorage liegen. Supabase Auth oder ähnliches nötig. |
| **Passwort-Reset per E-Mail** | Hoch | Aktuell nur UI-Stub ohne E-Mail-Versand. |
| **EmailJS-Templates** | Hoch | Müssen auf emailjs.com angelegt werden. |
| **Supabase-Datenbankanbindung** | Mittel | Buchungen werden sonst nur lokal zwischengespeichert. |
| **Geoapify-Key absichern** | Mittel | API-Key liegt im Frontend-Code (Domain-Beschränkung im Geoapify-Dashboard setzen). |
| **SSL-Zertifikat / HTTPS** | Hoch | Pflicht für DSGVO und für Leaflet (Mixed-Content-Policy). |
| **Domain-Weiterleitung** | Niedrig | `www.guadgfahrn.de` → korrekte Kanonisierung bereits im HTML. |

---

## 3. Technischer Stack

| Bereich | Technologie |
|---------|-------------|
| Frontend | Vanilla HTML5 / CSS3 / JavaScript (ES2020+) |
| Keine Frameworks | Kein React, Vue, Angular — rein native Implementierung |
| Karte | Leaflet.js 1.9.4 (CDN: cdnjs.cloudflare.com) |
| Schriften | DM Sans + Playfair Display (Google Fonts, Consent-abhängig) |
| Icons | Emoji-basiert (keine externen Icon-Libraries) |
| Datenspeicher | `localStorage` (Consent, Auth, Buchungs-Queue) |
| Build-System | Keines — statische Dateien, direkt deploybar |
| Hosting | Beliebig (Apache, Nginx, Cloudflare Pages, etc.) |

---

## 4. Deployment-Checkliste

- [ ] EmailJS-Konto + Templates einrichten → Keys in `main.js` eintragen
- [ ] Supabase-Projekt anlegen → Keys in `main.js` eintragen
- [ ] Supabase Auth für Nutzerverwaltung aktivieren (ersetzt localStorage-Auth)
- [ ] Geoapify API-Key im Dashboard auf die Domain beschränken
- [ ] SSL-Zertifikat einrichten (HTTPS)
- [ ] `www.guadgfahrn.de` → Server-Weiterleitung konfigurieren
- [ ] `og-image.jpg` für Social-Media-Vorschau erstellen und hochladen
- [ ] DSGVO: Cookie-Banner + Datenschutzerklärung von Rechtsexperten prüfen lassen

---

*Dieses Featuresheet wurde automatisch aus dem Quellcode (index.html, style.css, main.js) generiert.*
