# Objetos - Entendendo seu ciclo de vida
Em Python tudo é objeto, então é muito importante entender como a linguagem trabalha com eles. Python possui um CLI que já vem instalado com a linguagem, para usá-lo abra o terminal e digite `python3`.

> Python CLI funciona muito bem para escrever pequenos pedaços de códigos, dessa forma podemos utilizá-lo para ver como o código irá se comportar antes de adicioná-lo no código.
> Com o intuito de ser simples e leve, o CLI padrão não possui nenhuma feature avançada como: code completion, sintaxe coloring, paste and copy, etc.
> Podemos instalar um pacode de terceiro **ipython** `pip install ipython3`, e ao invés de usar python no terminal entre com ipython.

Quando escrevemos `python3`, o interpretador é executado e como não passamos nenhum arquivo .py para ser executado, ele entende que estamos invocando o modo interativo. Sua saída deve estar parecida com:
```shell
Python 3.4.3+ (default, Oct 14 2015, 16:03:50)
[GCC 5.2.1 20151010] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

## Hello World
Conforme disse anteriormente tudo em Python é objeto: números, strings, classes, etc. Vamos criar um simples programa para exibir uma mensagem de boas vindas na tela:

```python
msg = 'Hello world!'

print(msg)

>>> Hello world!
```

No código acima estamos instanciando uma nova variável com o nome de *msg*, e atribuindo o valor *Hello world!*. Ao passar por essa linha o interpretador Python vai criar um objeto imutável para armazenar a mensagem e irá referênciar o objeto com a variável *msg*.

Na linha abaixo estamos imprimindo o valor da variável utilizando o comando *print*.

No próximo capítulo vamos discutir sobre variáveis mutáveis e imutáveis e como Python trata essa diferença internamente, por hora vamos nos atentar apenas nos 3 passos que ocorrem na vida de um objeto:

1. Definição
2. Inicialização
3. Acesso e manipulação
4. Destruição

### 1 - Definição

```python
# Quando declaramos um valor o python cria em sua tabela de referência um código para o objeto
my_value = 10

print(id(my_value))
>>> 9272960
print(id(10))
>>> 9272960
print(id(my_value) == id(10))
>>> True
```

Com o exemplo acima podemos perceber que o objeto é o valor e não a variável. Então o Python irá criar o objeto *10*, e atribuir um identificador o qual não irá mudar até o termino da execução de seu código.

### 2 - Inicialização

Todo objeto em Python possui uma função construtora, através dessa função podemos passar alguns valores para que o objeto possa ser criado. Vamos fazer o uso da função built-in *int()* para criar novos objetos inteiros em diversas bases:

```python
value_d = int(42, 10)   	 # decimal
value_o = int(23, 8)    	 # octal
value_h = int('2A', 16) 	 # hexadecimal
value_b = int(b'101010', 2)  # binária

print(value_d)
>>> 42
print(value_o)
>>> 42
print(value_h)
>>> 42
print(value_b)
>>> 42
```

### 3 - Manipulação

Com o objeto criado e inicializado podemos trabalhar com o mesmo, através de métodos que estão definidos no objeto.

```python
name = 'rex'
print(name.upper())
print(name.lower())
print(name[::-1])
print(name.title())
```

### 4 - Destruição

Quando um objeto é destruído o espaço de memória é liberado e o mesmo não existe mais. Quem se encarrega de destruir os objetos é o *Coletor de lixos (Garbage Collector)* do Python. Ele é executado em intervalos de tempo, e inspeciona todos os objetos criados, para identicar se ainda estão sendo utilizados.

Caso existam objetos que não possuem mais referências de utilização, os mesmo são removidos. Para remover a referência de um objeto fazemos o uso da função *del*:

```python
name = 'rex'
print(name)
del(name)
print(name)
>>> NameError                                 Traceback (most recent call last)
<ipython-input-11-7fa07326b3c2> in <module>()
----> 1 print(name)

NameError: name 'name' is not defined
```

## Objetos Mutáveis e Imutáveis

Em Python temos dois tipos de objetos:

1. **Mutáveis**: Podemos mudar o valor e o mesmo não irá receber um novo id.
2. **Imutáveis**: Não podemos mudar o valor, para isso precismos criar uma cópia modificada do mesmo.

Exemplo com objetos mutáveis:

```python
# lista é um tipo mutável
my_list = [1, 2]

print(id(my_list))
>>> 140402788344968

my_list += [3, 4]

print(id(my_list))
>>> 140402788344968
```

Exemplo com objetos imutáveis:

```python
# tupla é um tipo imutável
my_tuple = (1, 2,)
print(id(my_tuple))
>>> 140402778836488

my_tuple += (3, 4,)
print(id(my_tuple))
>>> 140402800332536
```

Esse é o ciclo de vida dos objetos no Python. Nos próximos capítulos vamos abordar como criar nossos objetos customizados.
