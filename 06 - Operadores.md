# Operadores

Existem dois tipos de operadores, os aritméticos e os lógicos. Os operadores aritméticos são usados geralmente para fazer operações matemáticas entre dois valores ou concatenação/produção de strings.

Os seguintes operadores aritméticos estão disponíveis em Python:

| Símbolo | Função        | Tipo de dado  |
| ------- | ------------- | ------------- |
| +       | Adição        | Numéricos     |
| -       | Subtração     | Numéricos     |
| /       | Divisão       | Numéricos     |
| *       | Multiplicação | Numéricos     |
| **      | Potenciação   | Numéricos     |
| %       | Módulo        | Numéricos     |
| +       | Concatenar    | Strings       |
| *       | Repetir       | Strings       |
| +       | Concatenar    | Lists, Tuples |
| *       | Gerar         | Lists, Tuples |

Perceba que os operadores **+ e *** possuem funcionalidades diferentes de acordo com o tipo de dados no qual os mesmos estão interagindo. Vamos escrever alguns exemplos:

```python
# Trabalhando com tipos númericos
1+1
>>> 2

1-1
>>> 0

10/2
>>> 5.0

2*2
>>> 4

2**3
>>> 8

10%3
>>> 1

# Trabalhando com strings (operadores sobrecarregados)
'a' + 'b'
>>> 'ab'

'a'*3
>>> 'aaa'

# Trabalhando com lists/tuples (operadores sobrecarregados)
[1, 3]+[2, 5]
>>> [1, 3, 2, 5]

[1, 2]*3
>>> [1, 2, 1, 2, 1, 2]

(1, 3)+(2, 5)
>>> (1, 3, 2, 5)

(1, 2)*3
>>> (1, 2, 1, 2, 1, 2)
```

Vamos agora analisar os operadores lógicos. Os operadores lógicos são usados quando queremos fazer algum tipo de comparação entre dois valores, como por exemplo: quem é maior, quem é menor, são iguais, são diferentes.

| Símbolo | Função         |
| ------- | -------------- |
| >       | Maior          |
| <       | Menor          |
| ==      | Igual          |
| !=      | Diferente      |
| >=      | Maior ou igual |
| <=      | Menor ou igual |

Vamos fazer alguns exemplos:

```python
a = 10
b = 20

if a > b:
  print('A é maior que B')

if 100 >= b:
  print('B é maior ou igual a 100')

if 100 != a:
  print('Os números são diferentes')
```

Algumas vezes vamos precisar fazer mais de uma verificação para garantir uma regra de negócio que queremos implementar. Nesse caso, não queremos fazer um monte de if aninhado (um if dentro de outro if).

Para isso, podemos usar 2 operadores AND e OR. Além desses operadores contamos ainda com um operador de negação NOT, ele inverte o valor do resultado booleano da comparação.

| Símbolo | Função    |
| ------- | --------- |
| and     | E lógico  |
| or      | Ou lógico |
| not     | Negação   |

```python
a = 20
b = 10

# verificar se o número é maior que o outro e se ele é maior que 100
if a > b and a > 100:
  print('A é maior que B e também é maior de 100')

if a < b or a < 100:
  print('A é menor que B ou A é menor que 100')

# exibir a mensagem SUCESSO quando A for MAIOR que B
if not b > a:
  print('SUCESSO')
  print('A é maior que B')
```



## Exercícios

1. Crie um programa que imprima o valor do maior número entre duas variáveis.
2. Crie um programa que imprima o maior e o menor valor entre três variáveis.
3. Crie um programa que imprima 'HAHAHA' caso o número da variável seja par.
4. Crie um programa para dizer se o número é par ou ímpar.