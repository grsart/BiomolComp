# Busca por Similaridade com BLAST e PSI-BLAST

Nas práticas anteriores (02A-02C) trabalhamos com o alinhamento de **pares** de
sequências já conhecidas, usando matrizes de substituição (NUC.4.4, BLOSUM62)
e algoritmos de Programação Dinâmica (Needleman-Wunsch e Smith-Waterman).

Nesta última parte, vamos inverter o problema: dada **uma única sequência**,
vamos usar o BLAST para buscar, num banco de dados com milhões de sequências,
quais são as mais parecidas com ela. Em seguida, usaremos o **PSI-BLAST** para
refinar essa busca de forma iterativa.

A sequência de aminoácidos que vamos usar é a seguinte:

```
TGQVQLQESGGGLVQPGGSLRLSCAASGKMSSRRCMAWFRQAPGKERERVAKLLTTSGSTYLADSVKGRFTISQNNAKSTVYLQMNSLKPEDTAMYYCAADSFEDPTCTLVTSSGAFQYWGQGTQVTVSSGSMDPGG
```

Essa sequência corresponde a um **domínio variável isolado de anticorpo**
(um fragmento de imunoglobulina). Guarde essa pista, ela vai ser útil para
interpretar os resultados das buscas abaixo, principalmente na comparação
entre BLASTP e PSI-BLAST.

---

## Parte 1 — BLASTP com parâmetros default

Acesse o [BLASTP](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastp&PAGE_TYPE=BlastSearch&LINK_LOC=blasthome)
e execute a busca com a sequência acima, usando os **parâmetros default**.

> **O que "parâmetros default" significa na prática?** O BLASTP, por padrão,
> usa a matriz de substituição **BLOSUM62** (a mesma que vimos nas Práticas
> 02A e 02C) e um custo de gap *existence=11, extension=1*. São os
> mesmos conceitos de matriz de substituição e penalidade de gap que já
> exploramos nos notebooks anteriores, só que agora aplicados por uma
> ferramenta de busca em larga escala em vez de um alinhamento par-a-par.

**Q7-** Registre e discuta:

- a. Qual o **E-value** e a **%identidade** do melhor hit (primeiro resultado)?
- b. Qual a **cobertura da query** (*query coverage*) desse melhor hit?
- c. De qual **organismo** vêm os primeiros hits da lista?
- d. Algum dos primeiros hits está anotado como um domínio de anticorpo
  (nanobody, VHH, *single-domain antibody*, imunoglobulina)? Ou os hits
  parecem não relacionados a anticorpos?
- e. Com base nesses dados, você diria que essa busca encontrou uma
  sequência de referência clara e confiável para a nossa proteína, ou os
  resultados parecem fracos/ambíguos?

*Dica de registro: tire um print da tela de resultados (lista de hits com
E-value, identidade e cobertura) para poder comparar com as próximas etapas.*

---

## Parte 2 — PSI-BLAST

Repita a busca, agora usando a versão **PSI-BLAST**
([link direto](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastp&BLAST_SPEC=psiBlast&PAGE_TYPE=BlastSearch&LINK_LOC=blasthome)),
com a mesma sequência e parâmetros default.

> **O que o PSI-BLAST faz de diferente?** Um BLASTP comum sempre pontua os
> alinhamentos usando a mesma matriz fixa (BLOSUM62). O **PSI-BLAST**
> ("Position-Specific Iterated BLAST") funciona em rodadas: depois da
> primeira busca, ele pega os hits estatisticamente significativos, monta um
> **alinhamento múltiplo** entre eles e constrói uma **PSSM**
> (*Position-Specific Scoring Matrix*). Isso nada mais é do que uma matriz de
> substituição > **customizada para aquela família de sequências**, em vez de uma
> matriz genérica. Essa PSSM é usada como pontuação na iteração seguinte, permitindo
> encontrar sequências mais divergentes (homólogos remotos) que passariam
> despercebidos por uma matriz fixa como a BLOSUM62.

**Q8-** Compare com a Q7:

- a. Os hits de topo mudaram em relação ao BLASTP simples? Em quê?
- b. O E-value e a %identidade do melhor hit mudaram?
- c. Isso é esperado, considerando que essa é só a **primeira iteração** do
  PSI-BLAST (que ainda usa BLOSUM62, e não uma PSSM)? Nesse ponto, o
  resultado do PSI-BLAST deveria ser igual, parecido, ou diferente do BLASTP
  simples? Por quê?

---

## Parte 3 — Segunda iteração do PSI-BLAST

Na tela de resultados da Parte 2, clique no botão **"Run"** para disparar uma
nova iteração de busca (a segunda).

**Q9-** Registre e discuta:

- a. O que mudou na lista de hits em relação à primeira iteração (Q8)? Os
  E-values ficaram mais ou menos significativos?
- b. Que **tipo** de sequências passou a aparecer na lista? Ainda são parecidas
  com os hits anteriores, ou surgiram sequências de organismos/famílias
  diferentes?
- c. Isso é consistente com a explicação da PSSM dada na Parte 2?  
  Faz sentido que hits mais divergentes tenham aparecido agora?

---

## Parte 4 — Terceira iteração e avaliação de convergência

Rode mais uma iteração de busca, apertando novamente o botão **"Run"**.

**Q10-** Responda:

- a. Por que pode ser relevante rodar uma nova iteração após o resultado
  anterior? (pense em termos da PSSM sendo reconstruída a cada rodada)
- b. Qual foi a mudança observada na lista de hits desta vez, em comparação
  com a iteração anterior (Q9)?
- c. O que aconteceu com a sequência que estava na **primeira posição** do
  BLASTP original (Q7)? Ela continua no topo, caiu de posição, ou
  desapareceu da lista?
- d. É necessário executar mais uma iteração de busca? Justifique sua
  resposta usando o conceito de **convergência**: o PSI-BLAST é considerado
  convergente quando uma nova iteração não traz nenhuma sequência nova acima
  do limiar de significância (E-value) — ou seja, o conjunto de hits
  significativos deixa de mudar entre uma rodada e a seguinte. A sua busca
  já chegou nesse ponto?

---

## Síntese

1. Compare os resultados de BLASTP (Q7) com a última iteração do PSI-BLAST
  (Q10). O que esse experimento mostra sobre os limites de uma matriz de
  substituição fixa (BLOSUM62) para encontrar homólogos remotos?
2. Por que uma matriz de pontuação *específica da família* (PSSM) consegue
  captar relações evolutivas que uma matriz genérica não capta?
3. Que tipo de proteína (pense na dica dada no início) se beneficia
  particularmente desse tipo de busca iterativa, e por quê?
