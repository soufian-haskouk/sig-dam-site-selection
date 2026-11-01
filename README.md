# 🌍 SIG & AHP - Sélection de Sites de Barrages (Oued Ghris, Maroc)

![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Master](https://img.shields.io/badge/Master-SIDI-orange)
![GIS](https://img.shields.io/badge/Domain-GIS%20%26%20Multi--Criteria-blue?style=for-the-badge&logo=arcgis)
![Methodology](https://img.shields.io/badge/Methodology-AHP%20%2F%20Saaty-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)

> **Projet académique réalisé dans le cadre du Master SIDI (Systèmes d'Information Décisionnels et Imagerie) - FST Errachidia, combinant les Systèmes d'Information Géographique (SIG) et la méthode multicritère AHP pour l'optimisation du choix des sites de barrages dans le bassin versant de l'Oued Ghris (Drâa-Tafilalet, Maroc).**

---

## 📌 Présentation du Projet
La gestion des ressources en eau constitue un enjeu majeur dans les régions arides et semi-arides, comme le bassin versant de **l'Oued Ghris**. Ce projet propose une approche méthodologique intégrée pour identifier et cartographier les sites les plus favorables à l'implantation de barrages. 

En croisant **9 critères spatiaux** sous **ArcGIS 10.8** (topographiques, hydrologiques, pédologiques, climatiques et socio-économiques) avec la méthode d'aide à la décision **AHP (Analytic Hierarchy Process)** et l'outil *Weighted Overlay*, le modèle génère une carte d'adéquation globale permettant de cibler les zones prioritaires.

---


## 🛠️ Critères & Pondération du Modèle (AHP / Weighted Overlay)

Le modèle s'appuie sur une hiérarchisation rigoureuse de **9 couches thématiques** harmonisées en projection métrique (`WGS 1984 UTM Zone 30N`) avec une résolution spatiale de 30m :

| Critère d'Évaluation | Poids AHP (%) | Classe / Zone la plus favorable | Justification Scientifique & Technique |
| :--- | :---: | :--- | :--- |
| **Pente (Slope)** | **18%** | $5.21^{\circ} - 11.95^{\circ}$ | Morphologie de gorge favorable, stabilité et capacité de retenue |
| **Distance aux Cours d'Eau** | **16%** | $0 - 202\text{ m}$ | Proximité immédiate du lit d'écoulement et de l'assiette du réservoir |
| **Ordre des Cours d'Eau** | **14%** | Ordres 5 à 7 | Ciblage du lit principal de l'Oued Ghris et des axes à fort débit |
| **Précipitations Annuelles** | **12%** | $309 - 360\text{ mm/an}$ | Apports pluviométriques plus élevés pour sécuriser le remplissage |
| **Types de Sol (Pédologie)** | **10%** | Leptosols / Regosols (Texture fine) | Étanchéité naturelle favorable à la retenue |
| **Densité de Drainage** | **10%** | $0.961 - 1.313\text{ km/km}^2$ | Forte concentration des eaux de ruissellement |
| **Occupation du Sol (LULC)** | **9%** | Sols nus / Surfaces rocheuses | Ruissellement élevé et faible coût social |
| **Altitude (Elevation)** | **7%** | $\sim 586 - 963\text{ m}$ | Zones basses de vallée et convergence gravitaire |
| **Distance aux Routes** | **4%** | $0 - 953\text{ m}$ | Accessibilité du chantier et réduction des coûts logistiques |

---
## 📸 Galerie Cartographique & Résultats

### 🔄 Synthèse de la Reclassification (Reclass)
La figure ci-dessous représente la reclassification standardisée des 9 critères sur l'échelle d'aptitude de 1 à 5 :
| Carte d'Aptitude Finale (Weighted Overlay) |
| :---: |
| ![Carte Finale](les%20maps/carte%20finale%20.jpg) |

| Synthèse de Reclassification des Critères (Reclass)| 
| :---: |
| ![Reclass Map](les%20maps/reclass.jpg) |

### 🗺️ Cartes Thématiques Détaillées
| Zone d'Implantation (2D / 3D) |
| :---: |
| ![Zone Implantation](les%20maps/zone%20etude%20.jpg) |

| Pente (Slope) | Élévation (Altitude) | Types de Sol|
| :---: | :---: |:---: |
| ![Slope](les%20maps/slope%201.jpg) | ![Type de Sol](les%20maps/type%20de%20sol.jpg) | ![Elevation](les%20maps/Elevation.jpg) |

| Ordre des Cours d'Eau | Densité de Drainage | Distance aux Oueds (Buffer) |
| :---: | :---: | :---: |
| ![Stream Order](les%20maps/stream%20order.jpg) | ![Drainage Density](les%20maps/drainage%20density.jpg) | ![Buffer](les%20maps/buffer%20.jpg) |

| Précipitations Annuelles | Occupation du Sol (LULC) | Distance aux Routes |
| :---: | :---: | :---: |
| ![Precipitations](les%20maps/Precipitations%20.jpg) | ![LULC](les%20maps/LULC%20.jpg) | ![Routes](les%20maps/distance%20aux%20routes.jpg) |


---

## ⚙️ Méthodologie & Chaîne de Traitement SIG

1. **Pré-traitement Hydrologique (DEM 30m) :** Remplissage des dépressions (*Fill*), calcul de la direction d'écoulement (*Flow Direction*), du flux cumulé (*Flow Accumulation*) et extraction du réseau hydrographique majeur (Seuil > 1000)
2. **Génération & Reclassification des Critères :** Standardisation de toutes les couches sur une échelle d'aptitude commune de **1 à 5** (où 5 représente l'aptitude maximale/idéal)
3. **Analyse Multicritère (*Weighted Overlay*) :** Combinaison linéaire pondérée des 9 couches raster sous ArcGIS 10.8.
4. **Validation :** Confrontation des résultats avec les barrages existants et planifiés dans la région de Drâa-Tafilalet

---

## 📂 Structure du Dépôt (Repository)

```text
📁 sig-dam-site-selection/
├── 📁 DATA/
│   ├── 📦 data.part1.rar        # Partie 1 des données SIG et rasters de base (87 Mo)
│   └── 📦 data.part2.rar        # Partie 2 des données SIG et rasters de base (77 Mo)
├── 📁 Reclass/                  # Couches  extrait raster reclassifiées (Échelle 1 à 5)
├── 📁 les maps/                 # Cartes thématiques finales au format image (.jpg)
├── 📁 best_sites/               # Données de la zone d'implantation prioritaire
└── 📄 README.md                 # Documentation technique du projet
