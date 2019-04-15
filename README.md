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

# Harmadik verzió: neptun_db_v3.csv

- új **oszlopsorrend** az ésszerűség érdekében:
    - MultiIndex
        'Key',
        'FélévSorszám',
    - y
        'KépzésStátusz',
        'FélévesStátusz',

    - tanulmányi átlagok
        'Kumulált átlag',
        'Átlag',

    - kreditek
        'Féléven kumulált teljesített kredit',
        'Féléven kumulált felvett kredit',

        'Féléven teljesített kredit',
        'Féléven felvett kredit',

    - félév egyéb
        'Félév', 
        'Pénzügyi státusz', 

    - képzés egyéb
        'Aktív félévek', 
        'Képzés jogviszony kezdete', 
        'Képzési szint', 
        'Modulkód', 
        'Tagozat',

    - hallgató egyéb
        'Nem', 
        'Születési dátum', 
        'Irányítószám'

- **MultiIndex** beállítása: Key, FélévSorszám
- **Kategória változók:** a memóriaigény 40%-kal csökkent.
  - 'KépzésStátusz',
  - 'FélévesStátusz',
  - 'Pénzügyi státusz', 
  - 'Képzési szint', 
  - 'Modulkód', 
  - 'Tagozat',
  - 'Nem', 
  - 'Irányítószám'

- A MultiIndex és Kategória változók munkafolyamatot újra kell csinálni beolvasás után, így a folyamat egyszerű reprodukálhatósága érdekében **Python packagebe** foglaltam a betöltést:
  - !pip install loadneptun
  - import loadneptun
  - df = loadneptun.loadneptun(3) # ez betölti a neptun_db_v3.csv-t githubról egy dataframebe MultiIndexszel, kategóriaváltozókkal

# Negyedik verzió: neptun_db_v4.csv