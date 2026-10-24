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

### Template Polimi, secondo tentativo

Dopo l'installazione di `texlive-font-utils` e `ghostscript`, ripetuta soltanto
la compilazione reale. Strumenti aggiunti: `repstopdf` (epstopdf 2.33) e
Ghostscript 10.02.1. pdfTeX e Latexmk restano quelli del tentativo precedente.
Non è stato passato `-shell-escape`: il log riporta `restricted \write18 enabled`.
Directory nuova, distinta dal tentativo senza PDF:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error \
  -outdir=/home/enric/.local/state/thesis-latex-collaudo/real-20261024T0528 \
  Thesis.tex
```

Esito: PDF prodotto, 32 pagine, 496084 byte, A4, creato il 2026-10-24 01:29 EDT.
`latexmk` conclude che il bersaglio è aggiornato. Il log finale non contiene
errori LaTeX, file mancanti, citazioni indefinite o riferimenti indefiniti.
BibTeX con `abbrvnat.bst` riporta zero warning.

Warning già presenti nel template, non corretti:

- `pdfTeX warning (ext4): destination with the same identifier` per `page.i` e
  `page.ii`, alle due aperture di capitolo con numerazione romana.
- `Underfull \hbox (badness 10000)` nei paragrafi degli abstract, `Thesis.tex`
  righe 140–157 e 160–164.

Controllo visivo di tre pagine del PDF corrente:

- pagina 1, frontespizio: marchio Politecnico di Milano, titolo segnaposto
  «Title», corso ancora «Xxxxxxx Engineering», autore Enrico Bontempi,
  Student ID 10838032, advisor Prof. Gianluca D'Errico, anno 2026-2027;
- pagina 13, capitolo 1 pagina 5: Figure 1.1 e Figure 1.2 con i loghi EPS,
  riferimenti Figure 1.1, 1.2a e 1.2b risolti, Table 1.1 presente;
- pagina 19, bibliografia pagina 11: sei voci numerate, da [1] a [6].

Il PDF contiene pagine vuote fra i frontespizi di capitolo. Sono interruzioni
già previste dal template, non file mancanti di questo run. Titolo e corso
restano i segnaposto del template: nessun capitolo scientifico è stato scritto.

`repstopdf`, con shell escape ristretto, ha scritto quattro PDF
`*-eps-converted-to.pdf` accanto agli EPS in `Images/`, non nella directory di
build. Gli EPS originali non sono stati modificati. I quattro PDF generati
sono stati spostati in
`/home/enric/.local/state/thesis-latex-collaudo/real-20261024T0528/eps-converted/`
e non sono nel commit. Una compilazione successiva li ricreerà in `Images/`
finché il template non reindirizza l'output; il template non è stato cambiato
per questo.

PDF e anteprime, fuori dal repository:

- `/home/enric/.local/state/thesis-latex-collaudo/real-20261024T0528/Thesis.pdf`
- `/home/enric/.local/state/thesis-latex-collaudo/real-20261024T0528/front-01.png`
- `/home/enric/.local/state/thesis-latex-collaudo/real-20261024T0528/figure-13.png`
- `/home/enric/.local/state/thesis-latex-collaudo/real-20261024T0528/biblio-19.png`
