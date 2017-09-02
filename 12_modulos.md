# Módulos

Um módulo é um arquivo contendo definições e declarações do Python. O nome do arquivo é o nome do módulo com o sufixo .py adicionado.

Isto é, um arquivo *foo.py* é considerado um módulo Python se possuir definições e instruções da linguagem. Ou seja, qualquer arquivo Python pode ser considerado um módulo. Para este caso, o nome do módulo seria foo, definido pelo nome do arquivo, sem a extensão. Os módulos são carregados no Python pelo processo de importação.

```python
# foo.py

def hello_world():
  print('Hello world!')
  
def sum(a, b):
  return a + b


# main.py
import foo

if __name__ == '__main__':
  foo.hello_world()
  print(foo.sum(1, 9))
```

# Pacotes

O pacote é a forma de definir *namespaces* para os módulos, permitindo que inúmeros módulos de mesmo nome coexistam sem interferência. Basicamente, um pacote Python é um diretório que contém módulos.

```
├── client
│   └── test.py
└── main.py
```

```python
from client.test import hello_world

hello_world()
```



## Exercícios

1. Crie um módulo que contenha todas as operações básicas da calculadora.
2. Imagine que acabou de fechar um projeto grande em Python. Você precisa pensar em uma boa forma de organizar seus módulos. Qual estrutura de pacotes você montaria?