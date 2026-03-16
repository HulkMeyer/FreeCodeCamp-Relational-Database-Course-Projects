# Periodic Table Database

A PostgreSQL database and bash lookup script completed as part of the [freeCodeCamp Relational Database Certification](https://www.freecodecamp.org/learn/relational-database/).

---

## Project Overview

This project involved fixing and restructuring an existing periodic table database, then building an interactive bash script that accepts an atomic number, symbol, or element name as an argument and returns detailed information about that element.

---

## Database Schema

### `elements` table
| Column | Type | Constraints |
|--------|------|-------------|
| atomic_number | INT | PRIMARY KEY |
| symbol | VARCHAR(2) | UNIQUE, NOT NULL |
| name | VARCHAR(40) | UNIQUE, NOT NULL |

### `properties` table
| Column | Type | Constraints |
|--------|------|-------------|
| atomic_number | INT | PRIMARY KEY, FOREIGN KEY → elements(atomic_number) |
| atomic_mass | FLOAT | NOT NULL |
| melting_point_celsius | NUMERIC | NOT NULL |
| boiling_point_celsius | NUMERIC | NOT NULL |
| type_id | INT | FOREIGN KEY → types(type_id), NOT NULL |

### `types` table
| Column | Type | Constraints |
|--------|------|-------------|
| type_id | SERIAL | PRIMARY KEY |
| type | VARCHAR(50) | NOT NULL |

**Types stored:** metal, nonmetal, metalloid

---

## Database Fixes Applied

The original database had several issues that were corrected:

- Renamed `weight` → `atomic_mass`
- Renamed `melting_point` → `melting_point_celsius`
- Renamed `boiling_point` → `boiling_point_celsius`
- Added `NOT NULL` constraints to melting and boiling point columns
- Added `UNIQUE` and `NOT NULL` constraints to `symbol` and `name` columns
- Added foreign key from `properties` to `elements`
- Created a `types` table and replaced the `type` VARCHAR column with a `type_id` foreign key
- Changed `atomic_mass` column type to `FLOAT` to remove trailing zeros
- Capitalized all element symbols
- Removed the non-existent element with atomic number 1000
- Added Fluorine (atomic number 9) and Neon (atomic number 10)

---

## Files

- `element.sh` — bash script that accepts an element argument and outputs its information
- `periodic_table.sql` — database dump for rebuilding the database

---

## How to Run

### Rebuild the database
```bash
psql -U postgres < periodic_table.sql
```

### Run the script
```bash
chmod +x element.sh
./element.sh
```

### Example usage
```bash
# Search by atomic number
./element.sh 1

# Search by symbol
./element.sh H

# Search by name
./element.sh Hydrogen
```

### Example output
```
The element with atomic number 1 is Hydrogen (H). It's a nonmetal, with a mass of 1.008 amu. Hydrogen has a melting point of -259.1 celsius and a boiling point of -252.9 celsius.
```

### No argument provided
```
Please provide an element as an argument.
```

### Element not found
```
I could not find that element in the database.
```

---

## Git Commit Convention

Commits in this project follow the conventional commits format:
- `feat:` — new features
- `fix:` — bug fixes
- `chore:` — maintenance tasks
- `refactor:` — code restructuring
- `test:` — test additions or changes

---

## Certification

This project is part of the freeCodeCamp [Relational Database Certification](https://www.freecodecamp.org/learn/relational-database/), which covers PostgreSQL, Bash scripting, and Git.
