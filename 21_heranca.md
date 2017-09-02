# Herança

Python assim como C++ e Smaltalk implementa herança simples e mpultipla. Na herança simples, a classe extende de uma única super classe herdando todas as suas caracteristicas. Dizemos que a classe filha é a classe mais especifica e a classe pai ou super classe é a classe mais genérica.

A herança múltipla permite que uma classe filha herde de mais de uma super classe, fazendo com que o comportamento de todas as classes herdadas sejam extendidos.

```python
class Animal:
  def __init__(self, name):
    self.name = name
    
  def speak(self):
    return 'gruuuh'
  
  def walk(self):
    return 'walking ...'
    
class Dog(Animal):
  def speak(self):
    return 'Au-au'
  
d = Dog('Chappie')
a = Animal('Foo')

print(a.name, d.name)
print(a.walk(), d.walk())
print(a.speak(), d.speak())
```

```python
class Animal:
  def __init__(self, name):
    self.name = name
    
  def speak(self):
    return 'gruuuh'
  
  def walk(self):
    return 'walking ...'

class Robot:
  def __init__(self, number):
    self.number = number
  
  def toggle_xray_vision(self, turn_on=False):
    if turn_on:
      return 'x-ray vision activated'
    return 'x-ray vision disabled'
  
class Dog(Animal, Robot):
  def __init__(self, name, number):
    Animal.__init__(self, name)
    Robot.__init__(self, number)
    
  def speak(self):
    return 'Au-au'
  
  def __repr__(self):
    return '{}.{}'.format(self.name, self.number)
  
d = Dog('Chappie', 1)
a = Animal('Foo')

print(a.name, d)
print(a.walk(), d.walk())
print(a.speak(), d.speak())
print(d.toggle_xray_vision(True))
print(d.toggle_xray_vision())
```

