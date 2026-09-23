# 🌀 Predição de ensemble conformacional com BioEmu

> **Objetivo:** gerar um conjunto de conformações para um segmento curto de proteína usando o [BioEmu](https://www.science.org/doi/10.1126/science.adv9817), comparar esse ensemble com as predições do AlphaFold3 da parte anterior e discutir o que cada método é capaz (ou não) de representar.

---

## 📋 Sumário

- [Visão geral](#-visão-geral)
- [Sistema de estudo](#-sistema-de-estudo)
- [Roteiro](#-roteiro)
- [Perguntas](#-perguntas)
- [Atividade complementar](#-atividade-complementar-opcional)
- [Modelo de entrega](#-modelo-de-entrega)

---

## 🔭 Visão geral

O AlphaFold prediz, essencialmente, **uma** estrutura para cada sequência. O BioEmu é um modelo generativo treinado para **emular a distribuição de conformações de equilíbrio** de uma proteína: em vez de uma estrutura, ele gera um *ensemble*.

Nesta seção da prática, vamos gerar **50 conformações** para o peptídeo do **Sistema 2 da parte 2** e compará-las com as predições do AlphaFold3 com 1 e com 6 cópias.

Usaremos um Google Colab desenvolvido por terceiros (equipe do ColabFold), que executa o BioEmu, agrupa as conformações geradas com o **Foldseek** e permite visualizá-las.

> [!IMPORTANT]
> O BioEmu, como implementado neste notebook, trabalha **apenas com monômeros**. Ele não gera montagens de várias cópias como o AlphaFold3 fez com 6 cópias. Tenha isso em mente ao responder às perguntas.

---

## 🔬 Sistema de estudo

Peptídeo do Sistema 2 da parte 2:

```
LDNVATYAGQFNQDYLSGMAANMSGTFGGANMPNLYP
```

> [!TIP]
> Copie a sequência diretamente do bloco acima para evitar espaços ou quebras de linha.

---

## 🧭 Roteiro

1. Abra o [Google Colab do BioEmu](https://colab.research.google.com/github/grsart/BiomolComp/blob/main/P05/BioEmu.ipynb).
2. Verifique se o ambiente de execução está usando **GPU** (*Ambiente de execução → Alterar o tipo de ambiente de execução*). O notebook já vem configurado para GPU T4, mas confira.
3. Na primeira célula (*Sample with following config*), preencha:

   | Campo | Valor |
   |-------|-------|
   | `sequence` | a sequência acima |
   | `num_samples` | `50` |
   | `jobname` | um nome à sua escolha (por exemplo, `peptideo_sistema2`) |

   Mantenha os demais campos com os valores padrão.
4. Clique em **Executar tudo** (*Runtime → Run all*). A instalação das dependências leva alguns minutos.
5. Na seção **Display structure** aparecerão duas barras deslizantes:
   - **Cluster No:** escolhe o cluster (grupo de conformações semelhantes, definido pelo Foldseek);
   - **Sample Idx:** escolhe a conformação dentro do cluster.

   Navegue pelos clusters e pelas conformações de cada um.

> [!NOTE]
> Com a opção `filter_samples` ativada (padrão), conformações fisicamente irreais (com quebras de cadeia, por exemplo) são descartadas. Por isso, o número final de conformações pode ser **menor que 50**.

> [!NOTE]
> As conformações geradas pelo BioEmu contêm **apenas a cadeia principal**. A última célula do notebook (opcional) reconstrói as cadeias laterais e faz uma minimização de energia. Se ela apresentar erro, isso não afeta as análises desta prática.

---

## ❓ Perguntas

### Parte 1 — O ensemble gerado

**1.** Quantas conformações restaram após a filtragem? Em quantos clusters o Foldseek as agrupou? Como os clusters se distribuem: há um cluster dominante ou muitos clusters com poucas conformações cada?

**2.** O que o número e a distribuição dos clusters indicam sobre a heterogeneidade conformacional do peptídeo?

> [!TIP]
> O agrupamento usa um limiar de TM-score. Pense em como o TM-score se comporta para cadeias muito curtas e em como isso pode influenciar a quantidade de clusters obtida.

### Parte 2 — Estrutura secundária

**3.** Existe preferência por algum tipo de estrutura secundária (hélice, fita β, *coil*) no ensemble gerado? Essa preferência se concentra em alguma região específica do peptídeo? Se fizer a [atividade complementar](#-atividade-complementar-opcional), use a quantificação por resíduo para responder.

### Parte 3 — Comparação com o AlphaFold3

**4.** Compare o ensemble do BioEmu com a predição do AlphaFold3 com **1 cópia**. As conformações se parecem? O que o pLDDT do AlphaFold3 dizia sobre esse peptídeo, e como isso se relaciona com o ensemble do BioEmu?

**5.** Compare o ensemble do BioEmu com a predição do AlphaFold3 com **6 cópias**. Identifique quais resíduos formam estrutura secundária no arranjo de 6 cópias. Alguma conformação do ensemble do BioEmu apresenta esses mesmos resíduos em conformação semelhante? O que isso sugere sobre a origem da estrutura observada com 6 cópias: ela é uma propriedade do peptídeo isolado ou surge da interação entre as cópias?

### Parte 4 — Interpretação crítica

**6.** Com que tipos de dados o BioEmu foi treinado? Consulte o [artigo](https://www.science.org/doi/10.1126/science.adv9817). Com base nisso, você esperaria que ele representasse bem um segmento de baixa complexidade como este? O notebook também gera um MSA para a sequência: que tipo de informação evolutiva se espera obter para uma região como esta?

**7.** Considerando as três predições (BioEmu, AlphaFold3 com 1 cópia e com 6 cópias), qual descrição você considera mais adequada para este peptídeo em solução? E no contexto de uma fibra? Justifique.

---

## 🧪 Atividade complementar (opcional)

**8.** Quantifique a estrutura secundária de cada resíduo ao longo do ensemble. Adicione uma nova célula de código **ao final do notebook** (após a execução completa) e cole o código abaixo:

```python
import os
import mdtraj as md
import numpy as np
import matplotlib.pyplot as plt

traj = md.load(os.path.join(output_dir, "samples.xtc"),
               top=os.path.join(output_dir, "topology.pdb"))

# H = hélice, E = fita beta, C = coil
ss = md.compute_dssp(traj, simplified=True)
seq = traj.topology.to_fasta()[0]
pos = np.arange(1, len(seq) + 1)

frac = {s: (ss == s).mean(axis=0) * 100 for s in ["H", "E", "C"]}

print(f"Conformações analisadas: {traj.n_frames}\n")
print("Pos Res    %H     %E     %C")
for i, aa in enumerate(seq):
    print(f"{i+1:3d}  {aa}  {frac['H'][i]:5.1f}  {frac['E'][i]:5.1f}  {frac['C'][i]:5.1f}")

fig, ax = plt.subplots(figsize=(10, 3))
ax.bar(pos, frac["H"], label="Hélice", color="tab:red")
ax.bar(pos, frac["E"], bottom=frac["H"], label="Fita β", color="tab:blue")
ax.bar(pos, frac["C"], bottom=frac["H"] + frac["E"], label="Coil", color="lightgray")
ax.set_xticks(pos)
ax.set_xticklabels(list(seq))
ax.set_xlabel("Resíduo")
ax.set_ylabel("% das conformações")
ax.set_ylim(0, 100)
ax.legend(loc="upper right", ncol=3)
plt.tight_layout()
plt.show()
```

Quais resíduos têm maior propensão a formar fita β? E hélice? Compare com os resíduos estruturados na predição do AlphaFold3 com 6 cópias.

---

## 📝 Modelo de entrega

| Item | Resposta |
|------|----------|
| Nº de conformações após a filtragem | |
| Nº de clusters | |
| Tamanho do maior cluster | |
| Estrutura secundária predominante | |
| Região com maior propensão a fita β | |
| Região com maior propensão a hélice | |
| Resíduos estruturados no AF3 (6 cópias) | |

<details>
<summary><b>Respostas discursivas — Parte 1</b></summary>

**1.**

**2.**

</details>

<details>
<summary><b>Respostas discursivas — Parte 2</b></summary>

**3.**

</details>

<details>
<summary><b>Respostas discursivas — Parte 3</b></summary>

**4.**

**5.**

</details>

<details>
<summary><b>Respostas discursivas — Parte 4</b></summary>

**6.**

**7.**

</details>

<details>
<summary><b>Atividade complementar</b></summary>

**8.**

</details>

---

## 📚 Referências

- Lewis, S. *et al.* Scalable emulation of protein equilibrium ensembles with generative deep learning. *Science* (2025). [doi:10.1126/science.adv9817](https://www.science.org/doi/10.1126/science.adv9817)
- [Repositório do BioEmu (Microsoft)](https://github.com/microsoft/bioemu)
- [Notebook do BioEmu no ColabFold](https://github.com/sokrypton/ColabFold/blob/main/BioEmu.ipynb)
- van Kempen, M. *et al.* Fast and accurate protein structure search with Foldseek. *Nature Biotechnology* **42**, 243–246 (2024).
