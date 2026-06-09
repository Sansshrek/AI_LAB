Questo è un progetto universitario per il corso di AI LAB per la laurea di Informatica a Sapienza

Il progetto confronta l'efficacia di due approcci di Deep Learning per la classificazione automatica dei rifiuti in 6 categorie (Cartone, Vetro, Metallo, Carta, Plastica, Rifiuti Generici)   
L'obiettivo è mostrare i vantaggi del **Transfer Learning** tramite ResNet18 rispetto a un'architettura semplice addestrata da zero, specialmente in casi di pochi dati per il training   
Il dataset originale è stato reperito da:   
 https://www.kaggle.com/datasets/asdasdasasdas/garbage-classification

I file principali del progetto sono:
* **TrashNet_Baseline.ipynb**: Notebook contenente l'AI di controllo dove viene addestrata e valutata una Rete Neurale Convuluzionale (CNN) costruita da zero
* **TrashNet_Transfer_Old.ipynb**: Versione iniziale dell'approccio di Transfer Learning, mantenuta per mostrare i progressi ottenuti tramite le ottimizzazioni
* **TrashNet_Transfer.ipynb**: Notebook principale del progetto. Implementa l'architettura ResNet18 pre-addestrata su immagini generiche, e ottimizzata con fine-tuning all'ultimo layer e Learning Rate Scheduler per migliorare le performance
* **ambiente_ai/** (o come chiami l'ambiente Python): cartella dell'ambiente virtuale di Python per contenere le librerie necessarie
* **dataset.zip**: archivio compresso contenente le immagini per l'addestramento e il test divise in cartelle per classe

I notebook Baseline e Transfer vengono ri-addestrati automaticamente se non trovano i pesi delle AI.   
I file dei pesi sono:
* **baseline_weights.pth**: i pesi della rete Baseline
* **resnet18_base.pth**: i pesi di default scaricati per ResNet18
* **transfer_resnet18_weights**: i pesi finali della ResNet18 ottimizzata

Se non si vuole addestrare da capo le AI si possono scaricare i pesi che ho addestrato in precedenza dal mio Drive mettendoli nella cartella principale:   
https://drive.google.com/drive/folders/1_as4_Z_SHgpu-c4XLS5aWRgHF7LtgkJu?usp=drive_link


## Come Avviare in VS Code
1) Estrai il file `dataset.zip` nella cartella principale.
2) Nel terminale dentro la cartella principale creare l'ambiente virtuale (scegliete un nome che volete)  
    `python -m venv ambiente_ai`
3) Attivare l'ambiente creato
    * Su Windows: `.\ambiente_ai\Scripts\activate`
    * Su Linux: `source ambiente_ai/bin/activate`
4) Con l'ambiente attivo, installare i pacchetti necessari:   
    `pip install torch torchvision opencv-contrib-python numpy pandas matplotlib seaborn scikit-learn tqdm grad-cam ipykernel`
5) Ora possiamo aprire `TrashNet_Baseline.ipynb` oppure `TrashNet_Transfer.ipynb` e, assicurandoci che il kernel selezionato in alto a destra sia `ambiente_ai` (o quello creato), possiamo runnare finalmente le celle

---
Il tree finale della cartella principale dovrà essere:

```
/
+---ambiente_ai
|
+---dataset
|   \---Garbage classification
|       +---cardboard
|       +---glass
|       +---metal
|       +---paper
|       +---plastic
|       \---trash   
+---Trashnet_Baseline.ipynb
+---Trashnet_Transfer_Old.ipynb
+---Trashnet_Transfer.ipynb
+---README.md
|
| (poi se scaricate dal Drive o se runnate le AI)
+---baseline_weights.pth
+---resnet18_base.pth
+---transfer_resnet18_weights.pth
```