# MetaClasses

Em orientação a objetos, uma metaclasse é uma classe cujas instâncias também são classes e não objetos no sentido tradicional. Assim como classes definem o comportamento de certos objetos, metaclasses definem o comportamento de certas classes e suas instâncias. Nem toda linguagem orientada a objeto suporta metaclasses. 

Em Python as classes podem ser instâncias de qualquer classe que herde de type.

```python
class Animal:
  pass

print(type(Animal))
print(type(int))
```

```python
class AnimalMeta(type):
  def __call__(self, *args, **kwargs):
    # cria nova instancia
    obj = type.__call__(self, *args)
    
    # adiciona os atributos ao objeto
    for nome in kwargs:
      setattr(obj, nome, kwargs[nome])

    # retorna o objeto.
    return obj
    
class Animal(metaclass=AnimalMeta):
  __slots__ = ['name', 'color', 'age', 'nickname']
  
  def __repr__(self):
    return "<Animal: {name}, {nickname}, {age}, {color}>".format(
      name=self.name,
      nickname=self.nickname,
      age=self.age,
      color=self.color)
  
dog = Animal(name='Chappie', nickname='Magrelo', age=1, color='Yellow')
print(dog)
```

```python
rex = type('Cao', tuple(), {
  'name': 'Rex',
  'age': 3,
  'color': 'white'
})

print(rex)
```

