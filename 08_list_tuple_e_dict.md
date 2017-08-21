# List, Tuple e Dict

Python possui tipos de dados mais complexos, onde podemos armazenar uma lista de N objetos de qualquer tipo, N itens no formato chave/valor ou uma lista de N objetos onde os valores dessa lista não podem ser alterados.

## List

Listas em Python podem armazenar qualquer tipo de objeto e não é necessário informar a quantidade de máxima de itens que irá armazenar, pois o tamanho é controlado dinâmicamente.

Conforme discumos no capítulo 2, listas são objetos do tipo mutável. Isso permite que durante a execução do programa a lista sofra alterações nos itens que ela armazena, podemos adicionar ou remover itens.

Como a lista pode armazenar qualquer tipo de objeto, podemos ter uma lista dentro de outra lista (listas aninhadas). Assim como Strings, listas são fatiáveis, então podemos acessar seus valores através de colchetes.

```python
my_list = [1, 2, 3, 4]

my_list[0]
>>> 1
my_list[:3]
>>> [1, 2, 3]
my_list[::-1]
>>> [4, 3, 2, 1]
```

A classe list possui muitos métodos que podemos utilizar para manipular o seu conteúdo. Podemos fazer o uso dos comandos **help() e dir()** para listar e ver a forma de utilização dos mesmos. Abaixo alguns métodos:

```python
my_list = [1, 2]

my_list.append(3)
>>> [1, 2, 3]
[1, 2, 2, 3, 5, 1, 3, 2].count(2)
>>> 3
my_list = [4, 22, 10, 2]
my_list.sort()
>>> [2, 4, 10, 22]

# Alterando valor
my_list = [1, 2, 3]
my_list[0] = 0
>>> [0, 2, 3]

# Removendo valores
my_list = [1, 2, 3]
my_list.pop()
>>> 3
my_list
>>> [1,	 2]
```

## Stack

Podemos usar listas com o comportamento de pilha (FIFO - First In First Out), para isso usando os métodos `append` e `pop`.

```python
my_stack = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
my_stack.pop()
>>> 10
my_stack += [123, 456, 789]
my_stack
>>> [1, 2, 3, 4, 5, 6, 7, 8, 9, 123, 456, 789]
my_stack.pop()
>>> 789
my_stack.pop()
>>> 456
my_stack.pop()
>>> 123
my_stack.pop()
>>> 9
my_stack.pop()
>>> 8
my_stack
>>> [1, 2, 3, 4, 5, 6, 7]
```

## Set

Python possui uma implementação para listas que não repetem valores. Essas listas são conhecidas como Sets, e existem em diversas linguagens.

```python
my_list = [1,2,3,4,1,2,3,4]
set(my_list)
>>> {1,2,3,4}

# Criando um set
my_set = {1, 2, 3}
my_set.add(1)
my_set.add(5)
print(my_set)
>>> {1, 2, 3, 5}
```

## Tuple

As tuplas são tipos de dados imutáveis, o seu uso é muito semelhante a listas. Devemos usar as tuplas quando precisamos de uma lista de valores que não devem ser alteradas durante a execução do programa. Para declarar uma tupla usamos parênteses ao invés de colchetes.

## Dict

Dicionários são estruturas que armazenam valores utilizando uma referência para buscá-los, dizemos que são estruturas chave/valor. Se você já programou em Java, um dicionário é igual ao *HashMap<Object, Object>*.

Assim como as listas e tuplas, um dicionários pode armazenar todos os tipos de objetos como valor, mas para chaves você deve informar um objeto imutável. 

Para declarar dicionários usamos o caracter chave ({}), e dentro do delimitador colocamos um objeto imutável como chave, dois pontos (:) um objeto mutável ou imutável como valor.

O dicionário não preserva a ordem de inserção dos itens, essa é uma caracterisca diferente entre listas, tuplas e dicionário, uma vez que as outras duas preservam a ordem.

Caso você precise manter a order de inserção dos itens no dicionário você irá ter que usar **OrderedDict**, que é um dicionário com um outra implementação.

```python
my_dict = {
  'name': 'Guilherme',
  'idade': 23,
  'city': {
    'name': 'Araraquara',
    'uf': 'São Paulo',
  },
  'languages': ['Python', 'Android', 'Java'],
}

# Acessando os itens
my_dict['name']
>>> 'Guilherme'

# Adicionando um novo valor
my_dict['rg'] = '56789345-9'
my_dict
>>>
{
  'city': {
    'name': 'Araraquara',
    'uf': 'São Paulo'
  },
  'idade': 23,
  'languages': ['Python', 'Android', 'Java'],
  'name': 'Guilherme',
  'rg': '56789345-9'
}

# Recuperando valores
my_dict['name']
# or
my_dict.get('name')
>>> 'Guilherme'

# Removendo itens
my_dict.popitem()  # remove o ultimo valor inserido
>>> ('rg', '56789345-9')
# or
my_dict.pop('idade')  # remove a chave passada por parametro
>>> 23
```

### Construindo um dicionário com order fixa

Caso você precise manter a ordem do dicionário criado, existe uma implementação de dicionário que irá atender. Abaixo exemplo de uso:

```python
from collections import OrderedDict

my_dict = OrderedDict({
  'name': 'Guilherme',
  'idade': 23,
  'city': {
    'name': 'Araraquara',
    'uf': 'São Paulo',
  },
  'languages': ['Python', 'Android', 'Java']
})

print(my_dict)
>>>
OrderedDict([('name', 'Guilherme'),
             ('idade', 23),
             ('city', {'name': 'Araraquara', 'uf': 'São Paulo'}),
             ('languages', ['Python', 'Android', 'Java'])])
```

Você pode manipular o *OrderedDict* da mesma forma que o dicionário padrão.