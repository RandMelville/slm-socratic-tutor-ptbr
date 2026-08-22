# Estado da revisão R1 (JBCS) — atualizado em 22/08/2026

> **➡️ O estado atual está na §10 (22/08): protocolo v0.4 congelado, guia do professor e planilhas
> prontos. O aval está dado (parecer do Marcelo em 10/08, aceite da Rosa em 11/08). Falta só o
> e-mail dos dois codificadores para compartilhar as planilhas e enviar os convites.** A §8 explica
> o que caiu e a §9 registra o parecer que mudou o plano. Leia as três, nessa ordem, se estiver
> retomando.

> **⚠️ LEIA A §8 ANTES DE QUALQUER COISA.** Em 30/07 o Marcelo apontou que as duas
> codificações comparadas no κ das FMs foram produzidas sob protocolos diferentes, o que
> invalida aquele κ como estimativa de confiabilidade. A investigação de 04–05/08 confirmou
> a objeção e encontrou um problema maior: **a 1ª codificação das 39 devolutivas do modelo
> foi produzida por assistente de IA, não por leitura humana.** O κ = 0,14 e a §7.6 do
> artigo, tais como estão, não se sustentam. Protocolo v0.3 escrito e enviado aos autores.
> **Tudo abaixo desta linha, até a §8, é o estado congelado de 30/07 e está superado no que
> toca à codificação do lado do modelo.**

## Histórico da própria revisão (30/07/2026)

> A 2ª codificação cega voltou do Marcelo, a análise pré-registrada
> foi executada e o artigo foi editado conforme as regras congeladas. O κ das FMs deu
> **0,14** e disparou a linha 3 do pré-registro (rebaixamento da Tabela 9); o κ da RQ2 deu
> **0,54** e disparou a linha 2 (régua mantida como sonda, limitação quantificada).
> Detalhe em §5 deste documento. Rascunho da resposta em `RESPOSTA_REVISORES_R1.md`.

## Histórico (congelado em 27/07/2026)

Decisão editorial de **27/07/2026**: *"a revised version is required for further review"*.
Prazo de **45 dias**, vence por volta de **10/09/2026**. Dois pareceres: Revisor A
("Revisions Required") e Revisor C ("Resubmit for Review"), ambos construtivos, nenhum
pedindo coleta nova nem experimento de inferência adicional.

**O trabalho está parado aguardando uma única coisa: a 2ª codificação cega do Prof.
Marcelo.** Todo o resto que não depende dela está feito.

---

## 1. Bloqueado no Marcelo

Enviados por e-mail em 27/07: `codificacao_cega_v02.xlsx` e `GUIA_2a_CODIFICACAO.pdf`.

**Pendência conhecida (27/07):** o codebook v0.2 (`codebook_funcoes_mediacao.pdf`) **não**
foi no mesmo e-mail, e o guia o referencia como anexo. Ele nunca viu a v0.2 (a passada de
junho foi contra a v0.1; a v0.2 nasceu depois, ampliando FM02 e FM04). Precisa ir numa
mensagem de seguimento, senão ele codifica de memória pela v0.1 e o κ mede a coisa errada.

Também não foram enviados a nota de encaminhamento nem o pré-registro, então ele não sabe
que isso veio de revisor nem que há prazo.

### Atualização de 29/07: codebook próprio da rodada da Qwen

Ele leu o guia, entendeu a tarefa e travou no codebook: o v0.2 é o documento de junho,
enquadrado no corpus dos cinco professores (E1–E5, o flag de E4/C10, "próximos passos" que
já executamos). Pediu um instrumento coerente com esta rodada antes de começar a codificar.

Entregue: **`data/segunda_codificacao_cega/codebook_respostas_modelo.{md,pdf}` (v0.2-Q)**.
Objeto identificado (as 39 saídas da Qwen), unidade de análise (a devolutiva integral do
modelo), referências da rodada humana removidas, MTL formalizada com a sigla expandida
(contração de *MeTaLinguístico*; nome por extenso "foco metalinguístico no texto do aluno"),
fronteiras MTL × FM02/FM03/FM04 com tabelas 2×2 de exemplos inventados, e o corpus
registrado como 13 cenários × 3 repetições.

