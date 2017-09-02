# Propriedades

Python possui o mecânismo de propriedades, com elas podemos definir métodos para: leitura, escrita e destruição.

```python
class Person:
  def __init__(self, name):
    self._name = name
  
  @property
  def name(self):
    return self._name
  
  @name.setter()
  def name(self, name):
    self._name = name
  
  @name.deleter
  def name(self):
    del self._name
```

Podemos definir que a variável terá apenas acesso de leitura.

```python
class Person:
  def __init__(self, name):
    self._name = name
  
  @property
  def name(self):
    return self._name
```



## Exercícios

1. Defina uma classe que contenha um parâmetro. Defina todas as propriedades para o mesmo.
2. O que acontece quando o atributo tem somente a propriedade de leitura declarada e o programa tenta atribuir um novo valor?