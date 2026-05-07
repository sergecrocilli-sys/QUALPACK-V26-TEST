# QUALPACK V23 CORE

Application de contrôle qualité et de traçabilité pour industries agroalimentaires  
Développée par CODEX EXPERTISE

Date : Avril 2026

---

## DESCRIPTION

QUALPACK est une application web locale / synchronisée permettant :

- la saisie d’échantillons de pesées réglementaires préemballés ;
- la réalisation de tests détecteurs de métaux ;
- l’édition de rapports PDF qualité ;
- l’export Excel des historiques ;
- la synchronisation cloud sécurisée via Supabase ;
- l’utilisation sur tablette / PC / smartphone ;
- un fonctionnement partiellement offline grâce à IndexedDB.

---

## FONCTIONNALITÉS PRINCIPALES

### PESÉES PRÉEMBALLÉS

- saisie de 10 ou 20 poids
- calcul moyenne
- calcul écart-type
- calcul TU1 / TU2
- verdict automatique :
  - Conforme
  - À surveiller
  - Non conforme

---

### TESTS DÉTECTEURS

- validation Fer
- validation Non Ferreux
- validation Inox
- suivi par ligne / détecteur / OF / opérateur

---

### RAPPORTS PDF

#### PDF Pesées

- détail des pesées
- moyenne brute
- tare fixe
- moyenne nette
- analyse conformité

#### PDF Détecteurs

- historique des tests
- conformité des essais

#### Rapport Qualité Dashboard PDF

- synthèse
- KPI
- traçabilité
- analyse & décision

---

## ARCHITECTURE

### FRONTEND

- HTML
- CSS
- JavaScript Vanilla

### STOCKAGE LOCAL

- IndexedDB
- LocalStorage fallback

### CLOUD

- Supabase

### PWA

- manifest.json
- service worker

---

## FICHIERS PRINCIPAUX

- index.html
- style.css
- db.js
- sync.js
- pdf-v2.js
- lignes.js
- manifest.json
- sw.js

---

## VERSION ACTUELLE

V23 CORE

Version stable de travail avant déploiement client pilote.

---

## ROADMAP

### V24

- gestion catalogue produits / clients finaux
- quantité prévue
- saisie libre OF
- opérateurs

### V25

- multi-clients
- sécurité avancée RLS
- environnement client dédié

---

## CONFIDENTIALITÉ

Les données restent la propriété exclusive de votre société et sont traitées de manière confidentielle.

---

## DÉVELOPPÉ PAR

CODEX EXPERTISE  
Serge Crocilli
