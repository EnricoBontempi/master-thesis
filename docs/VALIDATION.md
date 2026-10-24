# Verifiche Codex

- Template iniziale: b406d69850e02ce82a31f0694f41399459373b00.
- `demos/evidence-transfer/demo.tex`: compilato con `latexmk -pdf
  -interaction=nonstopmode -halt-on-error -outdir=/tmp/thesis-demo-build demo.tex`
  dalla directory della demo. PDF di una pagina con PNG illustrativo e riferimento
  incrociato risolto. Nessuna citazione o misura scientifica inventata.
- `Thesis.tex`: compilazione tentata dalla root con lo stesso comando e
  `-outdir=/tmp/thesis-real-build`. Interrotta perché `thmtools.sty` non è
  disponibile nell'ambiente Codex. Non è un errore dimostrato del server.
- Nessuna modifica a Thesis.tex, bibliografia, template o Images/.
- Prove reali scientifiche e controllo visivo finale della tesi: non eseguiti.

Per ripetere la demo:

```bash
cd demos/evidence-transfer
latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=/tmp/thesis-demo-build demo.tex
```

Per il template reale predisporre i pacchetti TeX richiesti (in particolare
thmtools, normalmente texlive-latex-extra, e gli algoritmi, normalmente
texlive-science), poi rieseguire senza cambiare il template per aggirare dipendenze
mancanti. Controllare il log del run corrente e il PDF prodotto. Il superamento
della demo non certifica la compilazione del template reale o la validità scientifica.

## Collaudo server, 2026-10-24

Le osservazioni Codex sopra restano quelle registrate allora. Questa sezione
descrive solo il collaudo successivo sul server. Non è un risultato scientifico.

Strumenti: pdfTeX 3.141592653-2.6-1.40.25 (TeX Live 2023/Debian), Latexmk 4.83.
`thmtools.sty` e `algorithmic.sty` sono presenti. `repstopdf` e `gs` no.

### Template Polimi

Dalla root, senza modificare `Thesis.tex`, la bibliografia, il template o
`Images/`:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error \
  -outdir=/home/enric/.local/state/thesis-latex-collaudo/real Thesis.tex
```

Esito: interrotto, nessun PDF. Il log del run riporta `sh: 1: repstopdf: not found`
e l'errore fatale di `pdftex.def` sul file
`Images/02_ING_IND_INFORMAZIONE_COL_POSITIVO-eps-converted-to.pdf`.
I quattro asset in `Images/` sono EPS e non sono stati convertiti né modificati.
Citazioni e riferimenti non sono stati raggiunti. Il controllo visivo del
template reale non è stato eseguito perché non esiste un PDF.

Manca il pacchetto che fornisce `repstopdf` e, come dipendenza raccomandata,
Ghostscript. Non è stato installato da questa sessione:

```bash
sudo apt-get install --no-install-recommends texlive-font-utils ghostscript
command -v repstopdf gs
```

### thesis-research

Commit remoto e locale `9aeafcbcfcf6f7b0078dac21aed8315db0597a83`. Diario,
stato scientifico, registro esperimenti, catalogo figure e registro
presentazioni non contengono attività, figure o una baseline. Nessun capitolo
è stato aggiornato e nessun risultato è stato importato.

### Demo isolata

`demos/evidence-transfer/demo.png` non è stato ricopiato. Il suo SHA-256
`4bd05c354edbfb8f4b10ec3493edc9fbfbe4be103bbfb6d1ca29085a45504332` coincide
con `demos/transport-demo-v1/figures/left.png` al commit
`51af452253b90441877f4cfeb240bd1ddd37eada`, stato `illustrative`.
L'origine storica resta `examples/pptx/figures/left.png` al commit
`eac671afb314254bf9bb88cfc78318cd35b7460f`. La demo non è inclusa in
`Thesis.tex`.

```bash
cd demos/evidence-transfer
latexmk -pdf -interaction=nonstopmode -halt-on-error \
  -outdir=/home/enric/.local/state/thesis-latex-collaudo/demo demo.tex
```

Esito del log finale: una pagina, nessun errore, nessun file mancante, nessun
riferimento o citazione indefiniti. `pdfinfo` riporta 1 pagina, 51024 byte.
`pdftotext` mostra il riferimento risolto «Figure 1» e la didascalia
«Illustrative transport fixture; not a scientific result.» La prima pagina è
stata renderizzata e ispezionata: compare il pannello illustrativo a tre barre,
non un risultato scientifico.

PDF e anteprima, fuori dal repository:

- `/home/enric/.local/state/thesis-latex-collaudo/demo/demo.pdf`
- `/home/enric/.local/state/thesis-latex-collaudo/demo/page-1.png`
