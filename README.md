# Analyseur Checklist Audit

## Objectif du projet
Outil d’analyse automatisée des checklists d’audit de supervision dans le domaine aéronautique.  
Il permet de **calculer les statistiques de conformité** à partir des fichiers Excel utilisés lors des inspections, et d’identifier les questions non satisfaisantes pour alimenter les plans d’actions correctives.

---

## Fonctionnalités v1
- Lecture d’un fichier Excel de checklist (colonnes : numéro, référence réglementaire, question, directive, réponse, statut, commentaire).
- Comptage par statut : satisfaisant, non satisfaisant, sans objet, non évalué.
- Calcul du taux de conformité selon la règle métier validée :  
  

Taux de conformité = satisfaisant / (satisfaisant + non satisfaisant + non évalué)

  
  → Les « sans objet » sont exclus du dénominateur.
- Extraction des questions non satisfaisantes (numéro, question, commentaire).
- Sortie :
  - Affichage à l’écran du récapitulatif (comptages + taux en % avec 2 décimales).
  - Export des questions non satisfaisantes dans un fichier `actions_correctives.csv`.

---

## Hors périmètre v1 (déféré à une v2)
- Suivi de l’évolution entre plusieurs audits dans le temps.
- Gestion des échéances des plans d’action.
- Agrégation multi‑aéroports.
- Interface graphique.

---

## Critère objectif de réussite
Un fichier test de 34 questions dont la composition est connue (ex. : 23 satisfaisant, 6 non satisfaisant, 4 sans objet, 1 non évalué).  
- Calcul manuel : \(23 ÷ (23+6+1) = 76,67\%\).  
- Le programme doit afficher exactement ce taux, les bons comptages, et lister les 6 questions non satisfaisantes.  
- La réussite est validée si le résultat du programme correspond au calcul manuel.

---

## Installation et utilisation
1. **Cloner le dépôt**
   ```bash
   git clone <url_du_depot>
   cd analyseur-checklist-audit

## Créer et activer l’environnement virtuel

python -m venv venv
venv\Scripts\activate   # Windows
source venv/bin/activate # Linux/Mac


## Installer les dépendances
pip install -r requirements.txt


## Lancer l’analyse
python analyseur-checklist-audit-vf.py


Structure du projet
analyseur-checklist-audit/
│
├── README.md
├── .gitignore
├── requirements.txt
├── venv/                # environnement virtuel (non versionné)
├── analyseur-checklist-audit-vf.py          # script principal
└── data/
    └── checklist.xlsx    # fichier d’exemple


