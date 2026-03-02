Celestial Bodies Relational Database
A PostgreSQL database mapping the known (and fictional) universe, developed as part of the freeCodeCamp Relational Database Certification. This project demonstrates proficiency in SQL schema design, establishing one-to-many relationships, and enforcing data integrity through constraints.

🌌 Project Overview
The goal of this project was to build a functional relational database using PostgreSQL that captures the hierarchical nature of celestial bodies. The database is structured to ensure that every star belongs to a galaxy, every planet to a star, and every moon to a planet.

Key Features:
Structured Hierarchy: 5 interconnected tables including galaxy, star, planet, moon, and galaxy_type.

Data Integrity: Utilizes PRIMARY KEY, FOREIGN KEY, UNIQUE, and NOT NULL constraints to ensure data remains accurate and linked.

Diverse Data Types: Implementation of various PostgreSQL types including INT, NUMERIC, VARCHAR, BOOLEAN, and TEXT.

Scalable Population: The database is populated with:

8 Galaxies

16 Stars

16 Planets

20 Moons

🛠️ Tech Stack
Database: PostgreSQL

Tools: VS Code, Terminal (psql)

📊 Database Schema
The database follows a strict relational model:

Galaxy Table: The parent table containing galaxy names, types (linked via ID), and physical characteristics.

Star Table: References galaxy_id to link stars to their parent galaxies.

Planet Table: References star_id to map planetary orbits.

Moon Table: References planet_id to track natural satellites.

Galaxy Type Table: A lookup table for classifying galaxies (Spiral, Elliptical, etc.).

🚀 How to Use
To recreate this database locally:

Ensure PostgreSQL is installed on your machine.

Clone this repository.

In your terminal, create the database:

SQL
CREATE DATABASE universe;
Import the schema and data:

Bash
psql -U postgres universe < universe.sql
Created by Christopher C Meyer as part of a professional Data Science portfolio.