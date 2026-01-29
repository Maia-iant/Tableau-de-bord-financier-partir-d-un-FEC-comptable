# 📊 Tableau de bord financier à partir d’un FEC comptable

Ce projet présente un **tableau de bord financier** construit à partir d’un **Fichier des Écritures Comptables (FEC)**, avec Power BI. L’objectif est de transformer un FEC brut en outil de pilotage pour la direction : activité, rentabilité, trésorerie, BFR, risques clients/fournisseurs et alertes.

> ⚠️ Par confidentialité, le fichier Power BI n’est pas publié. Le dépôt contient uniquement des **captures d’écran** du rapport.

---

## 🧾 Source de données : FEC

- Fichier des Écritures Comptables conforme à la norme française.  
- Table de faits `fec` (écritures) reliée à :
  - `Dates` (calendrier complet).  
  - `PCG` (plan comptable général, regroupements P&L).  
  - Tables métiers (étapes de compte de résultat, paramètres de simulation, etc.).

À partir de cette base, le rapport reconstruit les principaux états financiers et indicateurs de pilotage.

---

## 🧠 Objectifs du tableau de bord

- Reconstituer un **compte de résultat** (CA, marge, résultat net).  
- Suivre la **trésorerie** et le **BFR** à partir des écritures.  
- Analyser les **encours clients** (DSO, ancienneté, top clients).  
- Analyser les **dettes fournisseurs** (DPO, poids par fournisseur).  
- Mettre en place des **ratios & alertes** (codes couleur).  

---

## 📸 Aperçu des pages du rapport

> Les images ci‑dessous sont stockées dans le dossier `captures/`.

### 🏠 Page d’accueil

Page de bienvenue avec visuel de contexte et titre du rapport.

![Page d’accueil](captures/PAGE-ACCUEIL.jpg)

---

### 📈 CA & Résultat

Suivi du chiffre d’affaires, de la marge commerciale et du résultat net (mensuel et annuel), avec graphique waterfall du compte de résultat.

![Page CA & Résultat](captures/CA.jpg)

---

### 💶 Trésorerie

Analyse des soldes de trésorerie et des flux (encaissements / décaissements), avec masquage des données sensibles.

![Page Trésorerie](captures/TRESO-CONFIDENTIEL.jpg)

---

### 🔄 BFR (Besoin en Fonds de Roulement)

BFR mensuel en montant, variation du BFR par mois et interprétation (immobilisation ou libération de liquidités).

![Page BFR](captures/BFR.jpg)

---

### 💸 Charges

Répartition des charges fixes et variables, top 10 des postes de charges à partir du FEC (comptes de classe 6).

![Page Charges](captures/CHARGES.jpg)

---

### 👥 Clients & encours

Encours clients par mois, détail par client, DSO par client, part de chaque client dans l’encours et analyse par tranches d’ancienneté.

![Page Clients et encours](captures/ENCOURS-CLIENTS.jpg)

---

### 🧾 Fournisseurs & dettes

Encours fournisseurs, DPO global, top 10 des dettes par fournisseur et évolution mensuelle du DPO.

![Page Fournisseurs et dettes](captures/FOURNISSEURS-ET-DETTES.jpg)

---

### 🚦 Ratios & alertes

Vue synthétique des indicateurs clés : DSO, DPO, BFR, trésorerie, marge commerciale, résultat net, avec code couleur (vert / rouge) pour identifier rapidement les points d’alerte.

![Page Ratios & alertes](captures/RATIO-ET-ALERTES.jpg)

---

## 🏗️ Modélisation

- Modèle en **étoile** : table `fec` centrale + dimensions (`Dates`, `PCG`, etc.).  
- Table calendrier dédiée pour la time intelligence (variations N/N‑1, YTD, DSO/DPO).  
- Mesures DAX pour :
  - Recalculer les soldes (débit / crédit).  
  - Calculer DSO, DPO, BFR, marges, encours, ratios.  

---

## 📂 Contenu du dépôt

- `captures/` : captures d’écran anonymisées des pages du tableau de bord.  
- `README.md` : description de la démarche, des pages et de la modélisation.

> 🔐 Aucun FEC réel, aucune donnée nominative et aucun fichier `.pbix` n’est publié.

---

## 🚀 Pistes d’évolution

- Ajouter un onglet **Prévisions & simulations** (scénarios de variation CA, charges, DSO/DPO).  
- Intégrer un budget pour comparer Réel vs Budget.  
- Gérer plusieurs exercices / sociétés à partir de FEC multiples.

