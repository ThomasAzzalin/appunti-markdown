
## Errors
### SqliteError: FOREIGN KEY constraint failed
Quando capita sto errore di merda, e' perche' bisogna fare un delete a cascata di tutte le tabelle che fanno riferimento che stai provando ad eliminare dalla tabella padre.

Il codice per trovare ste tabelle e':
```sql
-- 1) Elenca tutte le tabelle che hanno un vincolo verso "skus"
SELECT name 
FROM sqlite_master 
WHERE type='table' 
  AND sql LIKE '%REFERENCES skus%';

-- 2) Per ognuna di quelle tabelle (diciamo "size_data" ma potrebbe essercene un’altra)
PRAGMA foreign_key_list('size_data');

-- 3) Controlla quali righe violano i vincoli
PRAGMA foreign_key_check;
```