# Tipos de dados

Em Python todo valor tem um tipo de dado. Quando criamos uma variável e atruímos um valor a ela, estamos definindo qual o tipo de dados que a mesma vai ter.

Existem diversos tipos de dados em Python, mas os que vamos utilizar com mais frequência podemos dividir da seguinte forma:

* Booleanos: Verdadeiro ou Falso
* Númericos: Inteiros, Ponto flutuante, Fração e números complexos
* Strings
* Listas
* Tuplas
* Sets
* Dicionários

## Booleanos

Valores booleanos podem ser Verdadeiro (True) ou Falso (False). Geralmente usamos os valores booleanos para verificar condições.

Podemos atribuir valores booleanos diretamente as nossas variáveis ou obtê-los apartir de uma comparação entre dois valores:

```python
# Atribuindo valor booleano
verdadeiro = True
if verdadeiro:
  print('O valor é True')
else:
  print('O valor é False')
  
# Obtendo apartir de uma comparação
e_maior = 10 > 2
if e_maior:
  print('O número é maior')
```

## Numéricos

Os valores númericos em Python são muito diversos, podemos representar números inteiros, ponto flutuante, frações e números complexos. O interpretador se encarrega de definir o tipo númerico que melhor representa o valor atribuído a variável.

```python
my_value = 1
print(type(my_value))
>>> <class 'int'>

my_value = 1.0
print(type(my_value))
>>> <class 'float'>

my_value = complex(1, 45)
print(type(my_value))
>>> <class 'complex'>

import fractions
my_value = fractions.Fraction(1, 3)
print(type(my_value))
>>> fractions.Fraction

# Conversão de números
int(1.56)
>>> 1

float(9)
>>> 9.0

100 + 10.0
>>> 110.0

int(100 + 10.0)
>>> 110
```

## Strings

Todo valor que está "empacotado" por aspas simples ou duplas é considerado uma String (str) em Python. 

```python
my_name = 'Guilherme'
print(type(my_name))
>>> <class 'str'>
```

## Listas, Tuplas, Sets e Dicionários

Esses são tipos de dados mais avançados, e teremos um capítulo para fazer só deles. Apesar de serem muito ricos, fazer o uso desses tipos é muito simples.

```python
# listas
my_list = [1, 2, 3]
print(type(my_list))
>>> <class 'list'>

# tuplas
my_tuples = (1, 2, 3,)
print(type(my_tuples))
>>> <class 'tuple'>

# sets
my_set = set('guilherme')
print(type(my_set))
>>> <class 'set'>

# dicionários
my_dict = {'name': 'Guilherme', 'age': 23}
print(type(my_dict))
>>> <class 'dict'>
```

