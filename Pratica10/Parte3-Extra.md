# Predição de ensemble conformacional para uma porção pequena de Proteína

Nesta seção da prática, iremos gerar um conjunto de 50 conformações distintas para a proteína do Sistema 2 da parte 2.  
Para isso, iremos utilizar um Google Colab de terceiros, já implementado para executar o algoritmo [BioEmu](https://www.science.org/doi/10.1126/science.adv9817)

1. Inicialmente, entre no seguinte [Google Colab](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/BioEmu.ipynb)
2. No campo **Sequence** insira a informação abaixo:
> LDNVATYAGQFNQDYLSGMAANMSGTFGGANMPNLYP


3. No campo **num_samples**, modifique o valor para 50
4. Clique no icone **Run all** ou **Executar tudo**
5. Na seção **Display Structures**, aparecerá uma barra deslizante, onde podem visualizar cada cluster.
    - Compare as estruturas geradas pelo BioEmu e as estruturas geradas pelo AlphaFold3, nas situações com uma e com seis cópias. Ambas foram geradas?  
    - Existe preferência para alguma estrutura secundária a ser gerada na sequência?
