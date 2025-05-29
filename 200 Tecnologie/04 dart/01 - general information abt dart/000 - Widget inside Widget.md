## Concetto chiave
In *Dart* un concetto chiave e' che i *Widget* possono entrare all'interno di altri *Widget*.

### Esempio
```dart
return Scaffold(
      appBar: AppBar(
        title: Text("Testo titoloso"),
      ),
      body: Center(
        child: Text('Hello'),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ),
    );
```

In questo caso il widget principale e' **Scafford**, al cui interno troviamo 3 **parametri**, al cui interno inseriremo dei widget:
- *appBar*
- *body*
- *floatingActionButton*
