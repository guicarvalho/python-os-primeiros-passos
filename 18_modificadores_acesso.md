# Modificadores de acesso

Em Python não possuímos modificadores de acesso como: *public, protected, private, etc*. Para fazê-lo utilizamos convenções de código. Quando estamos nos referindo mais especificamente de atributos e métodos de uma classe colocamos um underscore antecedendo o nome, isso indica que essa variável é privada e que não deveria ser acessada diretamente.

Python possui um recurso chamado **name mangling**, que pode ser usado para evitar conflito de nomes com nomes definidos por subclasses. Para que o interpretador faça essa modificação ao invés de colocar um underscore, colocamos dois underscores.

```python
class Person:
  def __init__(self):
    self.name = 'Guilherme'
    self._age = 23
    self.__nickname = 'Gui'
```

No exemplo acima definimos uma classe chama *Person*, que contém três atributos: name, age e nickname.

1. name é um atributo da classe e pode ser utilizado normalmente, como não possui nenhum underscore consideramos que seu modificador de acesso é público.
2. age inícia com um underscore que significa que não é uma boa acessarmos o seu valor diretamente, e muito menos alterar diretamente.
3. nickname está iniciando com dois underscore, estamos evitando que haja conflito de nomes.

Como dissemos a pouco, tudo é baseado em convenção, então não existe uma forma explicita de evitar que o programador acesse sua variável. Então vamos ver como podemos acessar os valores criados acima.

```python
p = Person()
print(p.name)
print(p._age)
print(p._Person__nickname)
```

## Um pouco mais sobre name magling

Name magling nos ajuda a anular métodos sem quebrar as chamadas de método intraclasse.

```python
class Mapping:
  def __init__(self, iterable):
    self.items_list = []
    self.__update(iterable)
      
  def update(self, iterable):
    for item in iterable:
      self.items_list.append(item)
      
  __update = update   # private copy of original update() method

class MappingSubclass(Mapping):
    def update(self, keys, values):
      # provides new signature for update()
      # but does not break __init__()
      for item in zip(keys, values):
        self.items_list.append(item)

m = Mapping('ABCD')
print(m.items_list)

m.update([1, 2, 3, 4])
print(m.items_list)

ms = MappingSubclass('ABCD')
print(ms.items_list)

ms.update('ABCD', [1, 2, 3, 4])
print(ms.items_list)
```



## Exercícios

1. Crie uma classe que contenha pelo menos um atributo privado, um método privado, um atributo público e um método utilizando name magling.
