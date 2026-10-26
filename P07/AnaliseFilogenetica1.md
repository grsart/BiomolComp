# Análise Filogenética de Sequências – Parte 1
Nesta atividade iremos realizar a análise filogenética do domínio transcriptase reversa de retrotransposons do tipo non-LTR.   
Este tipo de elemento transponível pode ser classificado em diversas famílias baseado na evolução do seu domínio da transcriptase reversa.  
O objetivo desta atividade é realizar a classificação de retrotransposons problemas em relação a estas famílias.  

> **Objetivos desta parte:** construir um alinhamento múltiplo de proteínas, inferir uma árvore por Neighbor-Joining com bootstrap, enraizar a árvore com um grupo externo (*outgroup*) e classificar sequências desconhecidas.  
> **Tempo estimado:** 60 minutos (com o MEGA já instalado).  
> **O que entregar:** respostas das questões Q1 a Q9; print da árvore **sem raiz definida** (seção 4, passo 2) e print da árvore **enraizada** (seção 4, passo 6).

A atividade completa tem três partes: **Parte 1** (este arquivo, MEGA), **Parte 2** (classificação de duas proteínas obtidas no NCBI) e **Parte 3** (notebook no Google Colab). As questões são numeradas em sequência ao longo das três partes (Q1 a Q19).

## 1- Programa MEGA
**O MEGA deve ser instalado antes da aula.** Servem as versões MEGA11 ou MEGA12 (a mais recente); os menus usados nesta prática são os mesmos nas duas.  
Verifique se o MEGA está instalado no computador. Se sim, abra o programa e pule para o tópico 2.  
Caso não esteja, siga o roteiro de instalação do **Anexo A**, no final deste arquivo.

