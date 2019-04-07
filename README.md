"# neptun_db" 

# Kiindulópont

Eredeti fájlnév: AA_mintafeladat_20160216.csv

Átnevezett: neptun_db.csv

# Második verzió: neptun_db_v2.csv

- új delimiter: tab
- új encoding: utf-8
- "Átlag" oszlop:
  - float kompatibilitás
  - hiányzó érték nullára alakítása
- "Kumulált átlag" oszlop:
  - float kompatibilitás
  - hiányzó érték nullára alakítása

A hiányzó érték nullára alakításával a nulla átlag a tanulmányi eredmények hiányát jelenti.
Ezeknek az **átlagoknak az átlagolásakor** azonban ezt figyelembe kell venni: *a nulla nem lehet beleszámolva az átlagba*.