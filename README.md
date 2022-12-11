# Códigos do Trabalho de conclusão de curso de Eng. da Computação da Univesp


Alvaro Jhovaldo Lopez Ayme - 1813474 

Fabiano Santos de Oliveira – 1822525 

Luiz Carlos Canuto Santos - 1715868 

Marco Antônio Martins – 1712353 

Maria Selma Costa - 1715523 




A continuação vamos a detalhar os códigos que usamos para analisar os nossos dados.

* Integração do Colab com o Google Drive

```python
# Conectar com o drive da unesp
from google.colab import drive
drive.mount('/content/drive', force_remount=True)
```

* Importamos as librerias.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```


* Leitura dos dados, e armazenamento num dataframe

```python
df = pd.read_csv('/content/drive/My Drive/UNIVESP/tcc/dados.csv')
```


* Seleccionamos as variáveis que usaremos para o nosso estudo

```python
df_subset = df[["('P1_a ', 'Idade')", "('P1_b ', 'Genero')", "('P1_e_a ', 'uf onde mora')", "('P1_h ', 'Nivel de Ensino')", "('P2_a ', 'Qual sua situação atual de trabalho?')", "('P2_f ', 'Cargo Atual')", "('P2_h ', 'Faixa salarial')", "('P2_g ', 'Nivel')"]]
```


*

```python
uf_sudeste = df_subset_01[ (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'SP') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'MG') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'RJ') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'ES') ]



uf_sul     = df_subset_01[ (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'RS') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'PR') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'SC') ]


uf_norte   = df_subset_01[ (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'AC') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'AM') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'RO') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'PA') |                          
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'AP') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'TO') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'RR') ]

uf_noreste = df_subset_01[ (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'MA') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'PI') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'BA') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'CE') |                          
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'RN') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'PB') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'AL') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'SE') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'PE') ]

uf_centro =  df_subset_01[ (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'MT') | 
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'MS') |
                           (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'GO') ]

uf_df =  df_subset_01[ (df_subset_01["('P1_e_a ', 'uf onde mora')"]  == 'DF') ]
```


* Código para graficar a distribuição das idades em função do Estado do Brasil.

```python
df_subset_01 = df_subset[df_subset["('P1_e_a ', 'uf onde mora')"] != "Exterior"]

grouped = df_subset_01.loc[:,["('P1_e_a ', 'uf onde mora')", "('P1_a ', 'Idade')"]] \
    .groupby(["('P1_e_a ', 'uf onde mora')"]) \
    .median() \
    .sort_values(by="('P1_a ', 'Idade')")

sns.set(rc={'figure.figsize':(15,8.27)})
ax = sns.boxplot(x="('P1_e_a ', 'uf onde mora')", y="('P1_a ', 'Idade')", data=df_subset_01, order = grouped.index, color='#99c2a2')


plt.xlabel('UF', fontsize=26);
plt.ylabel('Idade (anos)', fontsize=26);
plt.tick_params(axis='both', which='major', labelsize=20)

plt.show()
```

* Código para graficar a distribuição do número de pessoas Masculinas ou Femininas em função do Estado do Brasil

```python

# Distribuição de genero por UF


df_subset_01 = df_subset[ (df_subset["('P1_b ', 'Genero')"] != "Outro") & (df_subset["('P1_e_a ', 'uf onde mora')"] != "Exterior")]


sns.set(rc={'figure.figsize':(15,8.27)})
ax = sns.catplot(
    data=df_subset_01, x="('P1_e_a ', 'uf onde mora')", col="('P1_b ', 'Genero')",
    kind="count", height=10, aspect=.8,
)

ax.set(xlabel='UF', ylabel='Número de pesssoas')


```

* 

```python
```

* 

```python
```

* 

```python
```