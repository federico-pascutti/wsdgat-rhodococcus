# Búsqueda de aciltransferasas WS/DGAT en Rhodococcus jostii RHA1

Búsqueda de proteínas con el dominio Pfam PF03007 (wax ester synthase / acyl-CoA:diacylglycerol acyltransferase) en el proteoma de *R. jostii* RHA1 (NCBI GCF_000014565.1), usando HMMER.

## Cómo reproducirlo

```bash
conda env create -f environment.yml
conda activate bioinfo
curl -L -o PF03007.hmm.gz "https://www.ebi.ac.uk/interpro/wwwapi//entry/pfam/PF03007?annotation=hmm"
gunzip PF03007.hmm.gz
datasets download genome accession GCF_000014565.1 --include protein
unzip -o ncbi_dataset.zip
hmmsearch --tblout hits.tbl -E 1e-5 PF03007.hmm ncbi_dataset/data/GCF_000014565.1/protein.faa > hmmsearch.log
```

## Resultados

- 15 proteínas con E-value < 1e-5 (tabla en `wsdgat_hits.txt`).
- Con E-value < 1e-10 quedan [15].
- En mi tesis doctoral identifiqué 13 WS/DGAT en la cepa patagónica *R. jostii* 602; el número es comparable al de RHA1.
- El hit más débil: WP_272942770.1, (score 35,7) podría ser un fragmento de secuencia o tener el dominio incompleto; queda pendiente verificar el motivo catalítico HHxxxDG.”