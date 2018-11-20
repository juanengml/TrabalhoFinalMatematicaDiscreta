
<center><h1> Trabalho Prático de Matemática Discreta: Análise de Algoritmos de Ordenação </h1> </center>



| Membros | Nome                     |
|---------|--------------------------|
| 01      | Juan Manoel              |
| 02      | Robson Barreto             |
| 03      | Yang Jin Samara cavalari |
| 04      | Gustavo Jeromine         |
| 05      | Vladimir da Silva Borges |

### 1 - Introdução

Deve conter:(Vladimir e Robson)
* Uma breve descrição do objetivo do trabalho
* O que são algoritmos de ordenação, o que fazem, como funcionam, onde podem ser aplicados, importância etc
* Uma breve introdução aos algoritmos escolhidos


O trabalho a respeito de algoritmos de ordenação tem por objetivo principal a análise do código implementado, pontuando seus principais atributos relacionando volume de dados e tempo de execução, oque é muito comum no setor de análise de dados. Os resultados apresentados serão de cunho técnico e gráfico, mostrando a curva de variação no desempenho em cada tipo de algoritmo de ordenação.                                                                
Algoritmos de ordenação são métodos em termos de organização de código que tem por objetivo fazer  a ordenação de dados, ou seja, manipulam dados de uma sequência aleatória transformando-os em uma sequência ordenada decrescente, crescente, alfabética ou até mesmo falando em Orientação a Objeto, comparação de Objetos. Funcionam com uma repetição sistêmica dentro de um conjunto finito de elementos, comparando em  cada ciclo os dados de cada um, e trocando suas posições conforme for o objetivo do algoritmo. Podem ser aplicados em programas que frequentemente recebem uma grande quantidade de dados e por esse motivo necessitam de uma composição correta dos mesmos, para que eventualmente haja uma melhor performance do programa para executar a busca. 
Os algoritmos de ordenação tem grande importância no meio computacional, principalmente na área de programação por determinar muitas vezes o tempo de execução do programa em termos de alocação de dados, oque sempre foi um objetivo em comum entre os desenvolvedores.
O MERGE SORT que usa a estratégia de classificação, ordenação por partição (dividir e conquistar). O BUBLE SORT tem como característica percorrer o vetor por completo, comparando elementos adjacentes (dois a dois).


Objetivo:

Escrever uma análise descrevendo e comparando dois algoritmos de ordenação distintos.

Objetivos Específicos:

- Buscar por dois algoritmos distintos de ordenação na literatura.

- Descrever como funcionam, de onde surgiram, etc.

- Buscar na literatura pela complexidade assintótica no melhor e pior caso em notação Ozão ou Theta em relação ao tempo de execução/número de operações primitivas realizadas.

- Analizar as diferenças de complexidade entre os dois algoritmos e discutir a respeito da eficiência dos mesmos.




```python
from IPython.display import HTML
import time
```

### 2 - Descrição e Análise do Algoritmo 1

Deve conter:
* Descrição completa do primeiro algoritmo escolhido: nome, origem, estratégia usada, e como funciona
* Estrutura do algoritmo em pseudocódigo
* Citações para a descrição do algoritmo e pseudocódigo


##### Descrição completa do primeiro algoritmo escolhido: nome, origem, estratégia usada, e como funciona
<br>
<b>Nome: </b> Merge Sort
<br><br>
<b>Origem: </b> Existem evidências de que o algoritmo foi proposto por <b>John Von Neumann </b> em 1945. Essa discussão existe, por que ao estudar as várias contribuições que ele fez é, ao mesmo tempo, complexa e 
fascinante. Essa complexidade devesse em parte a existência de muitas fontes de
informação, algumas pouco é dificilmente acessíveis, outras discordantes entre si ou polêmicas. Outras contruibuições atribuem ao <b>Knuth</b>, que argumentou no seu livro ‘Arte de Programação
Computacional: Ordenando e Procurando’ que Von Neumann foi o primeiro a
descrever a idéia.
<br>
<br>
<b>Estratégia usada: </b>tenicas de classificação - Ordenação por partição(dividir e conquistar)
o mergesort é classificado como ordenação por partição, que parte do princípio de
"dividir para conquistar". Este princípio é uma técnica que foi utilizada pela primeira
vez por Anatolii Karatsuba em 1960 e consiste em dividir um problema maior em
problemas pequenos, e sucessivamente até que o mesmo seja resolvido diretamente.

