# Análise Filogenética de Sequências – Parte 2
## Identificação de família para duas proteínas inéditas

> **Objetivos desta parte:** recuperar proteínas no NCBI, identificar o domínio de transcriptase reversa com o CD-Search, extrair apenas a região do domínio e classificar as duas proteínas na árvore construída na Parte 1.  
> **O que entregar:** respostas das questões Q10 a Q15; o arquivo **filogenia2.fasta**; print da árvore enraizada com as duas novas sequências.

1. Entre no site do [NCBI](https://www.ncbi.nlm.nih.gov/) (busca Entrez).
  
2. Busque o código de acesso **CAJ00246.1**
  
3. **Q10- Em qual banco de dados do NCBI (Protein, Nucleotide, Gene...) está este registro? Como você sabe, olhando apenas o código de acesso e o resultado da busca?**  
   Abra a página do registro no banco **Protein**.
  
4. Faça a predição de domínios conservados nesta proteína, usando uma ferramenta do próprio NCBI. Ela fica no painel à direita da página da proteína, em **Analyze this sequence** > **Identify Conserved Domains** (CD-Search).
  
5. **Q11- Qual banco de domínios a ferramenta usa e qual domínio de transcriptase reversa ela identificou (nome e código)?**
  
6. Identifique o intervalo de resíduos de aminoácidos que representa o domínio de transcriptase reversa desta proteína.
  
7. Volte na página da proteína. Restrinja a sequência para o intervalo encontrado no passo anterior.  
    Para isso, use a opção **Change region shown** no canto superior direito, e depois escolha **FASTA** em *Display*.
  
8. Copie a sequência FASTA e salve em um arquivo de texto chamado ***filogenia2.fasta***.  
   **Substitua a linha de cabeçalho inteira** (a linha que começa com `>`) por apenas:  
   ```
   >TPA_poliprotein
   ```
   Se o cabeçalho longo do NCBI for mantido, o nome na árvore ficará ilegível ou será cortado pelo programa.
  
9. **Q12- Qual a importância de se obter somente a região do domínio?  
        Como isso impacta na construção da árvore?  
        Explique usando os conceitos de sinal e ruído filogenético.**
  
10. Repita o mesmo procedimento, dos passos 4 a 8, para a sequência cujo código de acesso é **CAJ00242.1**
  
11. Neste caso, o cabeçalho deve ser substituído por **>TPA_Sm** e a sequência salva no mesmo arquivo ***filogenia2.fasta***, logo abaixo da primeira.
  
12. Copie o conteúdo do arquivo ***filogenia1.fasta***, utilizado na Parte 1, para o final do arquivo ***filogenia2.fasta***.  
    Confira que cada cabeçalho `>` começa em uma **linha nova**: se a última linha de uma sequência ficar grudada no `>` seguinte, o MEGA vai juntar as duas sequências.
  
13. Repita as seções 2 e 3 da Parte 1 (alinhamento e árvore, com os mesmos parâmetros) para o arquivo ***filogenia2.fasta***. Enraíze a árvore no CRE2 e salve um print.  
    *Sem MEGA:* no notebook do Plano B ([AnaliseFilogenetica_PlanoB_Colab.ipynb](https://colab.research.google.com/github/grsart/BiomolComp/blob/main/Pratica6/AnaliseFilogenetica_PlanoB_Colab.ipynb)), cole as duas sequências na seção **Parte 2**. O notebook monta o filogenia2.fasta e faz os passos 12 e 13 automaticamente.
  
14. **Q13- Essas proteínas foram classificadas em quais famílias?**
  
15. **Q14- Verifique o valor de bootstrap dos ramos que agrupam cada uma das duas sequências à sua família. O agrupamento é confiável? Explique.**  
    *Referência usual:* valores de bootstrap ≥ 70% costumam ser considerados bom suporte para um ramo; valores abaixo de 50% indicam que o agrupamento não é sustentado pelos dados.
  
16. **Q15- Essas duas sequências vêm de um mesmo organismo.  
   Por que ficaram tão distantes uma da outra na árvore?  
   Qual a explicação biológica para isso?**   
