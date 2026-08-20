# Datasett og API fra KA

Dokumentasjon for deg som skal bruke KAs data om kirkebygg og gravplasser.

Sist oppdatert: 20. august 2026

---

## Om dataene

KA tilbyr to datasett med tilhørende API:

- **Gravplasser** – oversikt over gravplasser i Norge som anlegg
- **Kirker og kapell** – kirkebygg og kapell

Dataene forvaltes i KAs fagsystem for eiendomsforvaltning og oppdateres
løpende av gravplassmyndighetene og fellesrådene selv.

### Merk om navnebruk

**«Gravplasser»** brukes i flertall. Geonorge har en separat oppføring kalt
«Gravplass» som er innsendt av Kartverket og gjelder gravkart etter
gravferdsforskriften § 4 – altså graver med ID og gravfeltfastmerker innenfor
den enkelte gravplass. Det er et annet datasett med et annet formål enn KAs.

**«Kirker og kapell»** omfatter begge bygningstypene. Kapell er inkludert selv
om det ikke framgår av endepunktnavnet `churches`.

---

## API

| | |
|---|---|
| **Navn** | KAs API for kirkebygg og gravplass |
| **Base-URL** | `https://ordna.planiasky.no/api` |
| **Tilgang** | Krever autentisering – ta kontakt for tilgang |

API-et dekker begge datasettene. Det finnes ikke et eget API kun for
gravplasser.

---

## Endepunkter

### Gravplasser

| Endepunkt | Innhold | Format |
|---|---|---|
| `/ka/graveyards` | Alle gravplasser | GeoJSON |
| `/ka/graveyards/{guid}` | Én gravplass | GeoJSON |
| `/ka/simple/graveyards` | Alle gravplasser, redusert feltsett | JSON |
| `/ka/public/graveyards` | Kun offentlige gravplasser i drift | JSON |

### Kirker og kapell

| Endepunkt | Innhold | Format |
|---|---|---|
| `/ka/churches` | Alle kirker og kapell | GeoJSON |
| `/ka/churches/{guid}` | Ett bygg | GeoJSON |
| `/ka/simple/churches` | Alle kirker og kapell, redusert feltsett | JSON |
| `/ka/kbfbuildings` | Kun bygg med støtte fra Kirkebygg bevaringsfond (KBF) | JSON |

Samtlige listeendepunkter støtter søkekriterier.

---

## Viktig: hvilke endepunkter gir hele settet?

Endepunktene skiller seg fra hverandre på to måter, og det er verdt å være
bevisst på hvilken:

**Redusert feltsett** (`/ka/simple/...`) gir de samme objektene som
hovedendepunktet, men med færre felter per objekt. Antallet er det samme.

**Filtrert utvalg** (`/ka/public/graveyards`, `/ka/kbfbuildings`) gir *færre
objekter* enn hovedendepunktet:

| Endepunkt | Avgrensning |
|---|---|
| `/ka/public/graveyards` | Gravplassen er offentlig og i drift |
| `/ka/kbfbuildings` | Bygget har støtte fra Kirkebygg bevaringsfond |

Dette er den vanligste kilden til forvirring. Teller du gravplasser fra
`/ka/public/graveyards` og sammenligner med `/ka/graveyards`, får du ulike tall
– og det er forventet. Bruk `/ka/graveyards` hvis du trenger det fullstendige
settet.

---

## Format

GeoJSON-endepunktene inneholder geometri og er beregnet på kartbruk.
JSON-endepunktene er beregnet på oppslag og lister der geometri ikke trengs.

---

## Kontakt

Spørsmål om datasettene, tilgang eller innhold rettes til KA, avdeling for
kirkebygg og gravplass.
