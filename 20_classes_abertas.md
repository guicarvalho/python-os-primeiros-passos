# Classes Abertas

Em Python podemos alterar a classe em tempo de execução. Adicionando/alterando atributos ou métodos. Também conhecido como MonkeyPatch, um MonkeyPatch é um pedaço de código Python que se estende ou modifica outro código no tempo de execução (normalmente na inicialização).

```python
import json

from django.views.generic.list import ListView

from soccerapi.client import get_results

from .models import Result

# Mocka o retorno do serviço alterando a implementação do client do módulo
get_results = json.dumps({
  'Palmeiras x São Paulo': (4, 2),
  'Barcelona x Real Madrid': (3, 1),
})

class ResultsListView(ListView):
  model = Result
  
  def get_context_data(self, **kwargs):
    context = super(ResultListView, self).get_context_data(**kwargs)
    context['results'] = get_results()
    return context
```