<br><br>
<b>Como funciona: a técnica realiza-se em três fases.</b>

1) Divisão: o problema maior é dividido em problemas menores e os problemas menores obtidos são novamente divididos sucessivamente de maneira recursiva.

2) Conquista: o resultado do problema é calculado quando o problema é pequeno o suficiente.

3) Combinação: os resultados dos problemas menores são combinados até que seja obtida a solução do problema maior. Algoritmos que utilizam o método de partição são caracterizados por serem os mais rápidos dentre os outros algoritmos pelo fato de sua complexidade ser, na maioria das situações, O(nlogn). Os dois representantes mais ilustres desta classe são o quicksort e o mergesort



```python
print "Aplicação Merge Sort"
HTML('<img src="./merge.gif" style="width:200px;height:200px;" >')
```

    Aplicação Merge Sort





<img src="./merge.gif" style="width:200px;height:200px;" >



# Estrutura do algoritmo em pseudocódigo



<br>    
<b>MERGE-SORT(A, p, r)</b>

    if p < r then  
        q = ((p + r) / 2) //calcula o meio
        Merge-Sort(A, p, q)
        Merge-Sort(A, q + 1, r)
        Merge(A, p, q, r)

<b>Merge(A, p, q, r)</b>

    n1 = q - p + 1
    n2 = r - q
    sejam L[1 ... n1 + 1] e R[1 ... n2 + 1]
    for i = 1 to n1
        L[i] = A[p + i - 1]
    for j = 1 to n2
        R[j] = A[q + j]

    i = 1
    j = 1

    for k = p to r
        if L[i] <= R[j] then A[k] = L[i]
            i = i + 1
        else A[k] = R[j]
            j = j + 1
            
            


### Citações para a descrição do algoritmo e pseudocódigo
mergesort(A[0...n - 1], inicio, fim)
|   se(inicio < fim)
|   |   meio ← (inicio + fim) / 2 //calcula o meio
|   |   mergesort(A, inicio, meio) //ordena o subvetor esquerdo
|   |   mergesort(A, meio + 1, fim) //ordena o subvetor direito
|   |   merge(A, inicio, meio, fim) //funde os subvetores esquerdo e direito
|   fim_se
fim_mergesort

merge(A[0...n - 1], inicio, meio, fim)
|   tamEsq ← meio - inicio + 1 //tamanho do subvetor esquerdo
|   tamDir ← fim - meio //tamanho do subvetor direito
|   inicializar vetor Esq[0...tamEsq - 1]
|   inicializar vetor Dir[0...tamDir - 1]
|   para i ← 0 até tamEsq - 1
|   |   Esq[i] ← A[inicio + i] //elementos do subvetor esquerdo
|   fim_para
|   para j ← 0 até tamDir - 1
|   |   Dir[j] ← A[meio + 1 + j] //elementos do subvetor direito
|   fim_para
|   idxEsq ← 0 //índice do subvetor auxiliar esquerdo
|   idxDir ← 0 //índice do subvetor auxiliar direito
|   para k ← inicio até fim
|   |   se(idxEsq < tamEsq)
|   |   |   se(idxDir < tamDir)
|   |   |   |   se(Esq[idxEsq] < Dir[idxDir])
|   |   |   |   |   A[k] ← Esq[idxEsq]
|   |   |   |   |   idxEsq ← idxEsq + 1
|   |   |   |   senão
|   |   |   |   |   A[k] ← Dir[idxDir]
|   |   |   |   |   idxDir ← idxDir + 1
|   |   |   |   fim_se
|   |   |   senão
|   |   |   |   A[k] ← Esq[idxEsq]
|   |   |   |   idxEsq ← idxEsq + 1
|   |   |   fim_se
|   |   senão
|   |   |   A[k] ← Dir[idxDir]
|   |   |   idxDir ← idxDir + 1
|   |   fim_se
|   fim_para
fim_merge
<h4><b><i>" Observe que o método merge utiliza dois vetores auxiliares. A utilização desses vetores faz com o Merge Sort tenha complexidade O(n) no espaço.

