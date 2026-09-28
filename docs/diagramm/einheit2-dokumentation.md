# Einheit 2 – Datenmodell der Bewertungsapp

## Tabellenstruktur

### Team

| Spalte | Datentyp | Key |
|---|---|---|
| id | INTEGER | PK |
| name | STRING | NULL |
| klasse | STRING | NULL |

### Member

| Spalte | Datentyp | Key |
|---|---|---|
| id | INTEGER | PK |
| teamId | INTEGER | FK → Team.id |
| vorname | STRING | NULL |
| nachname | STRING | NULL |

### Project

| Spalte | Datentyp | Key |
|---|---|---|
| id | INTEGER | PK |
| teamId | INTEGER | FK → Team.id |
| titel | STRING | NULL |
| beschreibung | TEXT | NULL |
| praesentiertAm | DATE | NULL |

### Criterion

| Spalte | Datentyp | Key |
|---|---|---|
| id | INTEGER | PK |
| name | STRING | NULL |
| maxScore | INTEGER | NULL |
| weight | DECIMAL | NULL |

### Juror

| Spalte | Datentyp | Key |
|---|---|---|
| id | INTEGER | PK |
| name | STRING | NULL |
| email | STRING | NULL |

### Evaluation

| Spalte | Datentyp | Key |
|---|---|---|
| id | INTEGER | PK |
| projectId | INTEGER | FK → Project.id |
| criterionId | INTEGER | FK → Criterion.id |
| jurorId | INTEGER | FK → Juror.id |
| score | INTEGER | NULL |
| comment | TEXT | NULL |

Unique-Constraint: (projectId, criterionId, jurorId)

## Verwendete model:generate-Befehle

### Team

```bash
npx sequelize-cli model:generate --name Team --attributes name:string,klasse:string
```
### Member

```bash
npx sequelize-cli model:generate --name Member --attributes teamId:integer,vorname:string,nachname:string
```

### Project

```bash
npx sequelize-cli model:generate --name Project --attributes teamId:integer,titel:string,beschreibung:text,praesentiertAm:date
```

### Criterion

```bash
npx sequelize-cli model:generate --name Criterion --attributes name:string,maxScore:integer,weight:decimal
```

### Juror

```bash
npx sequelize-cli model:generate --name Juror --attributes name:string,email:string
```

### Evaluation

```bash
npx sequelize-cli model:generate --name Evaluation --attributes projectId:integer,criterionId:integer,jurorId:integer,score:integer,comment:text
```

## Screenshots der Datenbank

![Übersicht der Tabellen](docs/screenshots/tables.png)
![Übersicht der Evaluation Tabelle](docs/screenshots/evaluation_table.png)