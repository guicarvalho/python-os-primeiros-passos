# Data e Hora

No desenvolvimento de aplicações é muito comum precisarmos manipular data e hora. Python possui em sua biblioteca padrão um módulo para manipular data e hora. Podemos acessar a documentação do módulo com o link [https://docs.python.org/3.6/library/datetime.html](https://docs.python.org/3.6/library/datetime.html).

```python
from datetime import datetime

now = datetime.now()
print(now)
```

Acima recuperamos a data atual, inclusive com o horário. Podemos verificar qual é o dia da semana:

```python
days_of_week = {
	0: u'Domingo',
	1: u'Segunda-Feira',
	2: u'Terça-Feira',
	3: u'Quarta-Feira',
	4: u'Quinta-Feira',
	5: u'Sexta-Feira',
	6: u'Sábado',
}

number_of_day = datetime.now().isoweekday()  # dom = 0 ... sáb = 6
print('{}'.format(days_of_week[number_of_day]))
```

Podemos formatar a impressão da data passando uma *string* com a máscara.

```python
# ...
print('Data sem formatação: {}'.format(now))
print('Data formatada: {}'.format(now.strftime('%A %d de %b de %Y')))
print('Data formatada: {}'.format(now.strftime('%d/%m/%y')))
print('Data formatada: {}'.format(now.strftime('%d/%m/%Y')))
```

Você pode alterar o locale para exibir a formatação de acordo com o país desejado. *Nota: locale deve estar disponível na máquina*.

```sh
$ locale -a
C
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
POSIX
pt_BR.utf8
```

```python
import locale                               
locale.setlocale(locale.LC_ALL, 'pt_BR.utf8')

print('Data formatada: {}'.format(now.strftime('%A %d de %b de %Y')))
```

Outra necessidade muito comum é calcular a diferença entre duas datas. Quando ocorre uma operação matemática com objetos dos tipos *date, time* ou *datetime*, o Python irá devolver um objeto *timedelta*, no qual a diferença entre as unidades é expressada em microsegundos.

```python
from datetime import datetime

now = datetime.now().date()
birth = datetime(now.year + 1, 3, 21, 12, 0, 0, 0).date()
diff_days = (birth - now).days

print('Hoje: {}'.format(now.strftime('%d-%m-%Y')))
print('Próx. aniversário: {}'.format(birth.strftime('%d-%m-%Y')))
print('Faltam {} dias.'.format(diff_days))

# diff em horas
diff_hours = (birth - now).total_seconds() / 60 / 60
diff_minutes = (birth - now).total_seconds() / 60
diff_seconds = (birth - now).total_seconds()

print('Faltam {:.0f} horas.'.format(diff_hours))
print('Faltam {:.0f} minutos.'.format(diff_minutes))
print('Faltam {:.0f} segundos.'.format(diff_seconds))
```

Algumas vezes vamos precisar transformar textos em datas, por exemplo, podemos ler um arquivo txt com informações de usuários inativos no sistema. Ao parsear o arquivo durante o processo de leitura, vamos obter a data com o tipo string. 

```python
'... le o arquivo e obtem a linha com a data'
inactive_user_date = '10/10/15'
conv_date = datetime.strptime(inactive_user_date, '%d/%m/%y')
print(conv_date)
```

Para trabalhar apenas com horas, podemos fazer o uso do módulo time https://docs.python.org/3.6/library/time.html](https://docs.python.org/3.6/library/time.html). Esse módulo é especifico para trabalhar apenas com funções relacionadas a tempo.

```python
import locale

import os

from datetime import timedelta

from time import strftime, strptime, localtime, gmtime, mktime, time, tzset
                               
locale.setlocale(locale.LC_ALL, 'pt_BR.utf8')

now = localtime()
time_formatado = strftime('%a, %d %b %Y %H:%M:%S +0000', now)
print('{}'.format(time_formatado))

# time() retorna o tempo do sistema em segundos
now_sec = time.time()

# gmtime() converte segundos para struct_time
struct_time = time.gmtime(now_sec)
print(struct_time, now_sec)

# Somando uma hora
now = time()
new = now + (60 * 60)
now = gmtime(now)
new = gmtime(new)
print(strftime('%H:%M:%S', now))
print(strftime('%H:%M:%S', new))

# Calculando a diferença
t1 = mktime(strptime('2 Out 17', '%d %b %y'))
t2 = mktime(strptime('10 Out 17', '%d %b %y'))

diff = timedelta(seconds=(t2 - t1))
print(diff)
```



## Exercícios

1. Escreva um programa que calcule quantos dias faltam para a Copa do mundo FIFA 2018.
2. Escreva um programa que calcule o número de dias, horas, minutos e segundos que faltam para o aniversário. O programa deve solicitar a data ao usuário.