Por causa da cópia de elementos entre os vetores auxiliares e o vetor A, a complexidade no tempo do método merge é Θ(n) ou O(n).

Alternativamente, podemos utilizar um único vetor auxiliar na ordenação, porém a complexidade no tempo e no espaço será a mesma. "</i></b></h4>
[1] CORMEN, T. H. et al. Algoritmos: teoria e prática. 3 ed. Rio de Janeiro: Elsevier, 2012.

---

#### Codigo python


```python
def merge(llist, rlist):
        final = []
        while llist or rlist:
                if len(llist) and len(rlist):
                        if llist[0] < rlist[0]:
                                final.append(llist.pop(0))
                                
                        else:
                                final.append(rlist.pop(0))
                                 

                if not len(llist):
                                if len(rlist):
                                      final.append(rlist.pop(0))
                                       

                if not len(rlist):
                                if len(llist): 
                                      final.append(llist.pop(0))

        return final

def merge_sort(list):
        if len(list) < 2: return list
        mid = len(list) / 2
        return merge(merge_sort(list[:mid]), merge_sort(list[mid:]))
```

### 3 - Descrição e Análise do Algoritmo 2

Deve conter:
* Descrição completa do segundo algoritmo escolhido: nome, origem, estratégia usada, e como funciona
* Estrutura do algoritmo em pseudocódigo
* Citações para a descrição do algoritmo e pseudocódigo

<b> Descrição completa do segundo algoritmo escolhido: nome, origem, estratégia usada, e como funciona </b>

<b>Nome: </b> Bubble Sort<br><br>
<b>Origem: </b> Origem Não Achei <br><br>
<b>Estrategia Usada: </b>
 é o algoritmo de ordenação mais simples que funciona trocando repetidamente os elementos adjacentes se eles estiverem na ordem errada.<br><br>
<b>Como funciona: </b> 
Percorre o vetor inteiro comparando
elementos adjacentes (dois a dois) a estrategia de trocar as posições dos elementos se eles estiverem fora de ordem o repita os dois passos acima com os primeiros n-1 itens, depois com os primeiros n-2 itens, até que reste apenas um item <br><br>




```python
print "Aplicação Bubble Sort"
HTML('<img src="./Bubble.gif" style="width:200px;height:200px;" >')
```

    Aplicação Bubble Sort





<img src="./Bubble.gif" style="width:200px;height:200px;" >



### Estrutura do algoritmo em pseudocódigo


procedure bubbleSort( A : lista de itens ordenaveis ) defined as:
  do
    trocado := false
    for each i in 0 to length( A ) - 2 do:
      // verificar se os elementos estão na ordem certa
      if A[ i ] > A[ i + 1 ] then
        // trocar elementos de lugar
        trocar( A[ i ], A[ i + 1 ] )
        trocado := true
      end if
    end for
  // enquanto houver elementos sendo reordenados.
  while trocado
end procedure
---
#### Codigo Python 


```python
def bubble_sort(lista):
   elementos = len(lista)-1
   ordenado = False
   while not ordenado:
        ordenado = True
        for i in range(elementos):
             if lista[i] > lista[i+1]:
                 lista[i], lista[i+1] = lista[i+1],lista[i]
                 ordenado = False        
                 #print(lista)
   return lista
```

### 4 - Análise Assintótica Comparativa

Deve conter:
* Representação em Ozão ou Theta da complexidade do algoritmo 1 no melhor e pior caso em relação ao tempo de execução
* Representação em Ozão ou Theta da complexidade do algoritmo 2 no melhor e pior caso em relação ao tempo de execução
* Discussão a respeito de qual algoritmo é o mais eficiente


