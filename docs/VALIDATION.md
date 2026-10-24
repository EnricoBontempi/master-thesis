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
