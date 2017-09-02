# Polimorfismo

Assim como em muitas outras linguagens orientadas a objetos o Python permite o uso de polimorfismo, uma vez que ele também oferece o uso de herança. Polimorfismo é uma ferramenta muito poderosa na programação Orientada a Objetos, pois possibilita que um objeto possa se comportar de formas diferentes.

Então digamos que temos um objeto A que herda de um objeto B, podemos estender o objeto B e armazenar nele um objeto A e quando fizermos uma chamada a esse objeto A que está “envolvido” pelo método B podemos chamar qualquer função que B tem, pois A é um B por definição. Com isso acabam-se aquele emaranhado de IF's para testar se um objeto é subclasse de outro.

```python
def greeting(animal):
  return animal.speak()


class Animal:
  def speak(self):
    return 'grooooh'

class Duck:
  def speak(self):
    return 'Quack-quack'

  
class Dog:
  def speak(self):
    return 'Au-au'

  
class Cat:
  def speak(self):
    return 'Miau-miau'
  
  
print(greeting(Duck()))
print(greeting(Dog()))
print(greeting(Cat()))
```

