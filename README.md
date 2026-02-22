# Analýza legálního držení zbraní a infrastruktury v České republice (Power BI projekt)
------------------------------------------------------------------------

## Popis projektu
Cílem projektu je vytvořit interaktivní Power BI report zaměřený na oblast oprávnění pro legální držení zbraní a související infrastruktury v České republice.

Report analyzuje: 
- evidenci střelnic
- držitele zbrojních průkazů (ZP)
- zbrojní licence (ZL)
- legislativní změny od roku 2026

Projekt kombinuje: 
- Časovou analýzu (trend v letech)
- Strukturální analýzu (kategorie a skupiny)
- Regionální analýzu (kraj / okres)
- Prostorovou vizualizaci (heat mapa)

------------------------------------------------------------------------

##  Zdroje dat

### 1️⃣ Seznam střelnic v krajích ČR

Zdroj: Policie České republiky – https://policie.gov.cz/soubor/seznam-strelnic-v-krajich-cr-xlsx.aspx

Soubor obsahoval 16 listů (1 list = 1 kraj).
V Power BI byly listy sloučeny pomocí Power Query, vyčištěny a sjednoceny do tabulek:
- Střelnice celá ČR 
- Klasifikace střelnic
Původní zdrojové tabulky byly po transformaci následně skryty.
------------------------------------------------------------------------

### 2️⃣ Tabulka okresů (prostorová data)

Použita open-source tabulka okresů z projektu:
https://github.com/jlacko/powerbi-cesko

Byla vytvořena hierarchie Kraj → Okres, která byla následně využita při tvorbě vizuálu Heat mapa střelnic.

------------------------------------------------------------------------

### 3️⃣ Statistiky držitelů zbrojních průkazů a licencí

Zdroj: Roční statistiky Policie ČR - https://policie.gov.cz/clanek/statistika-rocni.aspx

Data byla sloučena do jedné tabulky a zahrnují:
- Počet držitelů ZP a  ZL dle let
- Kategorie zbraní
- Počet registrovaných zbraní
Původní zdrojové tabulky byly po transformaci následně skryty.
------------------------------------------------------------------------

### 4️⃣ Nová kategorizace ZL od roku 2026

Ručně vytvořená tabulka „ZL skupiny" pomocí funkce Zadat data. Tabulka je propojena se statistikami ZP a ZL.
Zdroj: https://www.svetzbrani.cz/slovnik-pojmu/zbrojni-licence/

------------------------------------------------------------------------

## Datový model

Použité tabulky: Střelnice celá ČR, Klasifikace střelnic, Okresy, ZP a ZL, ZL, ZL skupiny,  xMěřítka (DAX míry)

Model umožňuje regionální, časovou i strukturální analýzu.

------------------------------------------------------------------------

## Vizuální část reportu

Report obsahuje 3 stránky.

Použité vizuály: Sloupcový graf, Spojnicový graf, Donut graf, Kombinovaný graf, Mapový vizuál, Treemap, Karta, Slicer

Interaktivita: Navigační menu, Cross-filtering, Slicery (Rok, Kraj, Kategorie ZL, Způsob klasifikace)

------------------------------------------------------------------------

## DAX výpočty

-   Measure pro podmíněné formátování
-   TOP 3 skupiny ZL
-   Úprava agregace Donut grafu (pro odstranění napisu "Součet z")
-   Vypočítaný sloupec v tabulce "ZL skupiny"

Všechny míry jsou uloženy v tabulce „xMěřítka".

------------------------------------------------------------------------

## Shrnutí

Projekt vytváří interaktivní analytický přehled o legálním držení zbraní a související infrastruktuře v České republice, jejich struktuře, vývoji v čase a prostorové analýze
