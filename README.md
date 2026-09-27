# Projet UBER Pickups - CDSD - Bloc3

<img width="250" height="250" alt="Logo UBER EATS" src="https://github.com/user-attachments/assets/052d04d5-60a5-4ec8-9a1d-867a3d9a937b" />

**Auteur :** Patrick GROUILLET - JEDHA BOOTCAMP - DAFS-FT-17

**Objectif :** Prédire les points chauds de prise en charge UBER-EATS à New-York par clustering non-supervisé, 
afin de recommander aux chauffeurs les zones où se positionner selon le jour et l'heure

## Livrables

| Fichier | Description |
|---|---|
|'Projet UBER.ipynb' | Notebook principal - pipeline complet (preprocessing, KMeans, DBSCAN, évaluation, cartes Plotly) |
| "Fichier support de soutenance à reporter"|
| 'README.md | Ce fichier explicatif |

## Données

Télécharger les fichiers suivants depuis le dépôt public :
- `uber-raw-data-apr14.csv` à - `uber-raw-data-sep14.csv`

Colonnes du dataset d'origine : 'Date/Time', 'Lat', 'Lon', 'Base'

## Dépendances Python (principales bibliothèques)
pandas numpy scikit-learn matplotlib plotly

## Code d'Exécution
jupyter notebook : Projet UBER.ipynb
(temps d'exécution total : moins d'une minute sur mon poste)

##  Traitement

### Fusion des fichiers pour obtenir une seule base de données
### Exclusion des outliers
### Visualisation globale des volumes par créneaux horaires jour par jour
### Clusterisation par méthode du coude et de la silhouette
### Visualisation des points chauds en fonction du jour et de l'heure

## Conclusions

### Interprétation :

KMeans fournit une partition géographique exhaustive utile pour la répartition uniforme de la flotte
DBSCAN identifie les vraies zones denses de pickups et isole les zones périphériques comme bruit
(plus proche de la réalité opérationnelle)
La densité des pickups varie fortement selon les jours et les heures :
ce qu'un chauffeur doit voir à 18h00 un vendredi dans les quartiers de Midtown, Williamsburg ou Downtown
n'est pas identique à ce qu'il doit voir un lundi dans les quartiers des aéroports JFK ou La Guardia

### Recommandation : combiner les deux :

KMeans pour la vue stratégique 24h
DBSCAN pour la vue tactique en temps réel (avec mise à jour toutes les 15 minutes sur fenêtre glissante)

### Perspectives envisageables :

Métrique haversine plutôt qu'euclidienne standardisée (DBSCAN avec metric='haversine' sur radians)
afin de tenir compte de l’allure sphérique de la Terre
HDBSCAN pour éviter le réglage manuel d'EPS
Dashboard Plotly Dash / Streamlit en temps réel pour l'application chauffeur
A/B test : mesurer la réduction effective du temps d'attente suite au déploiement


