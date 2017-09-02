# Classes

Classes são projetos de objetos, então para construir nossos objetos precisamos primeiro criar nossas classes. Como dito ao decorrer de todo o material a linguagem Python é totalmente orientada a objetos, portante em muitos capítulos já fizemos o uso de classes para executar nossas tarefas.

Para declarar uma classe em Python usamos a palavra-chave class seguido de um nome, o qual representa o nome de nossa classe. O Python permite herança simples e herança múltipla como veremos mais a frente, por isso ao declaramos nossas classes podemos dizer de quem ela é “filha”. Caso nada seja informado então o interpretador intenderá que a classe é filha de object.

O Python também permite declarar classes vazias, para fazer isso utilizamos a palavra-chave *pass*. Pode parecer meio tosco no começo, mas o Python possui classes abertas, ou seja, a classe pode receber atributos e métodos durante a execução do programa. Classes vazias podem ser criadas para serem compostas durante a execução do programa. É claro que isso não é uma boa prática pois torna a leitura e entendimento do código muito mais complexo.

```python
class Car:
  # __init__ é utilizado para inicializar a classe
  def __init__(self, color, model, brand):
    print('__init__')
    self.color = color
    self.model = model
    self.brand = brand
    
  @classmethod
  def from_string(cls, strinfo):
    print(cls)
    color, model, brand = strinfo.split('-')
    return cls(color, model, brand)
  
  @staticmethod
  def is_string_valid(strinfo):
    return len(strinfo.split('-')) >= 3
  
  def __repr__(self):
    return '<Car: {} - {}, {}>'.format(self.model, self.brand, self.color)
```

Observe que aparece em alguns lugares a palavra *self*, na verdade essa é uma refência ao objeto. Em muitas linguagens o *self* (referência) não aparece na declaração dos métodos, ou seja, eles estão implícitos. 

Seguindo a filosofia do Python (The Zen of Python) de que explícito é melhor que implícito essa foi a maneira adotada. A palavra *self*, poderia ter qualquer nome mas a PEP 8 padroniza esse nome e muitos programadores já aderem *self* como palavra-chave do Python apesar de ele não ser.