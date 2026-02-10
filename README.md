# kotlin-tech-friday

## Code Structure

```
src/main/kotlin/com/dittnamn/
├── domain/                 # Inre kärnan (Helt oberoende av ramverk)
│   ├── models/             # Data classes (t.ex. User, Product)
│   ├── repository/         # Interfaces (Portar inåt)
│   └── services/           # Affärslogik (Services)
├── data/                   # Infrastruktur (Implementationsdetaljer)
│   ├── database/           # Exposed-tabeller och DAO:er
│   ├── repository/         # Implementation av domain-interfaces
│   └── remote/             # Ev. anrop till andra API:er
├── api/                    # Presentationslagret (Ktor)
│   ├── routes/             # API-endpoints
│   ├── dto/                # Data Transfer Objects (Request/Response)
│   └── plugins/            # Ktor-konfiguration (Serialization, JWT)
└── Application.kt          # Main-entry point (Hopsättning av allt)
```
