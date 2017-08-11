# Objetos - Entendendo seu ciclo de vida
Em Python tudo é objeto, então é muito importante entender como a linguagem trabalha com eles. Python possui um CLI que já vem instalado com a linguagem, para usá-lo abra o terminal e digite `python3`.

>   Python CLI funciona muito bem para escrever pequenos pedaços de códigos, dessa forma podemos utilizá-lo para ver como o código irá se comportar antes de adicioná-lo no código.
> Com o intuito de ser simples e leve, o CLI padrão não possui nenhuma feature avançada como: code completion, sintaxe coloring, paste and copy, etc.
> Podemos instalar um pacode de terceiro **ipython** `pip install ipython3`, e ao invés de usar python no terminal entre com ipython.

Quando escrevemos `python3`, o interpretador é executado e como não passamos nenhum arquivo .py para ser executado, ele entende que estamos invocando o modo interativo. Sua saída deve estar parecida com:
```py
Python 3.4.3+ (default, Oct 14 2015, 16:03:50) 
[GCC 5.2.1 20151010] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

## Hello World
Conforme disse anteriormente tudo em Python é objeto, números, strings, classes, etc. ```py
>>> msg = 'Hello world!'
>>> print(msg)
Hello world!
```
