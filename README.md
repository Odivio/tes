# Projet Power BI – Analyse des commandes (Superstore)

Mini-projet personnel réalisé dans le cadre de ma formation en Data Science & Management de l’Innovation. L’objectif est d’analyser les performances des ventes et des commandes d’un jeu de données type “Superstore”.

## Objectifs

- Suivre les **KPI principaux** : nombre total de commandes, ventes totales, profit total.  
- Analyser la performance par **Category**, **Sub-Category**, **Region**, **Segment** et **Person**.  
- Comparer le **profit année N vs année N‑1** à l’aide d’une table de dates dédiée et de mesures DAX temporelles.

## Modèle de données

- **Orders** : table de faits contenant les lignes de commande (Sales, Profit, Discount, Order Date, Customer, Category, Region, Segment, Person, etc.).  
- **People** : table de dimension pour les commerciaux / responsables.  
- **Date** : table de dates générée en DAX (`CALENDARAUTO`) et marquée comme table de dates, reliée à `Orders[Order Date]`.

Relations principales :
- `Date[Date]` → `Orders[Order Date]`.  
- `People[Person]` → `Orders[Person]`.

## Mesures DAX clés

- `Nb commandes = DISTINCTCOUNT( Orders[Order ID] )`  
- `Total Sales = SUM( Orders[Sales] )`  
- `Total Profit = SUM( Orders[Profit] )`  
- `Profit année précédente = CALCULATE( [Total Profit], SAMEPERIODLASTYEAR( 'Date'[Date] ) )`  

## Pages du rapport

- **Analyse des commandes**  
  - 3 cartes KPI : nombre de commandes, ventes totales, profit total.  
  - Graphiques principaux :  
    - Profit total par Category.  
    - Nombre de commandes par Category.  
    - Profit total par Region.  
  - Détails :  
    - Tableau Sub‑Category avec Nb commandes, Total Sales, Total Profit.  
    - Nombre de commandes par Category et Person.  
    - Visuel Profit total vs Profit année précédente (par année).

## Outils et workflow

- **Power BI Desktop** – modélisation et création du rapport (format PBIP).  
- **VS Code + Git** – versionning du projet PBIP (fichiers JSON/TMDL) et intégration avec GitHub.  
- **GitHub** – hébergement du projet et partage dans un portfolio data.

