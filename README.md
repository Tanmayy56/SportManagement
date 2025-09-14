# SportManagement
A MySQL-based Sport Management System with schema, seed data, and sample queries for managing players, teams, coaches, and matches.

SportManagement — MySQL Database Project

A relational database project for sports management.  
This schema manages sports, players, teams, coaches, and matches with realistic relationships and example queries.  

The project includes:
- Database schema (`CREATE DATABASE`, tables with foreign keys).
- Seed data (sports, players, coaches, teams, matches).
- Example SQL queries (players, teams, matches, wins, etc.).
- Deployment instructions (local MySQL or Docker).

Schema Overview

- Sport → List of sports (Indoor/Outdoor).  
- Player → Player details linked to a sport.  
- Coach → Coach details linked to a sport.  
- Team → Teams with assigned coaches.  
- Player_Team → Many-to-many mapping between players and teams.  
- Matches → Match history with participating teams, location, date, and winner.








