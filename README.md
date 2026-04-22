# Candea - Backend

[Italian version below](#candea---backend-italiano)

Candea is the backend API for the Candea e-commerce platform, dedicated to the sale of artisanal candles. Built with Node.js and Express, it handles the business logic, database management, and order processing for the application.

## Project Overview

The backend serves as the core engine for Candea, providing RESTful endpoints for the frontend to consume. It manages product listings, category filtering, discount code validation, and a robust order fulfillment system that includes automated email confirmations and stock management.

## Features

- **Product Management**: 
  - Dynamic listing with support for search queries.
  - Advanced filtering by category and promotional status.
  - Sorting by price, popularity (best sellers), and recent arrivals.
- **Order Fulfillment System**:
  - Secure processing of customer orders.
  - Automatic stock level updates upon successful purchases.
  - Integration with **Nodemailer** to send HTML-formatted order confirmations to customers.
- **Discount System**: Validation and application of time-sensitive discount codes.
- **Categorization**: Management of product categories for better catalog organization.
- **Centralized Error Handling**: Robust middleware for managing 404 Not Found and 500 Internal Server errors.
- **CORS Configuration**: Secure communication setup with the frontend application.

## Tech Stack

- **Runtime**: [Node.js](https://nodejs.org/)
- **Framework**: [Express.js](https://expressjs.com/)
- **Database**: [MySQL](https://www.mysql.com/) (using `mysql2` driver)
- **Email Service**: [Nodemailer](https://nodemailer.com/) (configured for SMTP services like Mailtrap)
- **Middleware**: CORS, Express JSON parser, static file serving.

## Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/andrea-pugliatti/candea-backend.git
   cd candea-backend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Environment Variables**:
   Create a `.env` file in the root directory based on `.env.example`:
   ```env
   DB_HOST=localhost
   DB_USER=your_user
   DB_PASSWORD=your_password
   DATABASE=candea_db
   FRONTEND_HOST=localhost
   FRONTEND_PORT=5173
   BACKEND_PORT=3000
   MAILTRAP_USER=your_mailtrap_user
   MAILTRAP_PASS=your_mailtrap_password
   ```

4. **Setup the Database**:
   Import one of the SQL backups located in the `db/` folder into your MySQL server to populate the schema and initial data.

5. **Run the server**:
   - **Development mode** (with watch):
     ```bash
     npm run dev
     ```
   - **Production mode**:
     ```bash
     npm start
     ```

## Project Structure

```text
candea-backend/
├── controllers/    # Request handlers and business logic
├── data/           # Database connection and mailer configuration
├── db/             # SQL backups and database diagrams
├── middlewares/    # Custom Express middlewares (errors, 404)
├── public/         # Static assets (product images)
├── routers/        # API route definitions
└── server.js       # Main entry point and server configuration
```

## API Endpoints

- `GET /api/products`: Retrieve all products (supports query params: `sortBy`, `order`, `promo`, `q`, `category`).
- `GET /api/products/:slug`: Get detailed information for a specific product.
- `GET /api/products/bySold`: Get products sorted by total units sold.
- `GET /api/categories`: List all available categories.
- `GET /api/discount/:code`: Validate a specific discount code.
- `POST /api/orders`: Submit a new order and trigger email confirmation.

---

# Candea - Backend (Italiano)

Candea è l'API backend per la piattaforma e-commerce Candea, dedicata alla vendita di candele artigianali. Sviluppata con Node.js ed Express, gestisce la logica di business, la gestione del database e l'elaborazione degli ordini per l'applicazione.

## Panoramica del Progetto

Il backend funge da motore principale per Candea, fornendo endpoint RESTful per il consumo da parte del frontend. Gestisce l'elenco dei prodotti, il filtraggio per categoria, la validazione dei codici sconto e un robusto sistema di evasione degli ordini che include conferme email automatizzate e gestione del magazzino.

## Funzionalità

- **Gestione Prodotti**: 
  - Elenco dinamico con supporto per query di ricerca.
  - Filtraggio avanzato per categoria e stato promozionale.
  - Ordinamento per prezzo, popolarità (più venduti) e ultimi arrivi.
- **Sistema di Evasione Ordini**:
  - Elaborazione sicura degli ordini dei clienti.
  - Aggiornamento automatico dei livelli di scorte al completamento dell'acquisto.
  - Integrazione con **Nodemailer** per inviare conferme d'ordine in formato HTML ai clienti.
- **Sistema di Sconti**: Validazione e applicazione di codici sconto a tempo.
- **Categorizzazione**: Gestione delle categorie di prodotto per una migliore organizzazione del catalogo.
- **Gestione Centralizzata degli Errori**: Middleware robusti per la gestione degli errori 404 Not Found e 500 Internal Server Error.
- **Configurazione CORS**: Configurazione per la comunicazione sicura con l'applicazione frontend.

## Stack Tecnologico

- **Runtime**: [Node.js](https://nodejs.org/)
- **Framework**: [Express.js](https://expressjs.com/)
- **Database**: [MySQL](https://www.mysql.com/) (tramite il driver `mysql2`)
- **Servizio Email**: [Nodemailer](https://nodemailer.com/) (configurato per servizi SMTP come Mailtrap)
- **Middleware**: CORS, Express JSON parser, gestione file statici.

## Installazione e Configurazione

1. **Clona la repository**:
   ```bash
   git clone https://github.com/andrea-pugliatti/candea-backend.git
   cd candea-backend
   ```

2. **Installa le dipendenze**:
   ```bash
   npm install
   ```

3. **Configura le Variabili d'Ambiente**:
   Crea un file `.env` nella directory root basandoti su `.env.example`:
   ```env
   DB_HOST=localhost
   DB_USER=tuo_utente
   DB_PASSWORD=tua_password
   DATABASE=candea_db
   FRONTEND_HOST=localhost
   FRONTEND_PORT=5173
   BACKEND_PORT=3000
   MAILTRAP_USER=tuo_utente_mailtrap
   MAILTRAP_PASS=tua_password_mailtrap
   ```

4. **Configura il Database**:
   Importa uno dei backup SQL situati nella cartella `db/` nel tuo server MySQL per popolare lo schema e i dati iniziali.

5. **Avvia il server**:
   - **Modalità sviluppo** (con watch):
     ```bash
     npm run dev
     ```
   - **Modalità produzione**:
     ```bash
     npm start
     ```

## Struttura del Progetto

```text
candea-backend/
├── controllers/    # Gestori delle richieste e logica di business
├── data/           # Connessione al database e configurazione mailer
├── db/             # Backup SQL e diagrammi del database
├── middlewares/    # Middleware Express personalizzati (errori, 404)
├── public/         # Asset statici (immagini dei prodotti)
├── routers/        # Definizioni delle rotte API
└── server.js       # Punto di ingresso principale e configurazione del server
```

## Endpoint API

- `GET /api/products`: Recupera tutti i prodotti (supporta i parametri: `sortBy`, `order`, `promo`, `q`, `category`).
- `GET /api/products/:slug`: Ottieni informazioni dettagliate per un prodotto specifico.
- `GET /api/products/bySold`: Ottieni i prodotti ordinati per unità totali vendute.
- `GET /api/categories`: Elenca tutte le categorie disponibili.
- `GET /api/discount/:code`: Valida uno specifico codice sconto.
- `POST /api/orders`: Invia un nuovo ordine e attiva la conferma via email.
