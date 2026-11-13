---
marp: true
theme: default
style: |
  section {background-color: #121114}
  h1,h2,h3 {color: #8393f0}
  p,ul,li,td,th {color: #ccc}
  section table {font-size: 0.85em}
  section table td {background-color: #121114}
  section table th {background-color: #272133; font-weight: bolder}
  pre {background-color: #17151a; color: #ccc}
  blockquote {border: 2px green solid; border-left-width: 15px; padding: 0.5em 15px;font-style: italic }
paginate: true
header: "ITIL, ITSM et GLPI"
footer: "![height:20px](https://raw.githubusercontent.com/DiginamicInternal/PublicAssets/refs/heads/main/Logo-diginamic-color-blk.png)"
---

# ITIL, ITSM et GLPI

### Gérer les services informatiques

Nicolas SAHUC

---

## 🎯 Objectifs pédagogiques

1. Présenter ITIL et son vocabulaire
2. Prioriser un ticket (urgence × impact)
3. Distinguer incident, demande, problème, changement
4. Décrire l'organisation d'un centre de services
5. Dérouler la gestion d'un incident
6. Situer les solutions d'ITSM
7. Installer et utiliser GLPI

---

## Le parcours

| #  | Étape                           | Durée  |
|----|---------------------------------|--------|
| 01 | ITIL : concepts et vocabulaire  | 1 h 30 |
| 02 | Le centre de services           | 1 h 30 |
| 03 | ITSM et solutions du marché     | 30 min |
| 04 | GLPI : installation             | 1 h 30 |
| 05 | GLPI : utilisation              | 2 h    |

---

# 1. ITIL

---

## ITIL en bref

- *IT Infrastructure Library* : des **bonnes pratiques**, pas une norme
- Né dans les années 1980, version actuelle : ITIL 4
- Organisation du SI, qualité des services, gestion des risques

---

## Le vocabulaire

| Terme | Sens |
|---|---|
| CI | élément de configuration |
| CMDB | base des CI et de leurs relations |
| KB | base de connaissances |
| SLA | engagement de niveau de service |
| Backlog | tickets affectés à une équipe |

---

## La matrice des priorités

| Urgence ＼ Impact | Faible | Moyen | Élevé |
|---|---|---|---|
| Faible | P5 | P4 | P3 |
| Moyenne | P4 | P3 | P2 |
| Élevée | P3 | P2 | **P1** |

---

## Niveaux de service (exemple)

| Priorité | Réponse | Résolution |
|---|---|---|
| P1 | 15 min | 2 h |
| P2 | 15 min | 4 h |
| P3 | 1 h | 2 jours |
| P4 | 4 h | 5 jours |
| P5 | 1 jour | 2 semaines |

---

## Quatre types de tickets

- **Incident** : un service est interrompu ou dégradé
- **Demande** : une sollicitation prévue au catalogue
- **Problème** : la cause profonde d'incidents
- **Changement** : ajout, modification, suppression d'un service

> Plusieurs incidents → un problème → un changement

---

# 2. Le centre de services

---

## Les niveaux de support

| Niveau | Missions |
|---|---|
| N1 | incidents non bloquants, demandes simples, accompagnement |
| N2 | incidents bloquants, changements simples |
| N3 | incidents et problèmes majeurs, expertise |

**Escalade** : transfert vers le niveau supérieur

---

## Les rôles

- **Front office** : point de contact, demandes simples, aiguillage
- **Back office** : expertise, causes profondes, solutions durables
- **Coordinateur·rice** : priorise, attribue, escalade, respecte les SLA
- **SDM** : relation client, SLA, amélioration continue

---

## Gérer un incident

1. Détection et enregistrement
2. Qualification
3. Affectation, escalade
4. Diagnostic
5. Résolution ou contournement
6. Clôture et compte rendu

Tout du long : **communication**. À la fin : **base de connaissances**.

---

# 3. ITSM

---

## ITIL ≠ ITSM

- **ITIL** dit *quoi* faire
- **ITSM** est *ce qu'on fait* : processus, personnes, outils

| Solution | Cible |
|---|---|
| ServiceNow | grandes entreprises |
| Jira Service Management | tech, PME, DevOps |
| GLPI | libre, PME, administrations |

---

# 4. GLPI : installation

---

## La pile LAMP

```bash
apt install -y apache2 php libapache2-mod-php mariadb-server
apt install -y php-mysql php-ldap php-curl php-gd php-intl \
               php-mbstring php-xml php-zip php-bz2
mysql_secure_installation
```

---

## Base et application

```sql
CREATE DATABASE glpidb CHARACTER SET utf8mb4;
CREATE USER 'glpiuser'@'localhost' IDENTIFIED BY '…';
GRANT ALL PRIVILEGES ON glpidb.* TO 'glpiuser'@'localhost';
```

```bash
tar -xvzf glpi-<version>.tgz -C /var/www/html
chown -R www-data:www-data /var/www/html/glpi
```

Puis `http://IP/glpi` dans un navigateur.

---

## Sécuriser dès la première connexion

- Comptes par défaut : `glpi`, `tech`, `normal`, `post-only`
- **Changer** leurs mots de passe
- **Supprimer** `install/install.php`

---

# 5. GLPI : utilisation

---

## Le ticket

Nouveau → En cours → (En attente) → Résolu → Clos

- Demandeur, catégorie, description, urgence/impact
- Suivis, attribution, solution, temps passé
- Validation par l'utilisateur avant clôture

---

## Problèmes et changements

- **Problème** : incidents liés, 5 pourquoi, Ishikawa, contournement, correction définitive
- **Changement** : justification, impact, plan, risques, **retour arrière**, tests

---

# Des questions ?

Pour toute question [adressez-vous au service pédagogie](mailto:pedagogie@diginamic.fr)
