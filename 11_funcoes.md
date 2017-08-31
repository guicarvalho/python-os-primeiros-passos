# Funções

Funções são blocos de códigos identificados por um nome único que podem recerber uma lista de parâmetros, esses parâmetros podem ou não ter valores padrões. Usar funções torna o código mais legível e possibilita o reaproveitamento de código. Programar baseado em funções, é o mesmo que dizer que estamos programando de maneira estruturada.

Funções podem ser vazias (sem retorno) ou retornar um ou mais objetos. Em Python não informamos se o parâmetro é passado por valor ou referência, essa classificação é feita pela interpretador que olha se o objeto passado é imutável ou mutável.

Caso o objeto passado por parâmetro seja imutável, os valores alterados dentro do escopo da função não serão refletidos ao objeto, mas se for passado um objeto mutável então os valores alterados dentro do escopo serão refletidos.

Para declarar uma função em Python utilizamos a palavra-chave *def* seguido por: nome da função,
lista de parâmetros, corpo da função e retorno. Para retornar valores em Python é usada a palavra-chave *return*. Caso você não informe um valor de retorno o Python automaticamente irá retornar *None* representando que o retorno da função é vazio.

```python
def my_function(anything):
  print(anything)
 
my_function('Hello World!')
my_function([1, 2, 3, 4, 5])
```

Acima um exemplo simples de uma função que recebe um parâmetro. Nesse caso estamos dizendo que no momento que *my_function* for chamada, deve ser fornecido um valor *anything* para ela. Nesse momento a função não faz muita coisa ela apenas imprime o valor informado.

Podemos ver o valor que *my_function* retornou atribuindo a uma variável. Como não a função não possui a palavra-chave *return* o Python irá retornar *None*.

```python
...
resp = my_function('Hello World!')
print('Resp: {}'.format(resp))
```

Para retornar um valor, podemos usar *return*. Quando o interpretador encontrar essa palavra-chave ele irá interromper a execução da função retornando o valor informado, ou seja, todas as linhas abaixo de return serão executadas.

```python
def op_sum(a, b):
  return a + b

result = op_sum(10, 20)
print('Total: {}'.format(result))
```

Podemos ter parâmetros obrigatórios e opcionais. Quando definimos parâmetros opcionais devemos informar um valor *default* para ele, caso ele não seja passado na chamada da função o valor padrão será utilizado.

```python
def op_div(a, b=1):
  return a / b

r1 = op_div(10)
r2 = op_div(10, 2)

print('r1: {}'.format(r1))
print('r2: {}'.format(r2))
```

Não existe um número máximo ou mínimo de parâmetros para uma função, podemos ter 1, 2, 3 ou 30 caso seja necessário. Porém uma função com muitos parâmetros não é muito fácil de trabalhar e manter o código.

Quando desejamos passar um grande número de valores como parâmetro e esse número pode variar de acordo com alguma condição podemos usar o recurso de *varargs* e *kwargs*. Esses recursos permitem que possam ser passados N parâmetros para a função sem que precisemos definir N parâmetros na chamada da função.

Quando utilizamos *varargs* os valor recebidos serão convertidos em uma tupla. Como sabemos em Python não definimos qual o tipo de dado da variável, quem faz isso para nós é o interpretador. Então de alguma forma precisamos informar que para a nossa função que ela irá receber um parâmetro que deve se comportar como *varargs*. Para isso usamos o sinal * antes do nome do parâmetro, nome é livre mas existe uma convenção e geralmente esse parâmetro tem o nome de *args*.

```python
def varargs(a, b, *args):
  """Soma N números passados por parâmetro."""
  print('a: {}, b: {}, args: {}'.format(a, b, args))
  result = a + b
  for number in args:
    result += number
  return result

r1 = varargs(1, 2, 3, 4, 5, 6, 7, 8, 9)
r2 = varargs(1, 2, 3)

print('r1: {}'.format(r1))
print('r2: {}'.format(r2))
```

Podemos trabalhar de forma semelhante com *kwargs*. A diferença está na forma como os parâmetros serão tratados pelo interpretador. Quando usamos *varargs* o interpretador espera que seja passado uma tupla de valores, quando usamos *kwargs* é esperado que seja passado um dicionário. Para isso fazemos a chamada da função passando os parâmtros no formato **chave/valor**.

