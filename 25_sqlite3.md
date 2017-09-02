# Extra: SQLite 3

O SQLite é uma biblioteca C que fornece um banco de dados leve baseado em disco que não exige um processo de servidor separado e permite acessar o banco de dados usando uma variante não padrão da linguagem de consulta SQL. Alguns aplicativos podem usar o SQLite para armazenamento interno de dados. Também é possível prototipar um aplicativo usando o SQLite e depois migrar o código para um banco de dados maior, como o PostgreSQL ou Oracle.

```python
import sqlite3
import pprint

with sqlite3.connect(':memory:') as conn:
    cursor = conn.cursor()

    # Cria tabela
    cursor.execute('CREATE TABLE IF NOT EXISTS animals (name TEXT, age INTEGER, color TEXT)')

    # Insere registro
    cursor.execute('INSERT INTO animals VALUES ("Chappie", 1, "Yellow")')

    # Busca com where
    q = ('Chappie',)
    cursor.execute('SELECT * FROM animals WHERE name = ?', q)
    print(cursor.fetchone())

    # Insere N registros
    animals = [
        ('Megui', 3, 'Black and White'),
        ('Spike', 8, 'White and Brown'),
        ('Nick', 6, 'Brown'),
    ]

    cursor.executemany('INSERT INTO animals VALUES (?, ?, ?)', animals)

    # Busca todos
    cursor.execute('SELECT * FROM animals')

    pprint.pprint(cursor.fetchall())
```



## Exercícios

1. Crie um programa que faça o cadastro de todos os livros de uma biblioteca. Organize o projeto utilizando pacotes.