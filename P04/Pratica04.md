# Pratica 4 - Predição de propriedades em sequências de proteínas

Na aula de hoje, iremos predizer uma série de propriedades de proteínas para cinco sequências selecionadas.  

-> O objetivo, ao final da prática, é classificar as proteínas em:  
1. Completamente estruturada
2. Completamente desestruturada
3. Parcialmente desestruturada
4. Proteína transmembrana
5. Proteína single pass em membrana

## Sequências das proteínas a serem utilizadas
O arquivo FASTA contendo as cinco sequências se encontra [aqui](https://raw.githubusercontent.com/grsart/BiomolComp/refs/heads/main/Pratica4/proteins.fasta)

## Parte 1: Cálculo de propriedades físicas e químicas
Nesta parte da prática, será utilizado o servidor [ProtParam](https://web.expasy.org/protparam/)
1. Abra o link acima
2. Insira uma sequência por vez no campo designado e submeta ao servidor
3. Analise os resultados
4. **Q1**: Para cada uma das proteínas, é possível extrair alguma informação sobre ser proteína de membrana ou desestruturada?  
   Essa proteína é estável?  
   Quais são os aminoácidos mais presentes e menos presentes?  
   Qual é a hidropaticidade da proteína? O que isso sugere?  

## Parte 2: Cálculo de estrutura secundária
1. Para essa parte, o aluno deverá realizar o download do arquivo [PredictSS_embed_ProtT5.ipynb](https://colab.research.google.com/github/grsart/BiomolComp/blob/main/P04/PredictSS_embed_ProtT5.ipynb)
2. Em um Google Colab, carregue o arquivo baixado
3. Execute todas as células clicando no botão 'run all'
4. Ao final da página, deverá aparecer o resultado final para todas as 5 proteínas
5. Salve os arquivos de output no seu computador para uma visualização integrada futura
6. **Q2**: O que significam as letras H, L e E que aparecem no resultado final? No segundo arquivos, temos D e O. O que significam?  
      É possível antecipar alguma informação com relação a porções transmembranares e regiões desestruturadas?  
      Todas as proteínas são passíveis de terem domínios bem estruturados?  

## Parte 3: Predição de regiões transmembranares
1. Nesta parte da prática, o aluno deverá acessar o [google colab](https://colab.research.google.com/github/grsart/BiomolComp/blob/main/P04/Pratica4_TMbed_short.ipynb) referente à predição de regiões transmembranares
2. Execute todas as células por meio do botão 'run all'
3. Salve os arquivos de output no seu computador para uma visualização integrada futura
4. **Q3**: Quantas destas proteínas são preditas de terem regiões transmembranares?  
       Quantas proteínas são single pass e quantas são transmembranares? Justifique  
       Para essas proteínas, a predição de estrutura secundária obtida na **parte 2** está consistente com as regiões transmembranares?  
       Caso haja uma proteina de passagem única pela membrana, ela pode ter um domínio estruturado?  
       Este domínio estaria no interior ou no exterior da célula? Justifique  

## Parte 4: Predição de regiões intrisecamente desestruturadas
1. Entre no servidor [Adopt](https://adopt.peptone.io/)
2. Cole o conteúdo do [arquivo fasta](https://raw.githubusercontent.com/grsart/BiomolComp/refs/heads/main/Pratica4/proteins.fasta) no servidor
3. **Q4**: Quais informações podem ser tiradas daí?  
       Existem proteínas completamente desestruturadas? Quais?  
       E proteínas completamente estruturadas? Quais?  
       Quantas proteínas possuem regiões estruturadas e outras desestruturadas? Quais? Como chegou a essa conclusão?  
4. Refine a visualização. Faça a predição para cada proteína isoladamente. O que acontece?  

## Parte 5: Predição de domínio e função
1. Entre no servidor [CD-search](https://www.ncbi.nlm.nih.gov/Structure/bwrpsb/bwrpsb.cgi)
2. Cole todo o conteúdo do arquivo [arquivo fasta](https://raw.githubusercontent.com/grsart/BiomolComp/refs/heads/main/Pratica4/proteins.fasta) no campo correspondente
3. Execute a análise
4. Salve o arquivo hitdata.txt (Download data > Download)
5. **Q5**. Para cada uma das proteínas, responda  
   Qual a função predita?  
   Espera que essa função esteja vinculada a uma proteína de membrana? Isso se confirma com as outras predições?  
   Para aquelas proteínas que tiveram regiões desestruturadas, como é a predição de domínios para elas? Existe alguma menção sobre regiões desestruturadas?  
   Existe alguma proteína com múltiplos domínios preditos?  


## Parte 6: Visão unificada
1. Entre no Colab de [visualização](https://colab.research.google.com/drive/1FFLDEtrinHKTGJYYLNUI7MYWFD9wPVrG)
2. Execute a primeira célula e carregue os arquivos salvos nas partes anteriores

**Q6**: Para cada proteína, a classificação final foi unânime entre todas as ferramentas utilizadas, ou houve algum caso em que diferentes métodos apontaram para conclusões distintas? Se houve discordância, qual evidência você priorizou para decidir a classificação final, e por quê?

  
