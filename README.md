# 📊 Tableau de bord financier à partir d’un FEC comptable

Ce projet présente un **tableau de bord financier** construit à partir d’un **Fichier des Écritures Comptables (FEC)**, en utilisant Power BI. L’objectif est de transformer un FEC brut en outil de pilotage pour la direction : CA, résultat, trésorerie, BFR, clients, fournisseurs, ratios et simulations.

> ⚠️ Par confidentialité, le fichier Power BI n’est pas partagé. Le dépôt contient uniquement des **captures d’écran** illustrant le rapport final et la structure du modèle.

---

## 🧾 Source de données : FEC

- Fichier des Écritures Comptables conforme à la norme française.  
- Table de faits `fec` (écritures) + dimensions :
  - `Dates` (calendrier complet).  
  - `PCG` (plan comptable, regroupements P&L).  
  - Tables métiers (étapes de compte de résultat, paramètres de simulation, etc.).

---

## 🧠 Objectifs

- Reconstituer un **compte de résultat** (CA, marge, résultat net).  
- Suivre **trésorerie** et **BFR** à partir du FEC.  
- Analyser **encours clients** (DSO, ancienneté).  
- Analyser **dettes fournisseurs** (DPO, poids par fournisseur).  
- Mettre en place des **ratios/alertes** (vert, orange, rouge).  
- Proposer une page **“Prévisions & simulations”** avec scénarios *what‑if*.

---

## 🧩 Pages du rapport

- **CA & Résultat** : CA mensuel, marge, résultat net, waterfall P&L.  
- **Trésorerie** : solde mensuel, encaissements/décaissements, comptes 51xx.  
- **BFR** : BFR en montant et en jours, variation mensuelle.  
- **Clients & encours** : encours par client, DSO global et par client, tranches d’ancienneté.  
- **Fournisseurs & dettes** : dettes par fournisseur, DPO global et par fournisseur.  
- **Ratios & alertes** : KPI DSO, DPO, BFR, trésorerie, marge, résultat avec codes couleur.  
- **Prévisions & simulations** : paramètres de variation CA/charges/DSO/DPO, indicateurs prévisionnels.  
- **Synthèse A4** : page “one‑page” pour export PDF avec 6–8 indicateurs clés.

---

## 🏗️ Modélisation

- Modèle en **étoile** : table `fec` centrale, reliée aux dimensions.  
- Table calendrier dédiée pour les calculs temporels (YTD, N/N‑1, ratios en jours).  
- Mesures DAX séparées entre :
  - Réalité (`CA`, `Resultat_Net`, `DSO`, `DPO`, `BFR`, etc.).  
  - Prévisions (`CA_Prevu`, `Resultat_Net_Prev`, `BFR_Prev`, etc.).

---

## 📸 Contenu du dépôt

- Dossier `captures/` : captures d’écran des pages du rapport.  
- `README.md` : description du projet, objectifs, structure du modèle.  
- Éventuels schémas de modèle ou extraits de formules génériques (sans données réelles).

> 🔐 Aucun FEC réel, aucune donnée sensible et aucun fichier `.pbix` ne sont publiés.

---

## 🚀 Pistes d’évolution

- Ajout d’un vrai **budget** pour comparer Réel vs Budget.  
- Scénarios avancés (stress tests sur DSO/DPO, variation de volumes et de marges).  
- Gestion multi‑exercices / multi‑sociétés à partir de plusieurs FEC.
