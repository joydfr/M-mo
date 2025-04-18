Avec plaisir Jody ! Voici un mémo clair et bien structuré en Markdown 📘 pour ton script de sauvegarde PostgreSQL automatisé :

# 🐘 Script de sauvegarde PostgreSQL —

## 🎯 Objectif

Créer un script bash qui :

- Sauvegarde automatiquement la base PostgreSQL `exo1_db`
- Stocke la sauvegarde dans un dossier `~/backups`
- Utilise un nom de fichier basé sur la date et l'heure
- Peut être étendu pour sauvegarder partiellement certaines tables

---

## 📝 Script `sauvegarde_exo1.sh`

```bash
#!/bin/bash

# 📁 Répertoire de sauvegarde
BACKUP_DIR="$HOME/backups"
mkdir -p "$BACKUP_DIR"

# 🐘 Nom de la base
DB_NAME="exo1_db"

# 🕒 Date et heure pour le nom du fichier
DATE=$(date +"%Y-%m-%d_%H-%M-%S")

# 📦 Nom du fichier de sauvegarde
FILENAME="${DB_NAME}_backup_${DATE}.dump"

# 💾 Exécution de la sauvegarde (format custom)
pg_dump -Fc "$DB_NAME" > "$BACKUP_DIR/$FILENAME"

# ✅ Confirmation
echo "Sauvegarde de '$DB_NAME' effectuée : $BACKUP_DIR/$FILENAME"



⸻

🔐 Donne les droits d’exécution

chmod +x sauvegarde_exo1.sh



⸻

▶️ Exécute le script

./sauvegarde_exo1.sh



⸻

💡 Variante : sauvegarde partielle (tables spécifiques)

Pour ne sauvegarder que certaines tables (utilisateurs, categories), modifie cette ligne :

pg_dump -Fc "$DB_NAME" > "$BACKUP_DIR/$FILENAME"

en :

pg_dump -Fc -t utilisateurs -t categories "$DB_NAME" > "$BACKUP_DIR/$FILENAME"



⸻

📂 Exemple de sortie

~/backups/exo1_db_backup_2025-04-17_15-45-32.dump



⸻

🚀 Bonus (non inclus ici, mais possible) :
	•	Ajout d’un log.txt
	•	Envoi d’un email
	•	Planification avec cron
	•	Nettoyage automatique des sauvegardes trop anciennes

⸻
```