> **Sem MEGA? Use o Plano B.** Se o MEGA não estiver instalado e não for possível instalá-lo (por exemplo, sem permissão de administrador ou sem a máquina virtual), faça as Partes 1 e 2 no Google Colab, com o notebook [AnaliseFilogenetica_PlanoB_Colab.ipynb](https://colab.research.google.com/github/grsart/BiomolComp/blob/main/Pratica6/AnaliseFilogenetica_PlanoB_Colab.ipynb). Ele tem as mesmas questões (Q1 a Q15) e só precisa de um navegador e de uma conta Google.

## 2- Análise de alinhamento
1. Realize o download do arquivo [filogenia1.fasta](https://raw.githubusercontent.com/grsart/BiomolComp/refs/heads/main/P07/filogenia1.fasta) e salve em uma pasta no seu disco (clique com o botão direito no link e escolha **Salvar link como...**). Confira se o arquivo salvo tem extensão `.fasta` e começa com a linha `>L1Mouse`.  
      O arquivo contém as sequências do domínio de transcriptase reversa (RT) que usaremos na nossa análise.  
      A primeira etapa será gerar um alinhamento múltiplo destas sequências.

2. Com o programa MEGA aberto, clique em **Align** > **Edit/Build Alignment**  
  
3. Uma nova janela se abrirá. Clique em **Retrieve Sequences from File**
  
4. Selecione o arquivo baixado no passo 2.1 (filogenia1.fasta)
  
5. **Q1- São quantas sequências? As sequências possuem o mesmo tamanho? Elas estão alinhadas? Se sim, como está o alinhamento?**
  
6. Vamos (re)alinhar as sequências. Clique em **Alignment** > **Align by ClustalW**  
   Selecione a opção *OK* para a pergunta de selecionar todas as sequências
  
7. Defina os valores de **Gap Opening Penalty** para 5.0 e os valores de **Gap Extension Penalty** para 0.1 (nos campos de alinhamento múltiplo). Clique em OK.  
   *Por que esses valores?*   
   *(Opcional)* Refaça o alinhamento com os valores padrão e compare a região dos motivos conservados.
  
8. **Q2- Os motivos conservados da imagem abaixo estão presentes no alinhamento obtido?**  
   *Dica:* procure no alinhamento a sequência **FADD** nas sequências L1 (variação do motivo catalítico YADD da transcriptase reversa) e o motivo **QG...SP** que aparece algumas posições antes. A partir deles, localize os demais motivos da figura.
  
  <img width="800" height="600" alt="Motivos conservados do domínio de transcriptase reversa" src="https://github.com/user-attachments/assets/7b45e116-51c7-4695-9509-816c4ecd9929" />

  
9. Exporte o alinhamento: Vá em **Data**, clique em **Export alignment** e então **MEGA format**. Salve como **filogenia1.meg**.
  
10. Feche a janela de alinhamento
  
## 3- Construção da árvore filogenética
1. Na janela principal do MEGA, clique no ícone **Phylogeny** e depois em **Construct/Test Neighbor-Joining Tree**.
  
2. Se aparecer a pergunta sobre usar os dados ativos (*active data*), clique em **Cancel** (vamos abrir o arquivo exportado).
  
3. Se aparecer a pergunta sobre salvar a sessão, clique em **Close without saving**
  
4. Selecione o arquivo **filogenia1.meg** salvo no passo 2.9
  
5. Na janela de opções da análise, configure **exatamente** os parâmetros abaixo (assim todos obtêm a mesma árvore):

   | Campo | Valor |
   |---|---|
   | Test of Phylogeny | **Bootstrap method** |
   | No. of Bootstrap Replications | **100** |
   | Substitutions Type | Amino acid |
   | Model/Method | **Jones-Taylor-Thornton (JTT) model** |
   | Rates among Sites | Uniform rates |
   | Gaps/Missing Data Treatment | **Pairwise deletion** |

   **Q3- Qual a importância de selecionar o teste de bootstrap em relação à opção padrão (None)? O que significa o número que aparece em cada ramo?**
  
6. Clique em OK e espere gerar a árvore filogenética (cerca de 1 minuto)

  
## 4- Análise da árvore filogenética
  
1. **Q4- A árvore está enraizada? Se sim, qual é a raiz?**  
  
2. Salve uma imagem desta árvore.
  
3. **Q5- Olhando a árvore, onde você acha que a raiz deveria estar? Que informação você precisaria para decidir?**
  
4. Vamos definir um enraizamento a partir de uma informação conhecida.  
   Sabe-se que o transposon CRE2 representa a primeira família a se divergir das outras.  
   **Q6- Essa informação é suficiente para definir essa família como a raiz da árvore? Explique utilizando o conceito de grupo externo (*outgroup*).**  
  
5. Para definir o enraizamento, selecione **Subtree** no menu do lado esquerdo da tela e clique em **Root**. Em seguida clique no ramo que leva ao CRE2.
  
6. Salve uma imagem da árvore enraizada.  
   **Q7- O que mudou ao fazer o enraizamento? A topologia (quem agrupa com quem) mudou? E a interpretação da árvore?**
  
7. Compare a árvore obtida com a árvore de referência abaixo. Cada clado na figura representa uma família distinta (por exemplo L1, RTE, R2, R4, CR1, Jockey, I, R1, Tad1 e CRE).
  
8. **Q8- Os membros na árvore da prática estão agrupados da mesma forma que na figura abaixo? Indique as diferenças e verifique o valor de bootstrap dos ramos que diferem.**
  
9. **Q9- A partir da árvore obtida, os elementos z82275, pido e Sr1 fazem parte de qual família? Justifique usando a topologia e os valores de bootstrap.**

<img width="900" height="1200" alt="Árvore de referência das famílias de retrotransposons non-LTR" src="https://github.com/user-attachments/assets/725c6933-9a62-4def-9b12-8ca432e5e5a7" />

---

## Anexo A – Instalação do MEGA
O MEGA tem versões para Windows, macOS e Linux. Nos computadores do laboratório, use a máquina virtual Windows ou, se disponível, a versão Linux.

1. Se for usar Windows: na janela de busca, digite Win para encontrar a máquina virtual Windows e abra a máquina virtual
2. Entre no site do software MEGA ([aqui](https://www.megasoftware.net/))
3. Selecione as opções abaixo  
   *a. Sistema operacional (Windows ou Linux)*  
   *b. Graphical (GUI)*  
   *c. MEGA12 (64 bits)* ou MEGA11, se a versão 12 não estiver disponível  
4. Clique em Download  
5. Aceite os termos  
6. Faça o cadastro  
7. Baixe o arquivo  
8. Instale o arquivo nas configurações padrão  
9. Após esse passo, deve-se ter o programa instalado. Abra o programa MEGA  
