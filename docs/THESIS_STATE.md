# Stato autorevole della tesi

- Domanda e metodo scientifico: non definiti.
- Fonte iniziale ispezionata: master-thesis `b406d69850e02ce82a31f0694f41399459373b00`.
- Fonte scientifica ispezionata il 2026-10-24: `EnricoBontempi/thesis-research`, commit `9aeafcbcfcf6f7b0078dac21aed8315db0597a83`. Diario, stato, esperimenti, catalogo figure e registro presentazioni sono vuoti di risultati. Baseline assente. Nessun dato è stato importato.
- Template: `Configuration_Files/PoliMi3i_thesis.cls`; entry point `Thesis.tex`. Invariati in questo collaudo, insieme alla bibliografia.
- Immagini Polimi: `Images/`, quattro EPS preservati. Non convertiti.
- Capitoli scientifici aggiornati: nessuno.
- Fonti scientifiche importate: nessuna. Le fonti sono state ispezionate e non contengono risultati da trasferire.
- Figure scientifiche importate: nessuna.
- Validità scientifica: nessuna conclusione verificata da questo lavoro infrastrutturale.
- Demo: `demos/evidence-transfer/`, isolata, non inclusa in `Thesis.tex`. Trasferimento e compilazione sono soltanto dimostrativi. `demo.png` è stato riusato, non duplicato. SHA-256 `4bd05c354edbfb8f4b10ec3493edc9fbfbe4be103bbfb6d1ca29085a45504332`. Origine storica: `examples/pptx/figures/left.png` al commit `eac671afb314254bf9bb88cfc78318cd35b7460f`. Corrispondenza verificata, senza riscrivere quell'origine: `demos/transport-demo-v1/figures/left.png` al commit `51af452253b90441877f4cfeb240bd1ddd37eada`, stato illustrative.
- Compilazione template reale: fallita, nessun PDF. Manca `repstopdf` per gli EPS Polimi. Controllo visivo non eseguito.
- Compilazione demo: riuscita, una pagina, riferimento risolto. PDF fuori dal repository in `/home/enric/.local/state/thesis-latex-collaudo/demo/demo.pdf`.
- Dettaglio comandi ed esiti: `docs/VALIDATION.md`.
- Prossimo passo: installare `texlive-font-utils` e `ghostscript`, ricompilare `Thesis.tex` senza modificare il template. Definire la domanda prima di aggiornare i capitoli.
