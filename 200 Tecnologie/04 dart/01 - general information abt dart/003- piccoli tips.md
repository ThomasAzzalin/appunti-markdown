# Debug banner
Se vuoi togliere il debug banner devi inserire questa riga di codice dentro il MaterialApp
```dart
debugShowCheckedModeBanner: false,
```
### Prima
![[Pasted image 20250215193215.png]]

### Dopo
![[Pasted image 20250215193300.png]]

## Codice completo
```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      ...
	  ),
	  ...
  }
}
```

# Dark / Light Mode
Per impostare la *dark mode* basta modificare una riga di codice:
```dart
colorScheme: ColorScheme.fromSeed(brightness: Brightness.dark),
```

### Prima
![[Pasted image 20250215195657.png]]

### Dopo
![[Pasted image 20250215195717.png]]

## Codice completo
```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(brightness: Brightness.dark, ...),
      ), 
      ...
    );
  }
}
```

# Format document
Tasto destro e premi su *Format Document*
![[Pasted image 20250215195928.png]]