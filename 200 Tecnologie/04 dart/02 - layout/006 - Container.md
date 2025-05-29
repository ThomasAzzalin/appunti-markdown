 Il *widget Container* e' come una *scatola vuota* che puoi riempire con tutto quello che vuoi.
## Argomenti della classe Container
### Child
Serve per poter inserire un *widget* dentro il *Container*.
```dart
Container(
	  child: Text("sono un testo in un container"),
	),
```

Ovviamente possiamo anche inserire un *container* all'interno di un'altro *container*, come in questo esempio
```dart
Container(
	  child: Container(
		  color: Color.black,
	  ),
	),
```

### height & width
Due argomenti importanti sono *Height* e *Width*, prendono come valori del valori *double*, e definiscono le dimensioni in pixel del container:
```dart
Container(
		height: 100.0,
		width: 100.0,
		child: Text("sono un testo in un container"),
	),
```

Se invece di un valore double si inserisce *double.infinity* allora il container occuper tutto lo spazio disponibile che ha il suo *padre*:
```dart
Container(
		height: double.infinity,
		width: double.infinity,
		child: Text("sono un testo in un container"),
	),
```

### Padding & Margin
Ulteriori due elementi utili quando si lavora con i *Container* sono il *padding* e il *margin*:
- *padding*: E' lo spazio che decidiamo tra il bordo del *container* e gli elementi che inseriamo all'interno
- *margin*: E' lo spazio fra il bordo e gli elementi *esterni* al *container*
#### Esempio
```dart
child: Container(
          height: double.infinity,
          width: double.infinity,
          margin: EdgeInsets.all(15),
          padding: EdgeInsets.all(20),
          decoration: BoxDecoration(
            color: Colors.blue,
            borderRadius: BorderRadius.circular(25),
          ),
          child: Container(
            height: double.infinity,
            width: double.infinity,
            decoration: BoxDecoration(
              color: Colors.red,
              borderRadius: BorderRadius.circular(25),
            ),
          ),
        ),
```
Risultato
![[Pasted image 20250216121913.png]]
La *parte bianca* intorno e' definita dal *margin*
```dart
margin: EdgeInsets.all(15),
```
la *parte blue* e' definita dal *padding*
```dart
padding: EdgeInsets.all(20),
```
La *parte rossa* e' un'altro *Container* che e' distanziato *20* dal bordo del container superiore grazie alla propieta' *padding*.
### decoration
Un'altro argomento fondamentale dei *container* e' *decoration*, esso prende come valore un'oggetto **BoxDecoration()**, che a sua volta ha altri parametri come:
- color:
- borderRadius
```dart
Container(
		decoration: BoxDecoration(  
            color: Colors.blue,
            borderRadius: BorderRadius.circular(25)
          ),
		child: Text("sono un testo in un container"),
	),
```
## Esempio di container con vari argomenti
```dart
Container(
	  height: 100.0,
	  width: 100.0,
	  decoration: BoxDecoration(  
		color: Colors.blue,
		borderRadius: BorderRadius.circular(25)
	  ),
	  child: Text("sono un testo in un container"),
	),
```

![[Pasted image 20250215220354.png]]