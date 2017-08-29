# For, While e Range

Python possui duas estruturas de repetição: *while* e *for*. Cada estrutura possui seu uso especifico, a estrutura *for* deve ser usada quando sabemos previamente o número de vezes que o código deve se repetir, já a estrutura *while* utilizamos quando não sabemos o número de iterações que podem acontecer.

## For

O comando *for* pede um objeto iterável, portanto devemos fornecer uma lista, string ou qualquer
outro objeto que possa ser iterável. A sintaxe do comando é semelhante ao *foreach* de linguagens como Java e C#.

```python
fruits = ['apple', 'grape', 'papaya', 'orange']

for fruit in fruits:
  print(fruit)
```

No trecho de código acima os itens da lista *fruits* serão percorridos um a um. O valor é atribuido a variável *fruit*, após fazer a atribuição utilizamos o comando *print* para exibir o valor para o usuário.

O comando *for* possui um bloco opcional chamado *else*. O bloco *else* é executado ao final da iteração, ele sempre será executado até mesmo quando o objeto iterável for vazio.

```python
fruits = ['apple', 'orange']
for fruit in fruits:
  print(fruit)
else:
  print('Acabou, lista cheia ...')
  
fruits = []
for fruit in fruits:
  print(fruit)
else:
  print('Acabou, lista vazia ...')
```

## While

Podemos utilizar o comado *while* quando não sabemos o número de vezes que nosso bloco deve
repetir. Geralmente utilizamos uma condição para saber se a iteração deve continuar, desviar ou pausar.

A sintaxe do comando é bem parecida com as de outras linguagens. O *while* também possui
o bloco *else* e seu funcionamento é o mesmo do comando *for*.

Outros comandos que geralmentes utilizamos com while são: *break* (interrompe a iteração) e *continue* (pula a execução e segue para a próxima).

Usando o *else*:

```python
op = 1

while op != 0:
  print('''MENU
  =============================
  1 - HELLO WORLD
  0 - EXIT
  ''')
  op = int(input('>> '))
  if op:
    print('HELLO WORLD!!!')
else:
  print('OBRIGADO POR USAR NOSSO PROGRAMA =)')
```

Usando *break* e *continue*:

```python
while True:
  number = int(input('Número PAR para continuar e ÍMPAR para parar: '))
  
  if number % 2:  # se houver resto é impar
    break
  else:
    print('AEEEE, vamos continuar!!!')
```

## Range

*Range* é uma função built-in do Python, ela é usada para produzir sequência de números inteiros apartir de um ínicio (inclusivo) para um fim (exclusivo) passo a passo. Se usarmos *range(i, j)* será produzido: i, i+1, i+2, i+3 ... j-1.

Se informarmos o ínicio sem o fim para a função, por padrão ela irá iniciar de zero.

```python
range(4)
>> 0, 1, 2, 3
```

Como vimos a função retorna uma lista iterável de inteiros, dessa forma podemos usar o comando *for* para percorrer os valores.

```python
for n in range(0, 11):
  print(n)

# exibindo a tabuada do 5
for n in range(0, 51, 5):
  print(n)
```

Lembrando que apenas o parâmetro fim (stop) é obrigatório, ínicio (start) e passo (step) são opcionais:

```
range(stop) -> range object
range(start, stop[, step]) -> range object
```

Acima podemos ver a Docstring do comando *range*.



## Exercícios

1. Crie um programa que exiba todos os números pares de 1 à 100.
2. Crie um programa para listar nomes de livros que você já leu.
3. Crie um programa que solicite um número ao usuário, caso o número seja par o programa deve exibir "VAMOS CONTINUAR" caso contrário o programa deve ser encerrado e exibir a mensagem "OBRIGADO!".