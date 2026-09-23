# 🧬 Navegação no AlphaFold Protein Structure Database (AFDB)

> **Objetivo:** explorar modelos estruturais preditos pelo AlphaFold, compará-los com as estruturas experimentais disponíveis e interpretar criticamente as métricas de confiança **pLDDT** e **PAE**.

---

## 📋 Sumário

- [Proteínas de estudo](#-proteínas-de-estudo)
- [Recursos utilizados](#-recursos-utilizados)
- [Roteiro](#-roteiro)
- [Perguntas](#-perguntas)
- [Atividade complementar](#-atividade-complementar-opcional)
- [Modelo de entrega](#-modelo-de-entrega)

---

## 🔬 Proteínas de estudo

Nesta seção da prática serão utilizadas as proteínas identificadas pelos seguintes códigos UniProt:

| # | Código UniProt | AFDB |
|:-:|:--------------:|:----:|
| 1 | [`Q08380`](https://www.uniprot.org/uniprotkb/Q08380) | [abrir modelo](https://alphafold.ebi.ac.uk/entry/Q08380) |
| 2 | [`P50995`](https://www.uniprot.org/uniprotkb/P50995) | [abrir modelo](https://alphafold.ebi.ac.uk/entry/P50995) |
| 3 | [`Q9NZQ7`](https://www.uniprot.org/uniprotkb/Q9NZQ7) | [abrir modelo](https://alphafold.ebi.ac.uk/entry/Q9NZQ7) |

---

## 🌐 Recursos utilizados

| Recurso | Para que serve |
|---------|----------------|
| [AlphaFold DB](https://alphafold.ebi.ac.uk/) | Modelos preditos, pLDDT e matriz de PAE |
| [PDBe-KB](https://www.ebi.ac.uk/pdbe/pdbe-kb/) | Cobertura da sequência por estruturas experimentais |
| [RCSB PDB](https://www.rcsb.org/) | Detalhes das estruturas experimentais e alinhamento estrutural |
| [UniProt](https://www.uniprot.org/) | Função, tamanho e anotação de domínios |
| [InterPro](https://www.ebi.ac.uk/interpro/) | Anotação de domínios e famílias |

---

## 🧭 Roteiro

1. Abra o site do [AFDB](https://alphafold.ebi.ac.uk/) e busque cada um dos códigos acima.
2. Entre nas respectivas páginas e responda às perguntas abaixo **para cada proteína**.
3. Organize as respostas no [modelo de entrega](#-modelo-de-entrega) ao final deste documento.

> [!TIP]
> A página de cada entrada no AFDB traz links diretos para o UniProt e para o PDBe-KB. Use-os para navegar entre os bancos sem precisar refazer as buscas.

---

## ❓ Perguntas

### Parte 1 — Identificação e estruturas experimentais

**1.** Qual é essa proteína? De qual organismo ela é? Qual é sua função principal e quantos resíduos ela possui?

**2.** Existem estruturas experimentais disponíveis para ela? Indique o método de cada uma (difração de raios X, cryo-EM ou RMN).

**3.** As estruturas experimentais cobrem a totalidade da proteína?

Para responder, use o link para o **PDBe-KB** fornecido na página do AFDB. A visualização de cobertura mostra quais regiões da sequência estão representadas em estruturas depositadas. Se preferir, busque os códigos no [RCSB PDB](https://www.rcsb.org/).

- Se houver **poucas estruturas**, liste-as com os resíduos cobertos por cada uma.
- Se houver **muitas estruturas** (dezenas ou centenas), indique a faixa máxima de resíduos coberta e escolha 2 a 3 estruturas representativas, justificando a escolha.

> [!IMPORTANT]
> Muitas entradas do PDB correspondem a **construtos truncados**, **mutantes**, **proteínas de outra espécie** ou **complexos** com outras moléculas (anticorpos, ligantes, parceiros de interação). Indique quando for o caso.

### Parte 2 — Qualidade do modelo predito

**4.** De volta à página do AFDB, avalie a qualidade da estrutura predita. Quais regiões possuem **pLDDT abaixo de 70**? O que isso significa?

**5.** Quantos domínios a proteína possui? Responda de duas formas:

- **(a)** pela anotação de domínios do UniProt (seção *Family & Domains*) ou do InterPro;
- **(b)** pela inspeção visual do modelo e da matriz de PAE.

Os dois números coincidem? Se não, por quê?

**6.** É possível identificar cada um dos domínios na matriz de **Predicted Aligned Error (PAE)**? Por quê?

**7.** A posição relativa entre os domínios tem boa qualidade? Justifique com base na matriz de PAE.

**8.** O pLDDT é uma medida de confiança **local**, enquanto o PAE mede a confiança na **posição relativa** entre pares de resíduos. Com base nisso, como o gráfico de PAE e o pLDDT se relacionam?

Dê um exemplo, em uma das proteínas estudadas, de duas regiões que individualmente têm pLDDT alto, mas cuja posição relativa tem PAE alto.

### Parte 3 — Interpretação crítica

**9.** Trata-se de uma proteína **estruturada**, **intrinsecamente desordenada** ou **parcialmente desordenada**? Justifique.

Discuta também: uma região com pLDDT baixo é necessariamente desordenada? Que outras razões podem levar o AlphaFold a atribuir baixa confiança a uma região?

**10.** Quais aspectos da proteína real o modelo do AFDB **não representa**? Considere, por exemplo:

- o estado oligomérico;
- modificações pós-traducionais (como glicosilação);
- a presença de membrana, íons, ligantes e parceiros de interação;
- a remoção do peptídeo sinal na proteína madura.

---

## 🧪 Atividade complementar (opcional)

**11.** Escolha uma estrutura experimental de uma das proteínas e sobreponha-a ao modelo do AFDB usando a ferramenta de alinhamento par a par do RCSB PDB (*Tools → Pairwise Structure Alignment*).

Compare o RMSD obtido alinhando a **proteína inteira** com o RMSD obtido alinhando **cada domínio separadamente**. Relacione o resultado com a sua resposta à pergunta 7.

---

## 📝 Modelo de entrega

Preencha a tabela abaixo com as respostas objetivas. As perguntas discursivas (4, 6–10) devem ser respondidas nas seções seguintes.

| Pergunta | Q08380 | P50995 | Q9NZQ7 |
|----------|--------|--------|--------|
| **1.** Nome da proteína | | | |
| **1.** Organismo | | | |
| **1.** Função principal | | | |
| **1.** Nº de resíduos | | | |
| **2.** Estruturas experimentais (método) | | | |
| **3.** Faixa de resíduos coberta | | | |
| **4.** Regiões com pLDDT < 70 | | | |
| **5a.** Nº de domínios (UniProt/InterPro) | | | |
| **5b.** Nº de domínios (modelo/PAE) | | | |
| **9.** Classificação | | | |

<details>
<summary><b>Respostas discursivas — Q08380</b></summary>

**4.**

**6.**

**7.**

**8.**

**9.**

**10.**

</details>

<details>
<summary><b>Respostas discursivas — P50995</b></summary>

**4.**

**6.**

**7.**

**8.**

**9.**

**10.**

</details>

<details>
<summary><b>Respostas discursivas — Q9NZQ7</b></summary>

**4.**

**6.**

**7.**

**8.**

**9.**

**10.**

</details>

---

## 📚 Referências

- Jumper, J. *et al.* Highly accurate protein structure prediction with AlphaFold. *Nature* **596**, 583–589 (2021).
- Varadi, M. *et al.* AlphaFold Protein Structure Database: massively expanding the structural coverage of protein-sequence space with high-accuracy models. *Nucleic Acids Research* **50**, D439–D444 (2022).