```python
def kwargs(a, b, **kwargs):
  """Soma N números passados por parâmetro."""
  print('a: {}, b: {}, kwargs: {}'.format(a, b, kwargs))
  result = a + b
  for number in kwargs.values():
    result += number
  return result

r1 = kwargs(1, 2, **{'v1': 10, 'v2': 54})
r2 = kwargs(3, 5, v1=25, v2=13)

print('r1: {}'.format(r1))
print('r2: {}'.format(r2))
```

Perceba que tanto *varargs* como *kwargs* estão definidos como últimos parâmetros da função. Não podemos colocá-los em outra posição, pois o interpretador não saberia no momento de execução onde atribuir os valor passados. Podemos usar *varargs* e *kwargs* na mesma função caso seja necessário.

```python
def varargs_kwargs(a, b, *args, **kwargs):
  print('varargs: {}'.format(args))
  print('kwargs: {}'.format(kwargs))
  
varargs_kwargs(1, 45, 4, 6, 7, 8, 10, v1=10, b2=19)
```

Em Python **tudo** é objeto, dessa forma funções também são objetos o que as tornam **objetos de primeira classe**.  Com isso podemos atribuir funções a variáveis, passá-las como parâmetro para funções, usá-las como valores em estruturas de dados (listas, tuplas, dicionários, etc) e usar como valor de retorno para uma função (closures).

```python
def fsum(a, b):
  return a + b

make_sum = fsum

print(make_sum(10, 30))
print(make_sum(156, 3))
print(make_sum(1, 128))
```

```python
def calculator(a, b, op):
  """Recebe dois valores 'a' e 'b' e qual operação deve ser executada."""
  return op(a, b)

def fsum(a, b):
  return a + b

def fdiv(a, b):
  return a / b

def fmul(a, b):
  return a * b

def fsub(a, b):
  return a - b

print(calculator(20, 10, fsum))
print(calculator(20, 10, fdiv))
print(calculator(20, 10, fmul))
print(calculator(20, 10, fsub))
```

```python
def greeting():
  return 'Hi!'

person = {
	'name': 'Guilherme',
  	'greeting': greeting
}

print('{0} my name is {1}.'.format(
  person.get('greeting')(),
  person.get('name')
))
```

```python
from random import randint

def make_list(numbers):
  size = len(numbers)
  def get_random():
    n = randint(0, size - 1)
    return numbers[n]
  return get_random

play = make_list([1, 65, 12, 52, 100, 3, 109, 10])

for i in range(10):
	print('{}: {}'.format(i, play()))
```

## Escopo Local e Escopo Global

Python trabalha com escopo local e global, dentro do bloco da função o escopo é local. Portanto alterações ali feitas em objetos imutáveis serão perdidas quando o método terminar de ser executado. Para resolver esse problema podemos utilizar a palavra-chave *global* que informa ao Python que a variável que está sendo manipulada no escopo local é global, fazendo assim o valor ser persistido na variável. Essa **Não é um boa prática e deve ser evitada**.

```python
# UnboundLocalError
salary = 1000
def salary_bonus(bonus):
  salary += bonus
  return salary
```

```python
salary = 1000
def salary_bonus(bonus):
  global salary
  salary += bonus
  return salary
```



## Exercícios

1. Crie uma função que calcule o IMC. O programa deve solicitar o peso e altura e imprimir qual o valor calculado.

2. Crie uma função que recebe N números por parâmetro. A função deve verificar se o número é par ou ímpar, caso par o somar o número ao valor total, caso ímpar subtrair o número do total. Ao final da execução imprimir o resultado.

3. Crie uma função para imprimir as informações do usuário seguinte usuário: `perfil = {'name': 'Guilherme', 'age': 23, 'city': 'Araraquara/SP'}`.

   Dica: `print('Nome: {name}, Idade: {age}, Cidade: {city}.'.format(**perfil))`

4. Crie um programa para ilustrar o uso da variável global. O programa deve conter duas funções, uma que modifica o valor corretamente e outra que não permite a alteração (erro ou valor não é alterado).

5. Crie uma função para fazer a operação de divisão. Essa função deve receber o valor do *divisor* e permitir que seja feita a chamada N vezes apenas passando o *dividendo*. Exemplo:

   ```
   divisor = 2

   dividir = funcao(divisor)
   r1 = dividir(10)
   r2 = dividir(30)
   r3 = dividir(80)

   Resultado:
   r1 = 5
   r2 = 15
   r3 = 40
   ```