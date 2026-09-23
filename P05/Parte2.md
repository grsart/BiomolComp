# 🧩 Predição de complexos com AlphaFold3

> **Objetivo:** usar o [AlphaFold Server](https://alphafoldserver.com/) para predizer complexos proteicos, interpretar as métricas de confiança **pLDDT**, **PAE**, **pTM** e **ipTM** e reconhecer as situações em que essas métricas enganam.

---

## 📋 Sumário

- [Visão geral](#-visão-geral)
- [Sistemas de estudo](#-sistemas-de-estudo)
- [Roteiro](#-roteiro)
- [Perguntas](#-perguntas)
- [Atividade complementar](#-atividade-complementar-opcional)
- [Modelo de entrega](#-modelo-de-entrega)

---

## 🔭 Visão geral

Nesta seção da prática, o foco será a predição de **complexos**: heterodímeros e homo-oligômeros. Os três sistemas estão relacionados às proteínas analisadas na parte anterior (AFDB), o que permite comparar a predição de cada cadeia isolada com a predição no contexto do complexo.

| Sistema | Tipo | Nº de execuções |
|:-------:|------|:---------------:|
| 1 | Heterodímero | 1 |
| 2 | Homo-oligômero (1 e 6 cópias) | 2 |
| 3 | Heterodímero | 1 |
| | **Total** | **4** |

> [!WARNING]
> O AlphaFold Server tem **cota diária de jobs por conta**. Confira as sequências antes de submeter para não gastar execuções com erros de digitação.

---

## 🔬 Sistemas de estudo

> [!TIP]
> Copie as sequências diretamente dos blocos de código abaixo. Copiar de texto corrido pode introduzir quebras de linha ou espaços que o servidor rejeita.

### Sistema 1

**Proteína 1**

```
MADNFSLHDALSGSGNPNPQGWPGAWGNQPAGAGGYPGASYPGAYPGQAPPGAYPGQAPPGAYPGAPGAYPGAPAPGVYPGPPSGPGAYPSSGQPSATGAYPATGPYGAPAGPLIVPYNLPLPGGVVPRMLITILGTVKPNANRIALDFQRGNDVAFHFNPRFNENNRRVIVCNTKLDNNWGREERQSVFPFESGKPFKIQVLVEPDHFKVAVNDAHLLQYNHRVKKLNEISKLGISGDIDLTSASYTMI
```

**Proteína 2**

```
MTPPRLFWVWLLVAGTQGVNDGDMRLADGGATNQGRVEIFYRGQWGTVCDNLWDLTDASVVCRALGFENATQALGRAAFGQGSGPIMLDEVQCTGTEASLADCKSLGWLKSNCRHERDAGVVCTNETRSTHTLDLSRELSEALGQIFDSQRGCDLSISVNVQGEDALGFCGHTVILTANLEAQALWKEPGSNVTMSVDAECVPMVRDLLRYFYSRRIDITLSSVKCFHKLASAYGARQLQGYCASLFAILLPQDPSFQMPLDLYAYAVATGDALLEKLCLQFLAWNFEALTQAEAWPSVPTDLLQLLLPRSDLAVPSELALLKAVDTWSWGERASHEEVEGLVEKIRFPMMLPEELFELQFNLSLYWSHEALFQKKTLQALEFHTVPFQLLARYKGLNLTEDTYKPRIYTSPTWSAFVTDSSWSARKSQLVYQSRRGPLVKYSSDYFQAPSDYRYYPYQSFQTPQHPSFLFQDKRVSWSLVYLPTIQSCWNYGFSCSSDELPVLGLTKSGGSDRTIAYENKALMLCEGLFVADVTDFEGWKAAIPSALDTNSSKSTSSFPCPAGHFNGFRTVIRPFYLTNSSGVD
```

### Sistema 2

**Proteína 1**

```
LDNVATYAGQFNQDYLSGMAANMSGTFGGANMPNLYP
```

| Situação | Número de cópias |
|:--------:|:----------------:|
| 1 | 6 |
| 2 | 1 |

### Sistema 3

**Proteína 1**

```
MRIFAVFIFMTYWHLLNAFTVTVPKDLYVVEYGSNMTIECKFPVEKQLDLAALIVYWEMEDKNIIQFVHGEEDLKVQHSSYRQRARLLKDQLSLGNAALQITDVKLQDAGVYRCMISYGGADYKRITVKVNAPYNKINQRILVVDPVTSEHELTCQAEGYPKAEVIWTSSDHQVLSGKTTTTNSKREEKLFNVTSTLRINTTTNEIFYCTFRRLDPEENHTAELVIPELPLAHPPNERTHLVILGAILLCLGVALTFIFRLRKGRMMDVKKCGIQDTNSKKQSDTHLEET
```

**Proteína 2**

```
MQIPQAPWPVVWAVLQLGWRPGWFLDSPDRPWNPPTFSPALLVVTEGDNATFTCSFSNTSESFVLNWYRMSPSNQTDKLAAFPEDRSQPGQDCRFRVTQLPNGRDFHMSVVRARRNDSGTYLCGAISLAPKAQIKESLRAELRVTERRAEVPTAHPSPSPRPAGQFQTLVVGVVGGLLGSLVLLVWVLAVICSRAARGTIGARRTGQPLKEDPSAVPVFSVDYGELDFQWREKTPEPPVPCVPEQTEYATIVFPSGMGTSSPARRGSADGPRSAQPLRPEDGHCSWPL
```

> [!NOTE]
> As sequências dos sistemas 1 e 3 estão completas, **incluindo o peptídeo sinal**, que é removido na proteína madura. Leve isso em conta ao interpretar as regiões de baixa confiança.

---

## 🧭 Roteiro

1. Acesse o [AlphaFold Server](https://alphafoldserver.com/) e faça login.
2. **Antes de iniciar qualquer análise, submeta os 4 jobs** (um para cada sistema/situação). Assim, o servidor processa as predições enquanto você trabalha.
3. Para o Sistema 2, crie dois jobs distintos: um com **6 cópias** e outro com **1 cópia** da mesma sequência.
4. Quando os jobs terminarem, abra cada resultado e responda às perguntas abaixo.

> [!IMPORTANT]
> O AlphaFold Server gera **5 modelos** por job. Não analise apenas o primeiro: comparar os modelos entre si é parte da avaliação de qualidade.

---

## ❓ Perguntas

### Parte 1 — Identificação

**1.** Identifique cada proteína dos três sistemas (busca por BLAST ou no UniProt). Quais delas você já analisou na parte anterior da prática? Qual trecho da proteína corresponde ao peptídeo do Sistema 2?

### Parte 2 — Qualidade das cadeias individuais

**2.** A predição de cada cadeia individual foi bem feita em todos os casos? Descreva em termos de pLDDT e do PAE **intracadeia**. Compare com os modelos do AFDB que você analisou na parte anterior: a predição de cada cadeia mudou no contexto do complexo?

### Parte 3 — Qualidade do complexo

**3.** Qual a qualidade da predição de cada complexo? Considere:

- os blocos **intercadeia** da matriz de PAE;
- a matriz de **ipTM por par de cadeias** fornecida pelo servidor;
- a consistência da interface entre os **5 modelos** gerados.

Quais regiões tiveram posição relativa bem predita?

**4.** Explique o que são o **pTM** e o **ipTM** e como eles podem ser utilizados para mensurar a qualidade de uma predição. Quais faixas de valores indicam predições confiáveis, duvidosas ou provavelmente incorretas? Em que situações essas métricas não funcionam bem? Considere, em particular:

- o efeito de regiões desordenadas ou de hélices transmembrana sem a membrana;
- o efeito de cadeias muito curtas.

### Parte 4 — Análise de cada sistema

**5.** *(Sistema 1)* O que a Proteína 1 reconhece na Proteína 2 para se ligar a ela? Esse elemento está presente na predição? Como isso se reflete nas métricas de confiança do complexo?

**6.** *(Sistema 2)* Como o número de cópias afetou o resultado? Quais as hipóteses para explicar o que aconteceu?

**7.** *(Sistema 2)* Como você verificaria se o arranjo predito com 6 cópias existe experimentalmente? Consulte o PDB e a literatura e discuta: o AlphaFold3 acertou, ou poderia estar gerando um artefato?

**8.** *(Sistema 3)* A interface entre os domínios extracelulares foi bem predita, segundo o PAE intercadeia? O valor global de ipTM reflete essa qualidade? Por quê?

---

## 📝 Modelo de entrega

| Métrica | Sistema 1 | Sistema 2 (6 cópias) | Sistema 2 (1 cópia) | Sistema 3 |
|---------|:---------:|:--------------------:|:-------------------:|:---------:|
| Identidade das proteínas | | | | |
| pTM | | | | |
| ipTM | | | — | |
| Regiões com pLDDT < 70 | | | | |
| Interface consistente entre os 5 modelos? | | | — | |

<details>
<summary><b>Respostas discursivas — Sistema 1</b></summary>

**2.**

**3.**

**5.**

</details>

<details>
<summary><b>Respostas discursivas — Sistema 2</b></summary>

**2.**

**3.**

**6.**

**7.**

</details>

<details>
<summary><b>Respostas discursivas — Sistema 3</b></summary>

**2.**

**3.**

**8.**

</details>

<details>
<summary><b>Resposta discursiva — Pergunta 4 (pTM e ipTM)</b></summary>

**4.**

</details>

<details>
<summary><b>Atividade complementar</b></summary>

**9.**

**10.**

</details>

---

## 📚 Referências

- Abramson, J. *et al.* Accurate structure prediction of biomolecular interactions with AlphaFold 3. *Nature* **630**, 493–500 (2024).
- [AlphaFold Server — FAQ e guia de interpretação dos resultados](https://alphafoldserver.com/faq)
