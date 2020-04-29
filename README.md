<h1 align="center">Logica Fuzzy</h1>
<p align="center">Resolução de problema de Consumo de combustível Viajante</p>
<p align="center">
  <a aria-label="Github Pages" href="https://dioumedeiros.github.io/genetic-algorithm/">
    <img src="https://img.shields.io/badge/genetic-algorithm-blueviolet" />
  </a>
</p>

## Instale o pacote skfuzzy

```python
!pip install networkx
!pip install scikit-fuzzy
```

## Criação de regras

```python
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl

# Cria as variáveis do problema - automóvel
velocidade = ctrl.Antecedent(np.arange(0, 200, 1), 'velocidade')
temperatura = ctrl.Antecedent(np.arange(16, 30, 1), 'temperatura')
consumo = ctrl.Consequent(np.arange(5, 25, 1), 'consumo')

# Cria automaticamente o mapeamento entre valores nítidos e difusos 
# usando uma função de pertinência padrão (triângulo)
consumo.automf(names=['pequeno', 'médio', 'grande'])


# Cria as funções de pertinência usando tipos variados
velocidade['baixa'] = fuzz.trapmf(velocidade.universe, [0, 0, 30, 60])
velocidade['média'] = fuzz.trapmf(velocidade.universe, [50, 70, 120, 150])
velocidade['alta'] = fuzz.trapmf(velocidade.universe, [110, 140, 200, 200])

temperatura['baixa'] = fuzz.trapmf(temperatura.universe, [16, 16, 20, 25])
temperatura['alta'] = fuzz.trapmf(temperatura.universe,[20, 25, 30, 50])

```

## Gerando gráficos

```python
velocidade.view()
temperatura.view()
consumo.view()
```

