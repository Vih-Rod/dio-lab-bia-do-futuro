# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve no Professor Fortuna? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores, ou seja, dar continuidade no atendimento de forma mais eficiente.  |
| `perfil_investidor.json` | JSON | Personalizar as explicações sobre as dúvidas e necessidades de aprendizado do cliente |
| `produtos_financeiros.json` | JSON | Conhecer os produtos disponíveis para que elas possam ser ensinados ao cliente. |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e usar essas informações de forma didática.|

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Existem duas possibilidades, injetar os dados diretamente no prompt (Ctrl+ C, Ctrl+ V) ou carregar os arquivos via código.

```python
import panda as pd
import json

#CSVs
historico - pd.read_csv('data/historico_atendimento.csv')
transacoes - pd.read_csv('data/transacoes.csv')

#JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
     perfil = json.load(f)

with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
     produtos = json.load(f)

```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

```text
Dados do cliente: 

Perfil do cliente:

Transacoes do cliente:

Produtos disponíveis para ensino:
```

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
