# 📊 Tableau de bord financier à partir d’un FEC comptable

Ce projet présente un **tableau de bord financier** construit à partir d’un **Fichier des Écritures Comptables (FEC)** avec Power BI. L’objectif est de transformer un FEC brut en outil de pilotage : activité, rentabilité, trésorerie, BFR, risques clients/fournisseurs et alertes.

> ⚠️ Par confidentialité, le fichier Power BI n’est pas publié. Le dépôt contient uniquement des **captures d’écran** du rapport.

---

## 🧾 Source de données : FEC

- Fichier des Écritures Comptables conforme à la norme française.  
- Table de faits `fec` (écritures) reliée à :
  - `Dates` (calendrier complet).  
  - `PCG` (plan comptable, regroupements P&L).  
  - Tables métiers (étapes de compte de résultat, paramètres, etc.).

---

## 🧠 Objectifs du tableau de bord

- Reconstituer un **compte de résultat** (CA, marge, résultat net).  
- Suivre la **trésorerie** et le **BFR** à partir du FEC.  
- Analyser les **encours clients** (DSO, ancienneté, top clients).  
- Analyser les **dettes fournisseurs** (DPO, top fournisseurs).  
- Mettre en place des **ratios & alertes** (codes couleur).

---

## 📸 Aperçu des pages du rapport

- [Page d’accueil](https://github.com/Maia-iant/Tableau-de-bord-financier-partir-d-un-FEC-comptable/blob/main/Captures/PAGE%20ACCUEIL.jpg)
- [Page CA & Résultat](/Captures/CA.jpg)
- [Page Trésorerie](/Captures/TRESO CONFIDENTIEL.png)
- [Page BFR](/Captures/BFR.jpg)
- [Page Charges](/Captures/CHARGES.jpg)
- [Page Clients & encours](/Captures/ENCOURS CLIENTS.jpg)
- [Page Fournisseurs & dettes](/Captures/FOURNISSEURS ET DETTES.jpg)
- [Page Ratios & alertes](/Captures/RATIO ET ALERTES.jpg)

---

## 🏗️ Modélisation

- Modèle en **étoile** : table `fec` centrale + dimensions (`Dates`, `PCG`, etc.).  
- Table calendrier dédiée pour les comparaisons temporelles (N/N‑1, YTD, ratios en jours).  
- Mesures DAX pour :
  - Recalculer les soldes (débit / crédit).  
  - Calculer DSO, DPO, BFR, marges, encours, ratios.

---

## 📂 Contenu du dépôt

- `Captures/` : captures d’écran anonymisées des pages du tableau de bord.  
- `README.md` : description de la démarche, des pages et de la modélisation.

> 🔐 Aucun FEC réel, aucune donnée nominative et aucun fichier `.pbix` n’est publié.

---

## 🚀 Pistes d’évolution

- Ajouter un onglet **Prévisions & simulations** (scénarios de variation CA, charges, DSO/DPO).  
- Intégrer un budget pour comparer Réel vs Budget.  
- Gérer plusieurs exercices / sociétés à partir de FEC multiples.
