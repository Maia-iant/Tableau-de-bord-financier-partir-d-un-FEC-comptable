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
- [Page Trésorerie](https://github.com/Maia-iant/Tableau-de-bord-financier-partir-d-un-FEC-comptable/blob/main/Captures/TRESO%20CONFIDENTIEL.png)
- [Page BFR](/Captures/BFR.jpg)
- [Page Charges](/Captures/CHARGES.jpg)
- [Page Clients et encours](https://github.com/Maia-iant/Tableau-de-bord-financier-partir-d-un-FEC-comptable/blob/main/Captures/ENCOURS%20CLIENTS.jpg)
- [Page Fournisseurs et dettes](https://github.com/Maia-iant/Tableau-de-bord-financier-partir-d-un-FEC-comptable/blob/main/Captures/FOURNISSEURS%20ET%20DETTES.jpg)
- [Page Ratios & alertes](https://github.com/Maia-iant/Tableau-de-bord-financier-partir-d-un-FEC-comptable/blob/main/Captures/RATIO%20ET%20ALERTES.jpg)
---

## 🏗️ Modélisation et approche comptable

La modélisation repose sur une démarche d’**expertise comptable** appliquée à la data :

### Schéma de données

- **Table de faits `fec`**  
  - Issue directement du Fichier des Écritures Comptables (FEC) normé.  
  - Colonnes clés : date de pièce, journal, numéro de compte, libellés, montants débit/crédit, références de pièces, lettrage.  
  - Utilisée comme base unique pour reconstituer CA, charges, trésorerie, encours et dettes.

- **Dimension `Dates`**  
  - Calendrier complet (jour, mois, trimestre, année, AnnéeMois).  
  - Sert à toutes les analyses temporelles : évolution mensuelle, comparaisons N / N‑1, calculs en jours (DSO, DPO, BFR).  

- **Dimension `PCG` (Plan Comptable Général)**  
  - Reprise / enrichissement du plan de comptes : classe, sous‑classe, nature (ventes, achats, charges d’exploitation, charges financières, etc.).  
  - Utilisée pour construire le compte de résultat, distinguer charges fixes/variables et agréger les indicateurs par nature comptable.

- **Tables métiers complémentaires**  
  - Table des **étapes de compte de résultat** pour piloter l’affichage du P&L (chiffre d’affaires, marge commerciale, EBE, résultat net…).  
 

### Logique de calcul (DAX)

- **Reconstruction des soldes**  
  - Utilisation systématique des sens débit/crédit pour recomposer :
    - Soldes de comptes (bilan, trésorerie, tiers).  
    - Soldes par nature (ventes, achats, charges, produits financiers, etc.).  

- **Indicateurs clients / fournisseurs**  
  - **Encours clients** et **dettes fournisseurs** basés sur les comptes 41 / 40.  
  - Calcul des **DSO** (days sales outstanding) et **DPO** (days payable outstanding) à partir des encours et des flux de CA / achats sur la période.  
  - Analyse d’**ancienneté des créances** par tranches (0–30 j, 31–60 j, etc.) afin de rapprocher vision comptable et gestion du risque.

- **BFR et trésorerie**  
  - BFR calculé à partir des postes clients, fournisseurs et stocks (si disponibles), en montant et en jours de CA.  
  - Mise en relation avec les flux de trésorerie (encaissements / décaissements) pour expliquer les tensions de cash.

- **Ratios et alertes**  
  - Ratios classiques de **performance** (marge, résultat), **liquidité** (trésorerie, BFR), **délai de paiement** (DSO, DPO).  
  - Surcouche d’**alertes visuelles** (vert / orange / rouge) via des mesures dédiées, pour donner une lecture immédiate à un non‑comptable.

### Valeur ajoutée “comptable → BI”

Cette modélisation traduit les réflexes d’un **ancien comptable / auditeur** dans un environnement BI :  
- Respect de la logique PCG et des équilibres débit/crédit.  
- Contrôles de cohérence intégrés (soldes par classes, rapprochements encours ↔ CA / achats, continuité temporelle).  
- Capacité à passer très vite d’une vision “états financiers” à une vision “pilotage opérationnel” (clients, fournisseurs, trésorerie, scénarios).
---

## 👩‍💻 Profil & rôle

Ce projet a été réalisé en autonomie, depuis l’extraction du FEC jusqu’à la conception du modèle et des visuels.  
Mon profil hybride **ex‑comptable / data analyst** m’a permis de :

- Transformer la structure FEC en modèle de données exploitable (vérification des équilibres débit/crédit, cohérence des classes de comptes).  
- Mettre en place des contrôles de type **audit FEC** (encours, délais de paiement, continuité temporelle).  
- Traduire les états comptables (P&L, BFR, trésorerie) en indicateurs opérationnels compréhensibles par la direction.
- La modélisation s’appuie sur une vision “audit” du FEC : chaque indicateur peut être rattaché à des comptes précis, ce qui facilite les revues avec l’expert‑comptable, le CAC ou l’administration fiscale.

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
