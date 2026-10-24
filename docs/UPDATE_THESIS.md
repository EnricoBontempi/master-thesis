# «Aggiorna la tesi»

1. Leggere AGENTS.md, THESIS_STATE, struttura effettiva di Thesis.tex e bibliografia.
   Eseguire `git status --short`, fetch e creare un branch dalla versione concordata,
   preservando lavoro locale e senza sovrascrivere main.
2. Acquisire thesis-research a un commit immutabile; leggere diario, stato scientifico,
   esperimenti, catalogo figure e registri delle presentazioni a quello stesso commit.
   Annotare in THESIS_STATE repo, commit, percorsi e data delle fonti ispezionate.
   Se manca accesso, chiedere un'esportazione versionata: non dichiarare di aver letto
   ciò che è solo riportato dall'utente.
3. Mappare evidenze e sezioni pertinenti. Distinguere ipotesi, materiale esplorativo,
   risultati verificati, superati o invalidati. Una review LLM, un commit, un meeting
   o un solver concluso non certificano validità fisica. Un risultato negativo
   pertinente può essere discusso con i suoi limiti e la sua evidenza.
4. Selezionare figure sulla base della domanda e delle evidenze. Copiarle in
   `Images/research/<ID>-<hash-breve>.png`, preservando gli asset Polimi. Registrare
   ID, stato scientifico, esperimento/configurazione, script/input se disponibili,
   commit sorgente, percorso e SHA-256 in THESIS_STATE. Non rinominare una figura
   senza aggiornare riferimenti e provenienza. Non sostituire materiale invalidato
   con affermazioni ancora basate su di esso.
5. Aggiornare testo, didascalie, label univoche, riferimenti incrociati e fonti reali.
   Le didascalie devono mantenere stato e limiti delle evidenze. Verificare ogni
   citazione su una fonte ispezionata; non inventare DOI, autori o misure. Se il
   significato scientifico è ambiguo, fermare quella modifica e chiedere chiarimento.
6. Da root eseguire:
   `latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=/tmp/thesis-build Thesis.tex`
   Controllare il log fresco per citazioni/riferimenti indefiniti, file mancanti,
   errori LaTeX e warning pertinenti. Verificare che il PDF sia del run corrente;
   ispezionare pagine, figure, didascalie e bibliografia. Non sostituire una compilazione
   reale con una semplice verifica di sintassi.
7. Aggiornare THESIS_STATE nello stesso commit: sezioni cambiate, fonti precise,
   limiti, materiale obsoleto e verifiche eseguite/non eseguite. Controllare il diff,
   fare commit/push del branch e aprire PR. Nessun merge automatico. Comunicare
   versione e limiti; attendere revisione umana finale.
8. Aggiornare Overleaf soltanto con Pull manuale dell'utente dalla versione scelta.
   Non automatizzare credenziali, sincronizzazione o deploy.

La demo sotto demos/ non deve essere inclusa nei capitoli né citata come ricerca.
