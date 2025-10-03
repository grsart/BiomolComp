# Análise Filogenética de Sequências
Nesta atividade iremos realizar a análise filogenética do domínio transcriptase reversa de retrotransposons do tipo non-LTR.   
Este tipo de elemento transponível pode ser classificado em diversas famílias baseado na evolução do seu domínio da transcriptase reversa.  
O objetivo desta atividade é realizar a classificação de retrotransposons problemas em relação a estas famílias.  

## Atividade 1  
### 1- Verificação de existência de programa Mega instalado
a. Verifique se o programa MEGA11 está disponível está instalado no computador. Se sim, abra o programa e pule para o tópico 2.   
    Senão faça os passos abaixo  
      
b. Na janela de busca, digite Win para encontrar a máquina virtual Windows. Abra a máquina virtual
c. Entre no site do software MEGA ([aqui](https://www.megasoftware.net/))
d. Selecione as opções abaixo  
   *a. Windows*  
   *b. Graphical (GUI)*  
   *c. MEGA11 (64 bits)*  
     
e. Clique em Download  
f. Aceite os termos  
g. Faça o cadastro  
h. Baixe o arquivo  
i. Instale o arquivo nas configurações padrão  
j. Após esse passo, deve-se ter o programa instalado na máquina virtual do Windows. Abra o programa MEGA11  

### 2- Análise de alinhamento
1. Realize o download do arquivo [filogenia1.fasta](https://github.com/grsart/BiomolComp/blob/main/Pratica6/filogenia1.fasta) e salve em uma pasta no seu disco.
      O arquivo contém um conjunto de sequências que usaremos na nossa análise.  
      A primeira etapa será gerar um alinhamento múltiplo destas sequências.

2. Com o programa MEGA11 aberto, clique em **Align** > **Edit/Build Alignment**  
  
3. Uma nova janela se abrirá. Clique em **Retrieve Sequences from File**
  
4. Selecione o arquivo baixado no ponto 2.1 (filogenia1.fasta)
  
5. **Q1- São quantas sequências? As sequências possuem o mesmo tamanho? Elas estão alinhadas? Se sim, como está o alinhamento?**
  
6. Vamos (re)alinhar as sequências. Clique em **Alignment** > **Align by ClustalW**
   Selecione a opção *OK* para a pergunta de selecionar todas as sequências
  
7. Defina os valores de Gap Opening Penalty para 5.0 e os valores de Gap Extension Penalty para 0.1. Clique em OK.
  
8. **Q2- Os motivos conservados da imagem abaixo estão presentes no alinhamento obtido?**
  
  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/7b45e116-51c7-4695-9509-816c4ecd9929" />

  
9. Exporte o alinhamento: Vá em **Data**, clique em **Export alignment** e então **Mega format**
  
10. Feche a janela de alinhamento
  
### 3- Construção da árvore filogenética
1. Na janela principal do MEGA11, clique no ícone **Phylogeny** e depois em **Construct/Test Neighbor-joining tree.**
  
2. Se perguntar para usar o dado ativo, clique em **cancel**
  
3. Se perguntar para salvar a seção, clique em **Close without saving**
  
4. Selecione o arquivo filogenia1.meg salvo no tópico 2.10
  
5. No campo **Test of Phylogeny**, selecione a opção **Bootstrap method**  
    **Q3- Qual a importância de selecionar esta opção em relação à opção padrão?**
  
6. Clique em OK e espere gerar a árvore filogenética

  
### 4- Análise da árvore filogenética
  
1. **Q4- A árvore está enraizada? Se sim, qual é a raiz?**
  
2. Salve um print desta árvore.
  
3. Vamos definir um enraizamento a partir de uma informação conhecida.
       Sabe-se que o transposon CRE2 representa a primeira família a se divergir das outras.  
   **Q5- Essa informação é suficiente para definir essa família como a raíz da árvore?  
         Explique utilizando o contexto de outgroup**  
  
4. Para definir um enraizamento, selecione **SubTree** no menu ao lado esquerdo da tela e então a opção clique em **Root Tree**
  
5. Selecione o ramo adjacente ao CRE2  
   **Q6- O que mudou ao fazer o enraizamento?**
  
6. Compare a árvore obtida com a árvore abaixo. Cada clado na figura abaixo representa uma família distinta.
  
7. **Q7- Os membros na árvore da prática estão agrupados da mesma forma que na figura abaixo?**
  
8. **Q8- A partir da árvore obtida, os membros Z82275 e pido fazem parte de qual família? Justifique**

<img width="900" height="1200" alt="image" src="https://github.com/user-attachments/assets/725c6933-9a62-4def-9b12-8ca432e5e5a7" />

