# Estado da revisão R1 (JBCS) — congelado em 27/07/2026

Decisão editorial de **27/07/2026**: *"a revised version is required for further review"*.
Prazo de **45 dias**, vence por volta de **10/09/2026**. Dois pareceres: Revisor A
("Revisions Required") e Revisor C ("Resubmit for Review"), ambos construtivos, nenhum
pedindo coleta nova nem experimento de inferência adicional.

**O trabalho está parado aguardando uma única coisa: a 2ª codificação cega do Prof.
Marcelo.** Todo o resto que não depende dela está feito.

---

## 1. Bloqueado no Marcelo

Enviados por e-mail em 27/07: `codificacao_cega_v02.xlsx` e `GUIA_2a_CODIFICACAO.pdf`.

**Pendência conhecida:** o codebook v0.2 (`codebook_funcoes_mediacao.pdf`) **não** foi no
mesmo e-mail, e o guia o referencia como anexo. Ele nunca viu a v0.2 (a passada de junho foi
contra a v0.1; a v0.2 nasceu depois, ampliando FM02 e FM04). Precisa ir numa mensagem de
seguimento, senão ele codifica de memória pela v0.1 e o κ mede a coisa errada.

Também não foram enviados a nota de encaminhamento nem o pré-registro, então ele não sabe
que isso veio de revisor nem que há prazo.

Quando a planilha voltar:
1. Rodar `src/cohen_kappa.py` sobre as colunas FM01–FM08 e sobre a coluna MTL.
2. Seguir **à risca** as regras de relato de `data/segunda_codificacao_cega/PRE-REGISTRO_analise.md`,
   escritas e datadas antes da anotação. Elas são vinculantes, inclusive nos cenários ruins
   (κ < 0,41 na RQ2 tira os 51,3% do abstract).
3. Escrever a §7.4 e a §8 com os números, e só então a *response letter*.

## 2. Feito nesta rodada

**Isolamento E3 executado e persistido.** `src/counter_experiment_e3_curl.py`, 26 chamadas
via `curl` em subprocess (2 modelos × 13 cenários), temperatura 0.2. Divergência **26/26**,
`pontos_fortes` como lista em todos os casos. Dados em
`data/results/counter_experiment_e3_curl.json`.

**A contagem de 80 corrigida para 100** nas seis ocorrências, incluindo duas que o revisor
não viu: o *abstract* e a seção **Data Availability**. Detalhamento explícito no §3.8
(E1 26, E2 24, E2b 24, E3 26). A Tabela 4 deixou de trazer "failure reproduced" e traz
0/13 e 0/13 com Wilson e Fisher, homogênea com as demais linhas.

**Análise em nível de cenário** (pedido do Revisor A). `src/scenario_level_rq2.py` →
`analises/scenario_level_rq2.json`. Resultado que responde pelo avesso: ICC(1) = −0,11,
DEFF = 0,79, n efetivo 49,5; bootstrap de cluster (B = 20.000) devolve [38,5%; 64,1%],
mais estreito que o Wilson ingênuo. O agrupamento **não** infla a precisão dos 51,3%.
Mantivemos o Wilson mais largo como leitura de referência, de propósito. O ICC não positivo
é substantivo: é a forma quantitativa da instabilidade.

**Afirmações causais abrandadas.** O *abstract* não diz mais "inherited from instruction
tuning"; diz o que o protocolo de fato mostra (invariância a temperatura e à camada de
transporte). Parágrafo novo no §5.2 delimitando que o desenho é comportamental e caixa-preta
e não atribui o comportamento a nenhuma etapa do pipeline.

**Fronteira de generalização** amarrada no *abstract* e na conclusão ao regime avaliado
(zero-shot, CPU-only, Q4, sem coerção, as oito famílias do §3.3).

**Related work ampliado** com quatro referências, metadados conferidos na fonte:
Essay-BR (Marinho et al., JIDM 2022), Barbosa & Mauá (PROPOR 2026), TutorBench
(Srinivasa et al., 2025) e Chan et al. (Applied Sciences 2026). O contraste somativo vs.
formativo está escrito, não só citado. TutorBench dá o parâmetro que o Revisor C pediu
(fronteira não passa de 56%, subtarefa de feedback ~51%), com ressalva explícita de que
não é comparação direta.

**Ressalva da RQ2 promovida** no *abstract* a sentença própria, antes dos números.

**Tabela 9 reenquadrada:** "Gap" → "Difference (pp)", "Experts" → "Specialist corpus",
legenda declarando distribuição descritiva de referência, não nota-alvo.

**Densidade:** o trio 3%/15%/0% contra 80%/69%/57% caiu de quatro ocorrências para uma
(o *abstract*) mais a tabela.

**DOIs.** Diagnóstico do Revisor C estava errado: as oito entradas **já tinham** campo
`doi`. O estilo imprime DOI para `@article` e `@inproceedings` mas não para `@misc`, que é
o tipo dos preprints do arXiv. Acrescentado `note = {DOI: ...}` nas oito. Isso vira uma
resposta melhor do que "adicionamos os DOIs".

**Tabela 5** com colunas de largura fixa + `\footnotesize`.

**Roadmap da Introdução** agora menciona a Seção 8.

## 3. Não verificado, e precisa ser

**Compilar no Overleaf.** O `sbc2023.cls` e o `apalike-sol.bst` não estão no repositório, e
não há LaTeX completo na máquina, então nada disto foi compilado. Conferir na primeira
compilação:
- a Tabela 5 cabe na coluna;
- os DOIs aparecem nas oito entradas `@misc`;
- as quatro referências novas renderizam.

**Nova versão do Zenodo** com o `counter_experiment_e3_curl.json`. O DOI conceitual
(10.5281/zenodo.20388846) permanece; a Data Availability agora declara 100 registros de
falsificação, então o depósito precisa bater.

## 4. Observações soltas

- `paulelder2007socratic` está na bib sem ser citada em lugar nenhum. Inócua com bibtex,
  mas talvez fosse para estar citada.
- Colisão de rótulos: **E1–E5** designa tanto os isolamentos do contra-experimento (§3.8,
  §5.3) quanto as cinco professoras (§7.3, Tabela 8). Nenhum revisor pegou, mas agrava a
  densidade de leitura de que o Revisor C reclamou. Renomear as professoras para P1–P5
  é barato.
- A `chave_cega.csv` está no `.gitignore`, seguindo a política do commit e679470, que
  retirou a chave de κ da primeira rodada do repositório público.