<center><h4>Complexidade Algoritmo 1 Merge</h4></center>

| Caso    | Analise Assintótica            | Tempo Execução   |
|---------|--------------------------------|------------------|
| Melhor  |       O(n log base 2 n)        | 0.000979900360107 | 
| Pior    |       O(n log base 2 n)        | 0.0190689563751   |



```python
m = merge_sort(Metrica_merge)
print "Melhor Caso: ",m[0]
print "Pior Caso: ",m[-1]
```

    Melhor Caso:  0.000979900360107
    Pior Caso:  0.0190689563751


<center><h4>Complexidade Algoritmo 2 Bubble</h4></center>

| Caso    | Analise Assintótica            | Tempo de Execução |
|---------|--------------------------------|-------------------|
| Melhor  |       O(n²)                    | 0.000216007232666 |
| Pior    |       O(n²)                    | 0.00135803222656  | 



```python
m = bubble_sort(Metrica_bubble)
print "Melhor Caso: ",m[0]
print "Pior Caso: ",m[-1]
```

    Melhor Caso:  0.000216007232666
    Pior Caso:  0.00135803222656


### Discussão a respeito de qual algoritmo é o mais eficiente

Bubble sort por ser uma função quadrática começa a rodar mais rapidamente enquanto o merge sort é uma função log-linear na base 2 e demora mais, ou seja é mais lento. Enquanto a sua estabilidade ao longo do tempo o merge sort é mais recomendado pois é estável.

O Bubble sort no melhor caso ele rodou em 0,00021 de segundos e no pior caso em 0,00135. O merge sort no melhor caso ele rodou em 0,00097 de segundos e no pior caso ele rodou em 0,01906 de segundos.

Segundo o Professor Moacir Ponti Jr. do Instituto de Ciências Matemáticas e de Computação da USP, o algoritmo bubble sort consome muito tempo quando todos os itens estão ordenados.

### 5 - Análise Experimental Opcional

Esta seção opcional deve conter:
* A descrição da configuração da análise experimental conduzida: implementação utilizada, configurações da máquina utilizada, tamanhos de entrada utilizados, tipo de dados usados como entrada, e método utilizado de quantificação de tempo/operações primitivas.
* Gráfico comparando ambas curvas de desempenho obtidas pelos algoritmos de ordenação escolhidos.



#### Valores de Test 


```python
from random import shuffle
import threading
import time
```


```python
x0 = range(100)     # 0
x1 = range(500)     # 1
x2 = range(1000)    # 2
x3 = range(1500)    # 3 
x4 = range(2500)   # 4 
x5 = range(3000)   # 5
x6 = range(35000)   # 6
x7 = range(40000)  # 7 
test = [x0,x1,x2,x3,x4,x5,x6,x7]
```


```python
for p in range(len(test)):
    shuffle(test[p])
```


```python
def Metrica_Bubble():
 data = []
 for p in range(len(test)):
    ini = time.time()
    bubble_sort(test[p])
    fim = time.time()
    print "\n",p,"[Bubble] \t\n Tempo de Execução: ",fim-ini
    tempo = fim-ini 
    data.append(tempo)
 return data  

def Metrica_Merge():
 data = []
 for p in range(len(test)):
    ini = time.time()
    merge_sort(test[p])
    fim = time.time()
    print "\n",p,"[Merge] \t\n Tempo de Execução: ",fim-ini
    tempo = fim-ini 
    data.append(tempo)
 return data  

```

###  "Rodando Metricas com Mult-thread"


