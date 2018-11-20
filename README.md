# Installazione di Cygwin

Cygwin è un software che permette di usare alcuni programmi pensati per Unix o Linux su una macchina Windows.

Ecco i passi per installare Cygwin:

- Andare sulla pagina dove si può scaricare Cygwin: <https://cygwin.com/install.html>
- Ci sono due link, una per la versione a 32 bit e uno per la versione a 64 bit.
- Voi scaricate la versione a 32 bit (che funziona su tutti i Windows)
- Scarichiamo il file: <https://cygwin.com/setup-x86.exe> e lo lasciamo nella cartella Download
- Scarichiamo anche questo file [install.bat](https://raw.githubusercontent.com/andreafrancia/lezione-herman/master/install.bat) (facendo tasto destro > Salva con nome).
- L'importante è che alla fine siano nella stessa cartella.
- Doppio clicchiamo il file __install.bat__
- Windows sa che file __.bat__ scaricati dalla Rete potrebbero essere malevoli, quindi è possibile che lui o un antivirus provi a bloccarvi. Se Windows vi apre una finestra "Protetto da Windows" voi cliccate "Ulteriori informazioni" e poi fate "Esegui comunque"
- Dovrebbe partire l'installazione di Cygwin. In automatico dovrebbe installare anche tutti i pacchetti necessari.

# Controllare che l'installazione di Cygwin abbia funzionato

- A questo punto se ha installato corrrettametne Cygwin dovreste trovare tra i programmi uno nuovo che si chiama "Cygwin Terminal"
- Aprite "Cygwin Terminal"
- Dovrebbe apparirvi un ambiente a linea di comando. Questo ambiente si chiama Terminale e permette di interagire con un programma particolare chiamato Shell.
- La Shell funziona a comandi. Voi gli scrivete un comando, premete invio e lei da quello che gli avete detto di fare.
- Il primo comando da dare è questo:

  ```
  echo "hello world"
  ```
  
- se vi risponde "hello world" allora vuol dire che funziona
- altri comandi che vi possono interessare sono:

  ```bash
  mkdir test        # <-- crea una cartella
  cd test           # <-- entra in una cartella
  explorer .        # <-- apre explora risorse nella cartella corrente
  
  ```


# Installare Computer Programs in Seismology

 - andiamo sulla pagina principale: <http://www.eas.slu.edu/eqc/eqc_cps/getzip.html>
 - seguiamo "The main web page for this software package is" <http://www.eas.slu.edu/eqc/eqc_cps/CPS330.html>
 - seguiamo "Download UNIX/LINUX/MacOS-X or WIN32(CYGWIN) Sources" 
 - compiliamo e premiamo "Submit License Information" <http://www.eas.slu.edu/cgi-bin/send_cps_license.bin>
 - cliccare "Get the executables" <http://www.eas.slu.edu/eqc/eqc_cps/getzip.html>
 - Appena sotto a "Download using the wget command" troviamo la linea `wget http://www.eas.slu.edu/eqc/eqc_cps/Download/NP330.Jan-05-2018.tgz`
 - Apriamo un terminale di Cygwin e gli copiamo e incollliamo la linea seguente, il comando `wget` serve per scaricare un file da internet

   ```
   wget http://www.eas.slu.edu/eqc/eqc_cps/Download/NP330.Jan-05-2018.tgz
   ```

 - alla fine dovrebbe aver scaricato nella cartella corrente un file chiamato `NP330.Jan-05-2018.tgz`
 - scompattiamo il file con il comando `tar`:

   ```
   tar xvfz NP330.Jan-05-2018.tgz
   ```

 - dovrebbe aver creato la cartella `PROGRAMS.330` con dentri molti file
 - entriamo nella cartella

   ```
   cd PROGRAMS.330
   ```

 - proviamo a lanciare il ./Setup

	```
   	./Setup
   	```
   	
 - scegliamo CYGWIN40

   ```  
   ./Setup CYGWIN40
   ```
   
 - facciamo partire la compilazione con ./C

   ```
   ./C
   ```

# Cosa fare se non funziona ./C

Per capire cosa è andato storto bisogna farlo ripartire in questo modo:

```
bash -xe C
```

Dal risultato si dovrebbe capire qual'è il programma mancante che ha generato il problema.

# Comandi

```
sprep96 -NPTS 4096 -DT 0.1 -L -R -NMOD 100 -FACL 10 -FACR 10 -M model.vel
sdisp96 > sdisp96.out
sdpsrf96 -L -XMIN 0 -XMAX 4 -YMIN 1.0 -YMAX 7.0
sdpsrf96 -R -XMIN 0 -XMAX 4 -YMIN 1.0 -YMAX 7.0
plotnps < SDISPR.PLT > 005R.ps
plotnps < SDISPL.PLT > 005L.ps
ps2pdf 005R.ps
ps2pdf 005L.ps
```
