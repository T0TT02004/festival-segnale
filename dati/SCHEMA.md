# Schema dei dati — Segnale

## 1. Entità
Il modello dati del festival si basa su due entità principali: **Evento** (archiviato in `dati/eventi.json`) e **Sede** (archiviata in `dati/sedi.json`).

## 2. Campi delle entità

### Evento (`dati/eventi.json`)
| Campo | Tipo | Descrizione | Esempio |
| :--- | :--- | :--- | :--- |
| `id` | `number` | Identificativo univoco dell'evento | `1` |
| `titolo` | `string` | Nome dell'appuntamento | `"Lettere in movimento"` |
| `data` | `string` | Data dell'evento in formato ISO (`YYYY-MM-DD`) | `"2026-06-12"` |
| `orario` | `string` | Ora di inizio (`HH:MM`) | `"10:00"` |
| `categoria` | `string` | Tipologia di appuntamento (`Incontro`, `Laboratorio`, `Mostra`) | `"Incontro"` |
| `descrizione` | `string` | Breve testo descrittivo dell'attività | `"Come cambia un messaggio quando cambiano le lettere?..."` |
| `immagine` | `string` | Percorso relativo dell'illustrazione associata | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | `string` | Testo alternativo per l'accessibilità dell'immagine | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | `number` | Chiave esterna che collega l'evento alla relativa sede | `1` |

### Sede (`dati/sedi.json`)
| Campo | Tipo | Descrizione | Esempio |
| :--- | :--- | :--- | :--- |
| `id` | `number` | Identificativo univoco della sede | `1` |
| `nome` | `string` | Nome della sede del festival e dell'edificio ospitante | `"Officina Nord — Sede centrale"` |
| `indirizzo` | `string` | Via, numero civico e città della sede | `"Corso Duca degli Abruzzi 24, Torino"` |

## 3. Chiavi primarie
* **Evento:** `id` (numerico, univoco all'interno della collezione e stabile nel tempo).
* **Sede:** `id` (numerico, univoco all'interno della collezione e stabile nel tempo).

## 4. Relazioni
Tra **Sede** ed **Evento** esiste una relazione **uno-a-molti (`1:N`)**:
* Una sede può ospitare più eventi.
* Ogni evento si svolge in una sola sede.
* Il collegamento avviene tramite la chiave esterna `Evento.sede_id`, che fa riferimento alla chiave primaria `Sede.id`.

## 5. Quantità
* **Eventi:** 6 record
* **Sedi:** 3 record

## 6. Gestione e aggiornamento dei dati
I dati sono gestiti direttamente dai curatori/sviluppatori del sito modificando manualmente i file JSON (`dati/eventi.json` e `dati/sedi.json`) all'interno della repository e pubblicando le modifiche (ad esempio tramite commit e deploy su GitHub Pages o server statico).

## 7. Che cosa mostra la pagina
La pagina **Programma** (`programma.html`) legge i dati dai due file JSON e genera dinamicamente le schede degli appuntamenti in ordine cronologico, mostrando per ciascun evento: l'illustrazione, la data, l'orario, la categoria, il titolo, la descrizione e il nome della sede ricavato incrociando `sede_id` con `sedi.json`.

---

## Schema concettuale (Mermaid)

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : ospita

    SEDE {
        number id PK
        string nome
        string indirizzo
    }

    EVENTO {
        number id PK
        string titolo
        string data
        string orario
        string categoria
        string descrizione
        string immagine
        string immagine_alt
        number sede_id FK
    }