### World Cup Database

**Description**
A PostgreSQL database that stores World Cup knockout round results from 2014 and 2018. Includes a bash script to insert data from a CSV file and a query script to answer specific questions about the data.

**Technologies**
- PostgreSQL
- Bash

**Database Schema**

`teams` table
| Column | Type | Constraints |
|--------|------|-------------|
| team_id | SERIAL | PRIMARY KEY |
| name | VARCHAR(50) | UNIQUE, NOT NULL |

`games` table
| Column | Type | Constraints |
|--------|------|-------------|
| game_id | SERIAL | PRIMARY KEY |
| year | INT | NOT NULL |
| round | VARCHAR(50) | NOT NULL |
| winner_id | INT | FOREIGN KEY → teams(team_id) |
| opponent_id | INT | FOREIGN KEY → teams(team_id) |
| winner_goals | INT | NOT NULL |
| opponent_goals | INT | NOT NULL |

**Files**
- `insert_data.sh` — reads `games.csv` and populates the database, avoiding duplicate team entries
- `queries.sh` — runs a series of queries against the database including aggregations, joins, and filters
- `worldcup.sql` — database dump for rebuilding the database

**How to Run**

Rebuild the database from the dump:
```bash
psql -U postgres < worldcup.sql
```

Insert data from CSV:
```bash
chmod +x insert_data.sh
./insert_data.sh
```

Run queries:
```bash
chmod +x queries.sh
./queries.sh