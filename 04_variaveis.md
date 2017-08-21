# Variáveis

Em linguagens de programação podemos definir valores que podem sofrer alterações no decorrer da execução do programa. Esses valores recebem o nome de *variáveis*, pois eles nascem com um valor e não necessáriamente devem permacer com o mesmo durante a execução do programa.

Para definir uma variável em Python basta definir o nome e qual o valor que deseja atribuir:

```python
age = 23
name = 'Guilherme'
print(f'Meu nome é {name} e eu tenho {age} ano(s) de idade.')
```

Perceba que não precisamos definir o tipo de dados da variável, o Python faz isso automaticamente para nós. Por isso não podemos simplesmente criar uma variável sem atribuir um valor.

Para alterar o valor da variável basta fazer uma atribuição de um novo valor:

```python
age = 23
name = 'Guilherme'
print(f'Meu nome é {name} e eu tenho {age} ano(s) de idade.')
>>> Meu nome é Guilherme e eu tenho 23 ano(s) de idade.

age = 22
name = 'Giovanna'
print(f'Meu nome é {name} e eu tenho {age} ano(s) de idade.')
>>> Meu nome é Guilherme e eu tenho 23 ano(s) de idade.
>>> Meu nome é Giovanna e eu tenho 22 ano(s) de idade.
```



# Constantes

Em Python não conseguimos criar valores contantes, ou seja, não existe um palavra-chave como **final** do Java, que indica ao interpretador (no caso do Python) que aquela variável não pode ter o valor alterado.

Mas podemos dizer ao programador através de convenção que aquela variável deve se comportar como uma constante. Para fazer isso, você deve criar a váriavel com o nome todo em letras maíusculas:

```python
ABS_PATH = '/home/guilherme/Documents/PythonCourse/'
```



## Exercícios

1. Criei um programa para armazenar as informações de um livro em variáveis, precisamos armazenar as seguintes informações: título, autor, ano de publicação, número de páginas e editora.
2. Altere o programa do exercício anterior, e adicione uma constante para o número de páginas do livro.