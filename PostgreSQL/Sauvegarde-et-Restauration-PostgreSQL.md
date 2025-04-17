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

## 4. Bonnes pratiques

- Sauvegardes régulières et automatisées
- Conservation hors site
- Rotation des sauvegardes
- Tests de restauration périodiques
- Documentation des procédures