Duas escolhas deliberadas, ambas justificadas no documento e na resposta a ele:
- **As oito definições estão intocadas** (só pontuação). O κ desta rodada é sobre a v0.2 e é
  a comparação com o vetor de junho que mostra que a ampliação de FM02/FM04 funcionou. Por
  isso a versão é 0.2-Q, não 0.3.
- **As âncoras seguem vindo do corpus humano**, sem os códigos E#/C# e com nota de que não
  fazem parte do material a codificar. Foram elas que calibraram as definições na leitura
  dele; trocá-las descalibraria o instrumento no meio da série.

Acompanham: `RESPOSTA_marcelo_codebook.{md,pdf}` (rascunho da mensagem, item a item) e uma
§6 de adendo no `PRE-REGISTRO_analise.md`, datada de 29/07, registrando a substituição de
instrumento e que a explicitação das fronteiras é anterior a qualquer anotação.

O `GUIA_2a_CODIFICACAO` **não** foi editado (está declarado congelado e já está com ele);
ainda cita o codebook antigo na linha "Material", e a §0 do codebook novo registra que o
substitui.

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

---

## 5. Execução da 2ª codificação (30/07/2026)

Planilhas recebidas: `codificacao_cega_QWEN_marcelo_consolidada.xlsx` e
`..._por_cenario.xlsx`. A segunda é superset estrito (abas "Codificação" e "Notas
metodológicas" idênticas byte a byte); usar só ela como fonte.

Análise: `analises/kappa_2a_codificacao.py` → `analises/kappa_2a_codificacao_resultados.txt`.

### Resultado (A) — confiabilidade das FMs

κ médio **0,138** sobre as 6 categorias definidas (FM05 e FM08 são 0/39 nos dois
codificadores, κ indefinido). Bruta média 76,1% (6 cat.) / 82,1% (8 cat.).

| FM | κ | bruta | anot.1 | anot.2 | PABAK |
|---|---|---|---|---|---|
| FM01 | 0,000 † | 92,3% | 39/39 | 36/39 | 0,85 |
| FM02 | 0,374 | 92,3% | 1/39 | 4/39 | 0,85 |
| FM03 | 0,082 ‡ | 51,3% | 4/39 | 21/39 | 0,03 |
| FM04 | 0,226 | 74,4% | 6/39 | 10/39 | 0,49 |
| FM05 | n/d | 100% | 0/39 | 0/39 | 1,00 |
| FM06 | 0,000 † | 94,9% | 0/39 | 2/39 | 0,90 |
| FM07 | 0,147 ‡ | 51,3% | 16/39 | 35/39 | 0,03 |
| FM08 | n/d | 100% | 0/39 | 0/39 | 1,00 |

† zero degenerado (anotador 1 constante). ‡ confundido com deriva de instrumento (FM03).

**Linha 3 do pré-registro disparou**, por dois caminhos: κ médio < 0,41 **e** FM02 (0,374) e
FM04 (0,226) abaixo de 0,40 por si sós. O zero da FM06 é degenerado e não conta; a regra
dispara sem ele.

Três leituras que sustentam o texto novo:
- **Direcionalidade:** 49/56 (87,5%) das divergências são o anotador 2 creditando função a
  mais. Replica o offset de 100% da 1ª rodada. Médias: 1,69 vs. 2,77 FMs por devolutiva.
  Como o argumento é sobre função **ausente**, o codificador mais generoso é o caso
  adversarial, e o padrão sobrevive a ele.
- **Deriva de instrumento:** FM03+FM07 concentram 38/56 divergências. A nota metodológica 5
  do Marcelo registra critério de FM03 mais inclusivo, que o anotador 1 não aplicou. **Não
  recalcular** com definição harmonizada: o pré-registro veda.
- **Conclusão sobrevive:** núcleo corretivo sob anot.2 é 10%/26%/5% contra 80%/69%/57% dos
  especialistas. FM05 e FM08 são 0/39 nos dois. É padrão replicado, não medida.

### Resultado (B) — validade de construto da RQ2

κ = **0,538**, bruta 76,9%. **Linha 2 do pré-registro.** Régua 51,3% (20/39) vs. juízo
especialista 53,8% (21/39); 9 divergências quase simétricas (4 sobre-crédito da régua, 5
falsos negativos). Os 51,3% ficam, agora sempre acompanhados do κ.

### Bônus não planejado

O agrupamento por cenário que o Marcelo fez às cegas acertou **13/13**. Reconstruiu a matriz
inteira só pelo texto do aluno. Entrou na §7.6 sem alegação estatística.

## 6. Edições aplicadas ao `main.tex` (30/07)

1. **Abstract:** trio 3%/15%/0% × 80%/69%/57% removido, virou padrão; κ=0,54 e 53,8%
   acrescentados ao lado dos 51,3%; κ=0,14 declarado.
2. **§6:** parágrafo novo "Construct validity of the lexical screen" com a análise (B).
3. **§7.4:** anotador descrito como coautor, não "independente"; frase final sobre "open
   item" substituída por ponteiro à §7.6.
4. **§7.5:** ressalva de codificador único reescrita; Tabela 9 declarada ilustração
   qualitativa; parágrafo de leitura reescrito para só afirmar o que sobrevive às duas
   codificações.
5. **Tabela 9:** coluna "Difference (pp)" removida, coluna "Coder 2 (blind)" acrescentada,
   legenda em negrito declarando que não é medida.
6. **§7.6 nova** (`sec:fm-blind`): tabela de κ/PABAK + 4 qualificações + achado 13/13.
7. **§8 Threats:** de cinco para seis limitações; item da RQ2 reescrito com κ=0,54; item novo
   sobre confiabilidade da codificação do modelo; limitações do pré-registro §5 (juiz único,
   anotador coautor, independência parcial) e a nota 11 do Marcelo (binário ≠ qualidade).
8. **§9 Conclusão:** percentuais fora, padrão dentro, κ das duas análises declarados.
9. **CRediT:** contribuição de codificação cega do Marcelo registrada.
10. **Materials:** pacote de confiabilidade + plano de análise datado declarados como
    material aberto.
11. **`references.bib`:** `byrt1993bias` (PABAK) e `feinstein1990high` (paradoxo do κ).
12. **Abstract cortado de 661 → 401 palavras** (a versão submetida tinha 551). Decisão do
    Randerson em 30/07 depois de ver que ocupava a página 1 inteira. Preservados: ressalva
    da RQ2 como sentença própria antes dos números, 51,3% + κ=0,54 + 53,8%, κ=0,83, κ=0,14,
    312+100 chamadas, reversibilidade one-shot, fronteira do regime. Comprimidos: o núcleo
    corretivo soletrado por extenso e a frase "used descriptively rather than as a
    performance yardstick". Responde de passagem à queixa de densidade do Revisor C.
13. **Tabelas 9 e 10 para `table*`.** A 1ª compilação no Overleaf mostrou as duas
    transbordando a coluna (a 9 derramava "Specialist corpus" por cima do texto; a 10 cortava
    "Coder 2" e PABAK na margem). Passaram a `\begin{table*}[!t]`, mesmo padrão das outras
    cinco tabelas largas. A nota de rodapé da Tabela 10 (símbolos † e ‡) foi **para dentro**
    do float, numa `minipage{\textwidth}`, senão flutuaria para longe da tabela que explica;
    por isso o "discussed below" virou "discussed among the qualifications in Subsection 7.6".
14. **Conversores atualizados** (`tex_to_docx.py`, `tex_to_pdf.py`): CITE + REFERENCES com as
    duas entradas novas, mapa REF com `sec:fm-blind`=7.6, `sec:fm-role`=7.7 e
    `tab:fm-kappa-model`=10, e `split_row()` novo expandindo `\multicolumn` para N células.
    Esse último consertou também as linhas de média das Tabelas 6 e 8, que vinham
    deslocadas uma célula desde sempre. Só afeta os artefatos de leitura, não o Overleaf.

## 7. Situação ao encerrar a sessão de 30/07/2026

**Compilação no Overleaf: OK.** Segunda compilação, depois do fix de `table*`, saiu limpa
(23 páginas). O PDF foi salvo na raiz do repo como
`SLMs_for_Offline_Writing_Feedback_Tutoring_in_Brazilian_Portuguese.pdf` e **enviado ao
Marcelo em 30/07**. Os artefatos de leitura `paper/jbcs/benchmark_slm_jbcs.{pdf,docx}` foram
regerados a partir do mesmo `main.tex` final, caso ele peça o Word.

**O `main.tex` está fechado para esta rodada.** Fonte de verdade, como sempre.

### O que falta

1. **Pareceres completos, bloqueante para enviar.** `RESPOSTA_REVISORES_R1.md` cobre a fundo
   os quatro itens desta rodada (2ª codificação, validade da RQ2, estatuto do anotador,
   achado 13/13). O resto está listado no fim do arquivo mas precisa ser pareado com o texto
   verbatim dos revisores, que **não está no repositório**. Colar os dois relatórios num
   arquivo aqui é o primeiro passo da próxima sessão.
2. **Zenodo.** A seção Materials agora declara publicamente o pacote da 2ª codificação e o
   pré-registro datado. O depósito precisa passar a incluí-los, senão a declaração fica falsa.
   O DOI conceitual (10.5281/zenodo.20388846) permanece.
3. **Planilhas do Marcelo soltas na raiz.** `codificacao_cega_QWEN_marcelo_consolidada.xlsx`
   e `..._por_cenario.xlsx`. A segunda é superset estrito da primeira. Mover para
   `data/segunda_codificacao_cega/` e decidir se as observações qualitativas dele vão
   públicas (o artigo já cita as notas metodológicas dele na §8).
4. **Prazo:** vence por volta de **10/09/2026**.

### Não urgente, mas anotado

- Colisão de rótulos E1–E5 (isolamentos do contra-experimento × as cinco professoras)
  continua. Renomear as professoras para P1–P5 é barato e ataca a densidade que o Revisor C
  criticou.
- `paulelder2007socratic` segue na bib sem ser citada.
- As notas metodológicas 1 (definição emergente de qualidade) e 13 (presença formal de FM não
  autoriza entrega direta ao aluno) do Marcelo **não** entraram nesta revisão, para não abrir
  escopo. São material do paper de 2027. A nota 11 (binário ≠ qualidade) entrou na §8.

---

## 8. Ruptura do protocolo de codificação (04–05/08/2026)

### 8.1 O que o Marcelo apontou

Em quatro mensagens entre 29 e 30/07, mais a planilha consolidada:

1. **Vazamento de ancoragem.** O codebook v0.2-Q informava ao 2º codificador a média de FMs
   da 1ª passada (1,7 contra 3,8 das humanas). Nota metodológica 8 dele.
2. **A nota da FM03 induz viés.** A exclusão de perguntas sobre enredo/personagem/tema não é
   sempre verdadeira: pergunta sobre a obra pode levar a reexaminar escolha do próprio texto.
   Redação substituta na nota metodológica 5.
3. **Presença de FM não é qualidade** (notas 2, 7, 11), e a devolutiva integral como unidade
   não corresponde ao corpus: evidências aparecem em segmentos (nota 6).
4. **Bloqueante:** "as duas codificações que seriam comparadas foram produzidas com
   protocolos diferentes. Nessas condições, não se pode calcular concordância entre elas."

### 8.2 O que a investigação de 04–05/08 verificou

Tudo abaixo foi conferido nos arquivos, não inferido.

- **Os números do artigo estão corretos.** κ recomputado do zero a partir da planilha do
  Marcelo cruzada com `chave_cega.csv`: idêntico em todas as células (κ médio 0,1383,
  bruta 82,1%, 49/7 divergências, 1,69 vs 2,77, RQ2 κ=0,5375, 20/39 vs 21/39). O achado
  13/13 confere contra a chave: 13 trios puros, 39 IDs únicos.
- **O defeito de instrumento é estreito.** Diff campo a campo v0.2 × v0.2-Q: as oito
  definições são substantivamente idênticas (única troca de palavra na FM05). O ÚNICO
  acréscimo substantivo é a "Nota específica deste corpus" da FM03 (0 ocorrências na v0.2).
  A "Fronteira com FM03" da FM04 já existia na v0.2. O vazamento está na linha 44 do
  codebook e também foi enviado em mensagem.
- **A contaminação toda empurra para concordância.** O vazamento apontava para menos funções
  e ele marcou mais; a nota da FM03 mandava não marcar e ele marcou 21/39. **κ=0,14 é limite
  superior.** É o que a nota 8 dele já dizia ("inflar a concordância").
- **O defeito não explica o resultado.** κ sem FM03 = 0,149 contra 0,138 com. A FM07, de
  definição idêntica nos dois instrumentos, tem as mesmas 19 divergências da FM03.
- **A 1ª codificação das 39 foi produzida por assistente de IA.** Registrado no docstring de
  `analises/fm_coding_model.py` ("anotador 1, Claude"); commit `ce2ca08` com Co-Authored-By.
  Contraste: `fm_coding.py` (65 humanas) não tem essa marca, commit `20d2e05` não tem
  Co-Authored-By, e o gabarito removido tinha coluna `minhas_FMs`. **Confirmado pelo
  Randerson em 04/08.** Logo o κ=0,14 nunca foi concordância entre anotadores.
- **`main.tex` linha 602 está factualmente errada:** diz "coded independently under codebook
  v0.2"; o 2º codificador usou v0.2-Q.
- **A §7.6 usa as notas 5 e 11 do Marcelo e ignora as notas 8, 9 e 10**, que são as que
  atingem a validade do κ. Elas estavam na planilha desde 30/07.

### 8.3 Data Availability declara três coisas falsas

| Declarado na §Materials | Situação real |
|---|---|
| codebook v0.2-Q, pacote de anotação, plano de análise | versionados ✔ |
| codificação completa das 39 com justificativas e notas | **não versionada** (xlsx soltas na raiz) |
| script de análise que produz a Tabela 10 | **não versionado** (`analises/kappa_2a_codificacao.py`) |
| arquivo permanente no Zenodo | **só a v1.5.0 de 29/06**, um zip de 1,9 MB; não tem o pré-registro (27/07), o codebook v0.2-Q (29/07), a codificação (30/07) nem o `counter_experiment_e3_curl.json` (27/07) que sustenta as "100 falsification calls" |

### 8.4 A sequência acordada com o Marcelo

Ele passou o passo a passo e o Randerson concordou:

1. Revisar o protocolo com base nas notas metodológicas. ✔ **feito** (`data/segunda_codificacao_cega/PROTOCOLO_REVISADO_v03.{md,pdf}`)
2. Enviar o protocolo revisado para concordância explícita dos três autores. ← **estado atual, aguardando**
3. Entregar a um novo codificador, sem acesso às codificações anteriores.
4. Comparar com a codificação do Marcelo, ambas sob o mesmo protocolo.
5. Recalcular a concordância e consolidar por cenário (3 execuções × 13 cenários).
6. Reescrever método, resultados e discussão narrando com transparência o que motivou a recodificação.
7. Atualizar a resposta ponto a ponto aos avaliadores.

Os dois revisores pediram o κ das FMs com todas as letras (Revisor C: *"carrying out this
second coding pass and reporting the corresponding κ"*; Revisor A: *"further reliability
validation, particularly for the mediation functions"*), então abrir mão do κ não era opção.

### 8.5 O que o protocolo v0.3 muda

FM03 com a redação da nota 5 (cai a exclusão das perguntas sobre a obra); unidade com
evidência segmentada (nota 6); nenhum agregado de passada anterior nem regra derivada do
corpus (nota 8); momento do confronto fixado (nota 9); preservação com errata (nota 10);
binário ≠ qualidade como limitação declarada (nota 11); consolidação por cenário no plano
de análise. Seção 1.2 do protocolo registra a procedência da codificação por IA. Seção 7
declara a assimetria residual: a passada do Marcelo carregou a ancoragem de densidade, a
nova não.

### 8.6 O que NÃO é atingido

- **A escolha do modelo do piloto.** Vem de conformidade estrutural, latência e Fisher sobre
  412 chamadas, tudo verificado por programa. ADR-0001 e ADR-0019 da plataforma seguem válidas.
- **κ = 0,83 do corpus humano** (par: Randerson × Marcelo, junho, devolutivas de professores,
  codebook v0.1). Outro corpus, outro instrumento.
- **κ = 0,54 da RQ2.** Ali a comparação é entre régua executada por programa e o juízo MTL,
  não entre dois codificadores. Ressalva a acrescentar: a nota da §5.2 do v0.2-Q pode tê-lo
  inflado, então é limite superior também.
- **O achado 13/13** dos cenários, verificado.

### 8.7 Pendências

1. **Aguardando** aprovação do protocolo v0.3 pelos três autores.
2. Depois: pacote cego novo, recrutar o codificador externo, recodificar, recalcular.
3. Reescrever §7.4, §7.5, §7.6, §8, abstract, conclusão e Data Availability.
4. Versionar `analises/kappa_2a_codificacao.py`. **Decisão pendente do Randerson:** as duas
   `.xlsx` do Marcelo vão para o repositório público com as observações qualitativas dele?
5. Nova versão do Zenodo com tudo da R1.
6. **Prazo: ~10/09/2026.**

---

## 9. Parecer do Marcelo sobre o v0.3 (10/08/2026)

`Observacoes_Protocolo_Revisado_v03.docx`, na raiz do repositório. Ele aprova o que o v0.3
incorporou (FM03 revista, evidência segmentada, retirada da ancoragem, separação FM×MTL,
preservação dos registros, consolidação por cenário) e levanta cinco pontos que **mudam o
plano acordado em 05/08**.

### 9.1 Regra de validade mínima das FMs (o ponto principal)

> Uma ocorrência somente deve ser codificada como 1 quando, além de apresentar as
> características formais da função, for semanticamente compatível com sua finalidade
> mediadora. Movimentos que se apresentem formalmente como uma FM, mas induzam o aluno ao
> erro, reforcem uma inadequação ou proponham alteração que possa piorar a produção devem ser
> considerados falsos positivos e codificados como 0.

Operacionalizada função a função, FM01 a FM08, no parecer. Justificativa dele: o artigo já
assume uma dimensão qualitativa (a RQ2 é "pedagogical-qualitative", e o texto registra que o
modelo elogia como qualidade o fenômeno plantado como problema, chegando a dizer que
"positively reinforces it"). Não é a qualidade plena, que depende de aluno real em interação
e fica para o piloto; é a validade mínima necessária para decidir se a FM ocorreu.

**Registro de evidência segmentada:** havendo um segmento válido e outro falso para a mesma
FM, codifica 1, e as Observações identificam os dois segmentos com justificativa, para que o
binário não apague o falso 1.

### 9.2 A codificação nº 4 sai do cálculo

A regra de validade mínima altera o instrumento de forma substantiva e pode mudar códigos que
ele já atribuiu. Na planilha há linhas com FM marcada como presente e Observação registrando
que a devolutiva elogia característica inexistente ou dá orientação tecnicamente inadequada.
A codificação dele é **preservada como percurso metodológico**, não como dado do κ.

### 9.3 Dois novos codificadores, não um

Sequência revista:
1. Discutir e aprovar entre os autores a versão final do protocolo.
2. Congelar antes de qualquer codificação.
3. Entregar o mesmo protocolo a **dois** novos codificadores independentes, sem acesso às codificações anteriores.
4. Preservar as duas separadamente antes de qualquer confronto.
5. Calcular a concordância **exclusivamente entre as duas novas codificações**.
6. Consolidar pelos 13 cenários, com as três execuções de cada.
7. Revisar método, resultados, discussão, limitações e conclusões.
8. Relatar aos avaliadores o percurso que levou à revisão do instrumento.

### 9.4 Correção de inferência no v0.3

O v0.3 escreveu: *"retirando a FM03 do cálculo, o κ médio vai de 0,138 para 0,149. O defeito
de instrumento, portanto, não explica o resultado."* **A segunda frase não decorre da
primeira.** O que o número mostra é que a regra antiga da FM03 não explica a discrepância
sozinha, não que o instrumento não contribua. A FM07 tem o mesmo número de divergências e
precisa ser investigada antes de afastar a hipótese, e a própria regra de validade mínima
oferece a hipótese: a definição da FM07 pode estar contando como desafio de ampliação
formulações apoiadas em informação inexistente ou situação comunicativa incoerente.
**Corrigir no v0.4.**

### 9.5 Outras exigências

- A procedência da codificação por IA precisa aparecer **no texto do artigo** com a mesma clareza que está no protocolo. Hoje o artigo diz "we coded the 39 outputs" e "a single-coder pass", o que permite ler como pessoa.
- Os exemplos dados aos novos codificadores **não podem** sair das 39 devolutivas que serão recodificadas. Só exemplos construídos ou do corpus humano.

### 9.6 Estado e esforço

- Enviado à Profa. Rosa em 10/08, com o Marcelo em cópia, o parecer + o `PROTOCOLO_REVISADO_v03.docx` (gerado com pandoc; o `paper/md_to_docx.py` usa `textutil`, ignora argumentos de linha de comando e sobrescreve o `.docx` do artigo, não usar).
- **Aguardando a leitura técnica da Rosa** para escrever o v0.4.
- **Esforço de referência: a codificação das 39 levou ~10 h.** Com dois codificadores, são ~20 h de trabalho de terceiros.
- **Os dois codificadores já estão garantidos** (Randerson, 10/08).
- Prazo da revista: ~10/09/2026.

---

## 10. Protocolo v0.4 e pacote dos codificadores (22/08/2026)

### 10.1 A Rosa respondeu em 11/08

Duas mensagens, na thread "Artigo JBCS - Benchmark de modelos - Protocolo revisado de codificação":

> "Randerson, concordo com encaminhar os dois documentos. Eu já tive uma situação semelhante ao
> analisar ressonâncias Magneticas (para um colega da área médica): as ressonâncias eram produzidas
> por máquinas diferentes. Mas a revista não colocou problemas, apenas apontamos estas diferenças.
> Como se tratava de medir um espaço do cérebro humano, cada conjunto de RMI foi analisado em
> função das características de cada máquina. A conclusão final juntou os resultados e foi única."

> "Prezado Randerson, concordo totalmente."

Vale para a carta-resposta: é um precedente de co-autora para declarar a diferença de procedência
em vez de escondê-la, com a conclusão final juntando os resultados.

### 10.2 O que foi produzido

Tudo em `data/codificacao_v04/`:

**Vai aos codificadores:** só o `GUIA_PROFESSOR` e a planilha. O material foi simplificado em
22/08 porque quem codifica são professores, não metodologistas: protocolo com histórico do estudo,
plano de análise e limitações é documento de artigo, não de tarefa, e treze vetores resolvidos
funcionariam como gabarito.

| Arquivo | O que é |
|---|---|
| `GUIA_PROFESSOR.md/.pdf/.docx` | **único documento entregue.** 3 páginas, ~1.150 palavras, sem jargão de método: oito definições em linguagem de professor com um exemplo cada, a coluna MTL, a regra do "parece mas não é" com três exemplos, quando escrever em Observações, três combinados de independência, prazo. Abre com o contexto da tese (PPGIE/UFRGS, devolutiva como 1ª passada com a professora conduzindo) e declara que os textos de aluno são fictícios; fecha dizendo o que acontece com a leitura, o crédito nos agradecimentos e que o pagamento não depende do resultado. Não diz a procedência das devolutivas, que é contada depois da entrega |
| `PROTOCOLO_v04.md/.pdf/.docx` | **interno.** Instrumento congelado e registro metodológico citado no artigo; regra de validade mínima na §3.0, item de falso positivo em cada FM, inferência da FM03/FM07 corrigida na §1.3, codificação nº 4 fora do κ na §1.5 |
| `ANEXO_CALIBRACAO.md/.pdf/.docx` | **interno.** Treze exemplos resolvidos, cinco de falso positivo, um de evidência segmentada; fonte de onde saíram, reduzidos, os exemplos do guia |
| `build_pacote_v04.py` | reconstrói as 39 da fonte e afirma, por assert, que são idênticas às de julho; gera os dois pacotes |
| `verifica_exemplos.py` | confere por programa que nenhum exemplo dos três documentos sai das 39 (102 trechos, 19 do corpus humano, 0 das 39) |
| `pacote_v04_codificador_{A,B}.csv` | material de anotação, mesmos IDs R01–R39 para os dois |
| `RECRUTAMENTO.*` | **fora do versionamento**, só no diretório local (está no `.gitignore`, porque traz valores e dados de contato). Perfil exigido dos codificadores e impedimentos (não pode ser autor nem um dos cinco professores do corpus humano), condições de remuneração, mensagens de recrutamento e o rascunho em inglês da frase de qualificação dos codificadores para a seção de confiabilidade |
| `EMAIL_convite_codificador.md` | texto do convite. Não há e-mail de congelamento: o parecer de 10/08 e o aceite da Rosa de 11/08 já fecharam a decisão, e o v0.4 é a execução dela |

Planilhas no Google Sheets, criadas e **ainda não compartilhadas** (faltam os e-mails dos dois
codificadores):

- Codificador A: `1wIGoRDItjZiRW-duak_gKpmzJEpBbE8MYHpO7nSv4gg`
- Codificador B: `1gjRHxW-Uh9UpiiFJS6HY7CltzckbK8pCM0nhEuhu3T0`

Três rascunhos no Gmail: um na thread dos autores (congelamento) e um por codificador, sem
destinatário. Os anexos precisam ser arrastados na hora de enviar, a API de rascunho não os aceita
a partir do repositório.

### 10.3 Recrutamento dos dois codificadores

Decidido em 22/08: os codificadores são recrutados **por chamada pública no LinkedIn**, com
formulário de inscrição (nome, Lattes, formação, tempo de sala de aula, rede, prática de devolutiva,
disponibilidade e a pergunta de contato prévio com o estudo). Material em `RECRUTAMENTO.*`, que
fica fora do versionamento por conter valores e dados de contato.

Perfil exigido: licenciatura em Letras (Português), 3 anos ou mais de Ensino Fundamental II com
experiência em 8º ou 9º ano, prática atual de corrigir produção textual com devolutiva escrita.
Impedidos: autores, integrantes do grupo de pesquisa, os cinco professores do corpus humano e quem
já teve contato com o material do estudo.

O recrutamento aberto **melhora o artigo**, e não só resolve a logística: a seção de confiabilidade
passa a poder declarar quem codificou, com que qualificação, o que garantiu a independência e que a
remuneração foi fechada antes e não depende do resultado. O rascunho dessa frase, em inglês, está
no `RECRUTAMENTO.md` §6.

Esforço informado aos candidatos: ~10 h, que é o registro do próprio Marcelo ao codificar as mesmas
39 devolutivas. É o único dado real de esforço que existe sobre esta tarefa.

### 10.4 Cronograma até o prazo

| Quando | O quê |
|---|---|
| 22/08 | publicar a chamada e abrir o formulário |
| até 26/08 | inscrições |
| 27/08 | escolha das duas pessoas, combinação do valor, compartilhamento das planilhas e envio dos convites |
| até 05/09 | as duas codificações, ~10 h cada |
| 05–09/09 | κ(A,B), consolidação por cenário, exame da FM07, reescrita de método, resultados, discussão, limitações e conclusão |
| 10/09 | prazo da revista |

**Sem folga.** Se em 27/08 o formulário não tiver dois nomes de perfil adequado, o plano B é convite
direto a contatos com o mesmo perfil e o mesmo valor, decidido no mesmo dia.

### 10.5 Pendências que não dependem de terceiros

- `analises/kappa_v04.py`: adaptar `kappa_2a_codificacao.py` para o par A × B; dá para escrever e testar com dados sintéticos enquanto a codificação acontece.
- Zenodo: só a v1.5.0 de 29/06 está depositada, sem nada da R1. A Data Availability declara material que não está lá.
- Decisão em aberto: as `.xlsx` do Marcelo, com as observações qualitativas linha a linha, vão para o repositório público?
- A procedência da codificação por IA ainda precisa entrar no **texto do artigo** (§ método), não só no protocolo.
