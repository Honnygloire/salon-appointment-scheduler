#  Salon Appointment Scheduler  
Projet freeCodeCamp – Relational Databases Certification

Ce projet fait partie du cursus **Relational Databases** de freeCodeCamp.  
Il consiste à créer un programme Bash interactif utilisant PostgreSQL pour gérer les **clients**, **services** et **rendez‑vous** d’un salon.

---

## 📁 Contenu du dépôt

| Fichier | Description |
|--------|-------------|
| **salon.sh** | Script Bash interactif permettant de réserver un rendez‑vous |
| **salon.sql** | Dump complet de la base PostgreSQL (structure + données) |
| *(non requis mais utilisés dans le projet)* |
| `examples.txt` | Exemples de sortie fournis par freeCodeCamp |

---

## 🗄️ Structure de la base de données

La base `salon` contient trois tables :

### **customers**
| Colonne | Type | Contraintes |
|--------|------|-------------|
| customer_id | SERIAL | PRIMARY KEY |
| phone | VARCHAR | UNIQUE, NOT NULL |
| name | VARCHAR | NOT NULL |

### **services**
| Colonne | Type | Contraintes |
|--------|------|-------------|
| service_id | SERIAL | PRIMARY KEY |
| name | VARCHAR | NOT NULL |

### **appointments**
| Colonne | Type | Contraintes |
|--------|------|-------------|
| appointment_id | SERIAL | PRIMARY KEY |
| customer_id | INT | REFERENCES customers(customer_id), NOT NULL |
| service_id | INT | REFERENCES services(service_id), NOT NULL |
| time | VARCHAR | NOT NULL |

---

## ✂️ Fonctionnement du script `salon.sh`

Le script :

### ✔️ Affiche la liste des services disponibles  
Format :  
`1) cut`  
`2) color`  
`3) perm`  
…  

### ✔️ Demande à l’utilisateur :
- le **service** souhaité → `SERVICE_ID_SELECTED`
- le **numéro de téléphone** → `CUSTOMER_PHONE`
- le **nom** si le client n’existe pas encore → `CUSTOMER_NAME`
- l’**heure du rendez‑vous** → `SERVICE_TIME`

### ✔️ Insère automatiquement :
- un nouveau client si le téléphone n’existe pas
- un rendez‑vous dans la table `appointments`

### ✔️ Affiche un message final conforme aux tests :

```
I have put you down for a cut at 10:30, Fabio.
```

---

## ▶️ Exécution locale

### 1. Importer la base
```bash
psql -U postgres < salon.sql
```

### 2. Rendre le script exécutable
```bash
chmod +x salon.sh
```

### 3. Lancer le programme
```bash
./salon.sh
```

---

## 🎓 Objectif pédagogique

Ce projet valide les compétences suivantes :

- Création et gestion de bases PostgreSQL  
- Relations entre tables (clé primaire / clé étrangère)  
- Scripts Bash interactifs  
- Requêtes SQL dynamiques  
- Gestion d’erreurs et validation utilisateur  

---

## ✨ Auteur

Projet réalisé par **Honnygloire MBOMBOTO TO HOUNDA**  
Dans le cadre de la certification freeCodeCamp – Relational Databases.

