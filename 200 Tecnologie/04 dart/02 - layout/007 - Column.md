E' utile per mostrare i suoi *widget* (children) in un'array verticale.
## Argomenti della classe Column
### Children
Serve per poter inserire piu' di un *Widget* dentro *Column*, accetta una *lista* di *widget* che deve essere lunga *almeno* 2.
```dart
Column(
	children: [
	  Container(
		width: 10.0,
		height: 100.0,
		decoration: BoxDecoration(
		  borderRadius: BorderRadius.circular(20),
		  color: Colors.red,
		),
	  ),
	  Container(
		width: 100.0,
		height: 100.0,
		decoration: BoxDecoration(
		  borderRadius: BorderRadius.circular(20),
		  color: Colors.red,
		),
	  )
	],
  ),
```
![[Pasted image 20250216123906.png]]