```python
t = threading.Thread(target=Metrica_Bubble,)
t2 = threading.Thread(target=Metrica_Merge,)
t.start()
t2.start()
```

    
    0 [Merge] 	
     Tempo de Execução:  0.00234603881836
    
    1 [Merge] 	
     Tempo de Execução:  0.00824189186096
    
    2 [Merge] 	
     Tempo de Execução:  0.0161800384521
    
    0 [Bubble] 	
     Tempo de Execução:  0.045725107193
    
    3 [Merge] 	
     Tempo de Execução:  0.0324440002441
    
    4 [Merge] 	
     Tempo de Execução:  0.0396988391876
    
    5 [Merge] 	
     Tempo de Execução:  0.0295140743256
    
    1 [Bubble] 	
     Tempo de Execução:  0.126824140549
    
    6 [Merge] 	
     Tempo de Execução:  0.540427923203
    
    7 [Merge] 	
     Tempo de Execução:  0.719171047211
    
    2 [Bubble] 	
     Tempo de Execução:  1.25040483475
    
    3 [Bubble] 	
     Tempo de Execução:  0.215059995651
    
    4 [Bubble] 	
     Tempo de Execução:  0.574501991272
    
    5 [Bubble] 	
     Tempo de Execução:  0.72434592247
    
    6 [Bubble] 	
     Tempo de Execução:  96.4967339039
    
    7 [Bubble] 	
     Tempo de Execução:  126.438951015


### Metricas sem Mult-thread


```python
Metrica_bubble = Metrica_Bubble()
Metrica_merge = Metrica_Merge()
```

    
    0 [Bubble] 	
     Tempo de Execução:  0.000216007232666
    
    1 [Bubble] 	
     Tempo de Execução:  0.000945091247559
    
    2 [Bubble] 	
     Tempo de Execução:  0.000577211380005
    
    3 [Bubble] 	
     Tempo de Execução:  0.000468015670776
    
    4 [Bubble] 	
     Tempo de Execução:  0.000679016113281
    
    5 [Bubble] 	
     Tempo de Execução:  0.000565052032471
    
    6 [Bubble] 	
     Tempo de Execução:  0.000970840454102
    
    7 [Bubble] 	
     Tempo de Execução:  0.00135803222656
    
    0 [Merge] 	
     Tempo de Execução:  0.000979900360107
    
    1 [Merge] 	
     Tempo de Execução:  0.00390791893005
    
    2 [Merge] 	
     Tempo de Execução:  0.0108478069305
    
    3 [Merge] 	
     Tempo de Execução:  0.013839006424
    
    4 [Merge] 	
     Tempo de Execução:  0.0141232013702
    
    5 [Merge] 	
     Tempo de Execução:  0.0141110420227
    
    6 [Merge] 	
     Tempo de Execução:  0.0157148838043
    
    7 [Merge] 	
     Tempo de Execução:  0.0190689563751


### Plot Grafico de Desempenho Merge Sort


```python
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```


```python
plt.plot(Metrica_merge)
plt.ylabel('Merge Sort')
plt.show()
```


![png](output_42_0.png)


### Plot Grafico de Desempenho bubble sort


```python
plt.plot(Metrica_bubble)
plt.ylabel('bubble sort')
plt.show()
```


![png](output_44_0.png)


### 6 - Referências

Esta seção deve conter uma linha para cada referência utilizada. Exemplo:

Lee, J., & Yeung, C. Y. (2018). Personalizing Lexical Simplification. In Proceedings of the 27th International Conference on Computational Linguistics.
Mancini, P. (2011). Leader, president, person: Lexical ambiguities and interpretive implications. European Journal of Communication, 26(1).
Saggion, H. (2018). LaSTUS/TALN at Complex Word Identification (CWI) 2018 Shared Task. In Proceedings of the Thirteenth Workshop on Innovative Use of NLP for Building Educational Applications

MERGESORT - https://www.ft.unicamp.br/liag/siteEd/includes/arquivos/MergeSortResumo_Grupo4_ST364A_2010.pdf

Merge Sort - https://pt.slideshare.net/dianacarolinatarapueschirivi/merge-sort-25398213

bubble sort - http://www2.dcc.ufmg.br/disciplinas/aeds2_turmaA1/bubblesort.pdf

https://edisciplinas.ups.br/pluginfile.php/2223654/mod_resource/content/1/ICC2_ordenacao_parte1.pdf

https://www.ufrj.brb/jairo_souza/files/2009/12/2-Ordena%C3%A7%C3%A3o-BubbleSort.pdf

