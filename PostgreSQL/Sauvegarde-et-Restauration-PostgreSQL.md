# Mémo : Sauvegarde et Restauration PostgreSQL

## 1. Sauvegarde avec pg_dump

### Formats disponibles

| Format       | Option   | Commande                                    | Avantages                                  |
| ------------ | -------- | ------------------------------------------- | ------------------------------------------ |
| Texte        | (défaut) | `pg_dump ma_base > sauvegarde.sql`          | Simple, lisible, compatible                |
| Personnalisé | `-Fc`    | `pg_dump -Fc ma_base > sauvegarde.dump`     | Compressé, restauration partielle possible |
| Répertoire   | `-Fd`    | `pg_dump -Fd ma_base -f dossier_sauvegarde` | Restauration parallèle                     |
| Archive tar  | `-Ft`    | `pg_dump -Ft ma_base > sauvegarde.tar`      | Format archive standard                    |

### Options utiles

- `-t table` : sauvegarde d'une table spécifique
- `-n schema` : sauvegarde d'un schéma spécifique
- `--data-only` : uniquement les données
- `--schema-only` : uniquement la structure
- `-Z niveau` : niveau de compression (0-9)

## 2. Restauration

### Avec psql (format texte)

```
psql -d ma_base -f sauvegarde.sql
```

### Avec pg_restore (autres formats)

```
pg_restore -d ma_base sauvegarde.dump
```

### Options utiles

- `-j nombre` : restauration en parallèle
- `--data-only` : restaure uniquement les données
- `--schema-only` : restaure uniquement la structure
- `--clean` : supprime les objets avant de les recréer
- `--no-owner` : ignore les instructions de propriété
- `--exit-on-error` : arrête à la première erreur

## 3. Automatisation sous macOS

### Avec launchd

1. Créer un fichier plist dans `~/Library/LaunchAgents/`
2. Créer un script de sauvegarde
3. Charger avec `launchctl load chemin_fichier.plist`

### Avec cron

```
crontab -e
0 1 * * * /opt/homebrew/bin/pg_dump -Fc ma_base > /chemin/sauvegarde_$(date +\%Y\%m\%d).dump
```

### Exemple de script sauvegarde 15j

```Bash
#!/bin/bash

# 📁 Répertoire de sauvegarde
BACKUP_DIR="$HOME/backups"
mkdir -p "$BACKUP_DIR"

# 🐘 Nom de la base
DB_NAME="nom de la base de donnée"

# 🕒 Date et heure pour le nom du fichier
DATE=$(date +"%Y-%m-%d_%H-%M-%S")

# 📦 Nom du fichier de sauvegarde
FILENAME="${DB_NAME}_backup_${DATE}.dump"
ENCRYPTED_FILENAME="${FILENAME}.gpg"

# 💾 Exécution de la sauvegarde (format custom)
pg_dump -h 10.2.0.76 -Fc "$DB_NAME" > "$BACKUP_DIR/$FILENAME"

# 🔐 Chiffrement du fichier avec mot de passe
# Remplace 'motDePasseSuperSecret' par une variable d’environnement ou un fichier si tu veux plus de sécurité
echo "motDePasseSuperSecret" | gpg --batch --yes --passphrase-fd 0 \
  --symmetric --cipher-algo AES256 \
  -o "$BACKUP_DIR/$ENCRYPTED_FILENAME" "$BACKUP_DIR/$FILENAME"

# 🧹 Suppression des sauvegardes chiffrées de plus de 15 jours
find "$BACKUP_DIR" -type f -name "${DB_NAME}_backup_*.dump.gpg" -mtime +15 -delete

# ✅ Confirmation
echo "Sauvegarde de '$DB_NAME' chiffrée effectuée : $BACKUP_DIR/$ENCRYPTED_FILENAME"
```

### Exemple script sauvegarde 15j, 1 mois et 1 ans

```bash
#!/bin/bash

# 📁 Répertoires de sauvegarde
BACKUP_DIR="$HOME/backups/journalières"
MONTHLY_DIR="$HOME/backups/mensuelles"
YEARLY_DIR="$HOME/backups/annuelles"
mkdir -p "$BACKUP_DIR" "$MONTHLY_DIR" "$YEARLY_DIR"

# 🔐 Mot de passe de chiffrement (idéalement à placer dans une variable d'environnement)
PASSPHRASE="motDePasseSuperSecret"

# 🐘 Nom de la base
DB_NAME="base de données"

# 🕒 Horodatage
DATE=$(date +"%Y-%m-%d_%H-%M-%S")
DATE_MONTH=$(date +"%Y-%m")
DATE_YEAR=$(date +"%Y")

# 📦 Noms de fichiers
FILENAME="${DB_NAME}_backup_${DATE}.dump"
ENCRYPTED_FILENAME="${FILENAME}.gpg"

FILENAME_MONTHLY="${DB_NAME}_backup_${DATE_MONTH}.dump.gpg"
FILENAME_YEARLY="${DB_NAME}_backup_${DATE_YEAR}.dump.gpg"

# 💾 Sauvegarde PostgreSQL (format custom)
pg_dump -h 10.2.0.76 -Fc "$DB_NAME" > "$BACKUP_DIR/$FILENAME"

# 🔐 Chiffrement
echo "$PASSPHRASE" | gpg --batch --yes --passphrase-fd 0 \
  --symmetric --cipher-algo AES256 \
  -o "$BACKUP_DIR/$ENCRYPTED_FILENAME" "$BACKUP_DIR/$FILENAME"

# 🧽 Suppression de la version non chiffrée
rm "$BACKUP_DIR/$FILENAME"

# 🧹 Nettoyage des sauvegardes journalières > 15 jours
find "$BACKUP_DIR" -type f -name "${DB_NAME}_backup_*.dump.gpg" -mtime +15 -delete

# 📅 Copie mensuelle (le 1er jour de chaque mois)
if [ "$(date +%d)" == "01" ]; then
  cp "$BACKUP_DIR/$ENCRYPTED_FILENAME" "$MONTHLY_DIR/$FILENAME_MONTHLY"
  # 🧹 Suppression des sauvegardes mensuelles > 12 mois
  find "$MONTHLY_DIR" -type f -name "${DB_NAME}_backup_*.dump.gpg" -mtime +365 -delete
fi

# 📅 Copie annuelle (le 31 décembre)
if [ "$(date +%m)" == "12" ] && [ "$(date +%d)" == "31" ]; then
  cp "$BACKUP_DIR/$ENCRYPTED_FILENAME" "$YEARLY_DIR/$FILENAME_YEARLY"
  # 🧹 Suppression des sauvegardes annuelles > 5 ans
  find "$YEARLY_DIR" -type f -name "${DB_NAME}_backup_*.dump.gpg" -mtime +1825 -delete
fi

# ✅ Confirmation
echo "✅ Sauvegarde chiffrée de '$DB_NAME' enregistrée : $BACKUP_DIR/$ENCRYPTED_FILENAME"
```

## 4. Bonnes pratiques

- Sauvegardes régulières et automatisées
- Conservation hors site
- Rotation des sauvegardes
- Tests de restauration périodiques
- Documentation des procédures
