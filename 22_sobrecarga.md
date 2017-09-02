# Sobrecarga

Python não possui sobrecarga de métodos, mas possui sobrecarga de operadores. Uma vez que tudo em Python é objeto os tipos primitivos também são. O comportamento dos operadores são definido por métodos especiais, porém esses métodos podem ser alterados.

```python
class Foo:
  def __init__(self, n):
    self.n = n

f1 = Foo()
f2 = Foo()

# Type Error
print(f1 > f2)
print(f1 + f2)
```

```python
class Foo:
  def __init__(self, n):
    self.n = n
    
  def __gt__(self, other):
    return self.n > other.n
    
  def __add__(self, other):
    return self.n + other.n

f1 = Foo(10)
f2 = Foo(5)

print(f1 > f2)
print(f1 + f2)
```



## Exercícios

1. Crie um programa para somar frações equivalentes. O usuário deve informar as duas frações, o sistema valida se as frações são equivalentes e em seguinda exibe o valor para o usuário. 