# Neo4j-Cypher

## Inhaltsverzeichnis

- [1. MATCH](#1-match)
- [2. WHERE](#2-where)
- [3. RETURN](#3-return)
- [4. ALIAS](#4-alias)
- [5. MERGE](#5-merge)
  - [5.1 ON CREATE](#51-on-create)
  - [5.2 ON MATCH](#52-on-match)
- [6. UPDATE](#6-update)
- [7. DELETE](#7-delete)



## 1. MATCH
Verwende die `MATCH`-Klausel, um Muster in der Datenbank zu finden, z.B. alle Personen.

```cypher
MATCH (person:Person)
```

## 2. WHERE
Verwende die `WHERE`-Klausel, um Bedingungen für die gefundenen Muster anzugeben, z.B. Personen mit einem bestimmten Namen.

```cypher
MATCH (person:Person)
WHERE person.name = 'John Doe'
```

## 3. RETURN
Verwende die `RETURN`-Klausel, um die gewünschten Daten aus der Abfrage zurückzugeben, z.B. den Namen der gefundenen Personen.

```cypher
MATCH (person:Person)
RETURN person.name
```

## 4. ALIAS
Verwende `AS`, um Aliasse für Werte oder Muster zu erstellen, z.B. den Namen als Alias.

```cypher
MATCH (person:Person)
RETURN person.name AS personName
```

## 5. MERGE
Verwende die `MERGE`-Klausel, um Personen zu erstellen oder zu aktualisieren, falls sie nicht existieren, basierend auf einem eindeutigen Merkmal wie der E-Mail-Adresse.

```cypher
MERGE (person:Person {email: 'john.doe@example.com'})
```

### 5.1 ON CREATE
Die `ON CREATE`-Klausel wird in Verbindung mit `MERGE` verwendet und definiert Aktionen, die nur beim Erstellen eines Musters ausgeführt werden, z.B. das Setzen des Erstellungsdatums.

```cypher
MERGE (person:Person {email: 'john.doe@example.com'})
ON CREATE SET person.created_at = timestamp()
```

### 5.2 ON MATCH
Die `ON MATCH`-Klausel wird in Verbindung mit `MERGE` verwendet und definiert Aktionen, die nur bei Aktualisierung eines vorhandenen Musters ausgeführt werden, z.B. das Setzen des Aktualisierungsdatums.

```cypher
MERGE (person:Person {email: 'john.doe@example.com'})
ON MATCH SET person.updated_at = timestamp()
```

## 6. UPDATE
Um Daten in einem vorhandenen Muster zu aktualisieren, verwende die `SET`-Klausel, z.B. den Namen einer Person ändern.

```cypher
MATCH (person:Person {email: 'john.doe@example.com'})
SET person.name = 'New Name'
```

## 7. DELETE
Um Muster oder Beziehungen zu löschen, verwende die `DELETE`-Klausel, z.B. eine Person basierend auf der E-Mail-Adresse löschen.

```cypher
MATCH (person:Person {email: 'john.doe@example.com'})
DELETE person
```
