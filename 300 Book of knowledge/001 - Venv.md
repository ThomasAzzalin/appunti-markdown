## General Info
#VirtualEnvironment
#python
#bash
27.04.2025
## Venv
E' uno strumento di [[010 Python|python]] che serve a creare *[[006 - Ambienti Virtuali|ambienti virtuali]]*.
Ogni ambiente virtuale e' isolato dall'esterno, ha il suo *[[012 Interprete|interprete python]]* e le sue *librerie*.
Questo e' anche molto utile quando bisogna eseguire il progetto su una macchina differente, per avere sempre le corrette [[011 Dipendenze|Dipendenze]] con le giuste versioni installate.

## Utilizzo
*Per creare un ambiente virtuale*, bisogna aprire un [[007 - Terminale|terminale]] nella cartella dove si desidera creare, e poi scrivere:
``` bash
python -m venv nome_cartella
```
Una volta creato va *attivato*, per farlo bisogna spostarsi nella cartella appena creata e scrivere:
``` bash
nome_cartella\Scripts\activate
```
Una volta attivato quando si scarichera' una *libreria* con [[008 - Pip|pip]] essa verra' salvata solo dentro quell'ambiente.
Per *disabilitare* l'ambiente virtuale, si basta semplicemente eseguire questo comando:
``` bash
deactivate
```

## [[011 Dipendenze|Dipendenze]]
Utilizzando *venv* si possono scaricare in un file .txt tutte le [[011 Dipendenze|Dipendenze]] necessarie per quel progetto con il comando:
``` bash
pip freeze > requirement.txt
```
E' utile perche' creando un nuovo [[006 - Ambienti Virtuali|ambiente virtuale]], e' possibile utilizzare il file *requirement.txt* per scaricare tutte le [[??? Dipendenze|Dipendenze]] con un solo comando:
``` bash
pip install -r requirement.txt
```

