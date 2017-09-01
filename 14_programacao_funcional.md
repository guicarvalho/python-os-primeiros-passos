# Programação Funcional

Programação funcional é um paradigma que trata a computação como uma avaliação de funções matemáticas. Tais funções podem ser aplicadas em sequências de dados (geralmente listas). São exemplos de linguagens funcionais: LISP, Scheme e Haskell (esta última influenciou o projeto do Python de forma marcante). As operações básicas do paradigma funcional são implementadas no Python pelas funções builtin *map(), filter(), reduce()* e *zip()*. (Retirado do livro: Python para desenvolvedores v2)

## Lambda

Python possui funções anônimas, ou seja, funções sem nome que são definidas inline e podem ser atribuidas a variáveis. Com isso podemos executar funções sem declarar as mesmas do jeito convêncinal. O uso de lambdas deve ser controlado, pois elas podem “sujar” o código.

```python
a = lambda x: x * 2
print(a)
print(a(2))
```

## Filter

Podemos aplicar uma função para filtrar os valores de nossos objetos iteráveis como: listas, tuplas e strings. A função *filter* pede dois parâmetros: 

1. Função: Será executada recebendo item a item como parâmetro. A função deve retornar um *bool*, se o retorno for *False* o item será removido da lista gerada. 
2. Iterável que desejamos filtrar.

```python
func = lambda x: x.lower() in ['java', 'python', 'c#']
langs = ['Python', 'Java', 'Cobol', 'Lisp', 'C++', 'C#', 'Ruby']
print(list(filter(func, langs)))

msg = list(filter(lambda x: x not in ['a','e','i','o','u'], 'Eu gosto de programar em Python.'))
print(msg)
print(''.join(msg))
```

## Map

A função *map* pede dois parâmetros:

1. Função: Será executada recebendo item a item como parâmetro. A função retorna o item modificado.
2. Iterável que desejamos modificar.

Ao final da execução será retornada uma nova lista de objetos com os valores modificados pela função.

```python
result = list(map(lambda x: x.upper(), 'guilherme@gmail.com'))
print(result)
```

## Reduce

Redução significa aplicar uma função que recebe dois parâmetros, nos dois primeiros elementos de uma sequência, aplicar novamente a função usando como parâmetros o resultado do primeiro par e o terceiro elemento, seguindo assim até o final da sequência. O resultado final da redução é apenas um elemento. (texto retirado do livro: Python para desenvolvedores v2)

```python
from functools import reduce

f = lambda x, y: x if x > y else y
result = reduce(f, [45, 12, 34, 281, 90, 1])
print(result)
```

## Zip

A função *zip* tem um funcionamento muito interessante, ela retorna uma lista de tuplas. As *tuplas* são formadas apartir das sequências que foram passadas por parâmetro. Vamos supor que passamos duas sequências e cada uma contêm 3 elementos, então a função irá retornar uma lista com três *tuplas*. A primeira *tupla* da lista é formada pelo elemento da posição zero do array um e array dois, a segunda tupla é formada pelo segundo elemento do array um e array dois e a última tupla é formada pelo terceiro elemento do array um e dois.

```python
result = zip('ABCD', '1234')
print(list(result))
```

## List Comprehension

De uma forma bem simples podemos dizer que compreensão de listas é um recurso onde podemos gerar uma lista através de um for inline. Comprimir listas pode ser feito usando vários for's e fazendo condições com if para avaliar se o elemento deve ou não estar na lista gerada. Dá para fazer praticamente tudo o que fizemos acima com *map* e *filter* utilizando *List Comprehension*.

Outro ponto é que o desempenho é melhor quando usamos *List Comprehension*, ela é mais eficiênte com o uso do processador e da memória.

```python
langs = ['Python', 'Java', 'Cobol', 'Lisp', 'C++', 'C#', 'Ruby']
result_filter = [x for x in langs if x.lower() in ['java', 'python', 'c#']]
print(', '.join(result_filter))

result_map = [x.upper() for x in 'guilherme@gmail.com']
print(''.join(result_map))
```



## Exercícios

1. Crie um programa para executar o somatório de uma lista de números inteiros. Exemplo: `[1, 5, 4] ... resultado = 10`.
2. Crie um programa que receba uma lista de números inteiros. Remova todos os números ímpares maiores que trinta. Exemplo: `[1, 21, 31, 41] ... resultado [1, 21, 41]`.
3. Crie um programa que receba uma lista de números, e no final da execução retorne a mesma lista com os números elevados ao cubo.