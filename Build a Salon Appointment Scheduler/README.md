### Salon Appointment Scheduler

**Description**
An interactive bash script that allows a salon to schedule appointments. The script displays available services, checks if a customer exists by phone number, adds new customers if needed, and books appointments — all backed by a PostgreSQL database.

**Technologies**
- PostgreSQL
- Bash

**Database Schema**

`customers` table
| Column | Type | Constraints |
|--------|------|-------------|
| customer_id | SERIAL | PRIMARY KEY |
| phone | VARCHAR(20) | UNIQUE, NOT NULL |
| name | VARCHAR(50) | NOT NULL |

`services` table
| Column | Type | Constraints |
|--------|------|-------------|
| service_id | SERIAL | PRIMARY KEY |
| name | VARCHAR(50) | NOT NULL |

`appointments` table
| Column | Type | Constraints |
|--------|------|-------------|
| appointment_id | SERIAL | PRIMARY KEY |
| customer_id | INT | FOREIGN KEY → customers(customer_id) |
| service_id | INT | FOREIGN KEY → services(service_id) |
| time | VARCHAR(20) | NOT NULL |

**Files**
- `salon.sh` — interactive appointment scheduling script
- `salon.sql` — database dump for rebuilding the database

**How to Run**

Rebuild the database from the dump:
```bash
psql -U postgres < salon.sql
```

Run the scheduler:
```bash
chmod +x salon.sh
./salon.sh
```

**Example Interaction**
```
~~~~~ Salon Appointment Scheduler ~~~~~

Here are the available services:

1) Cut
2) Wash
3) Color
4) Perm

Which service would you like? Enter a service ID:
1

What is your phone number?
555-555-5555

What's your name?
Fabio

What time for your appointment?
10:30

I have put you down for a Cut at 10:30, Fabio.
```

---

## Setup

### Prerequisites
- PostgreSQL installed and running
- Bash (Linux/macOS or WSL on Windows)

### Rebuild All Databases
```bash
psql -U postgres < worldcup.sql
psql -U postgres < salon.sql
```
