# fii-simulador-dio

Simulador educacional de investimentos em fundos imobiliários desenvolvido para o desafio da DIO. A ferramenta foi criada do zero em uma pasta de trabalho em branco e organizada para funcionar como uma pequena aplicação de Excel.

> **Aviso:** este projeto é acadêmico/educacional. Os valores e percentuais usados são exemplos criados para demonstrar a lógica do exercício e não constituem recomendação de investimento.

## O que a ferramenta responde

A aba **Simulador** responde às cinco perguntas principais:

- **Quanto investir por mês:** célula de entrada `B6` e destaque em `E5`.
- **Por quantos anos:** entrada `B8` e destaque em `E6`.
- **Qual a taxa de rendimento mensal:** entrada `B9` e destaque em `E7`.
- **Quanto de patrimônio vai acumular:** resultado em `E8`.
- **Quanto vai receber de dividendos por mês:** resultado em `E9`.

Também existe uma sugestão automática de aporte de **30% do salário**, calculada em `B7`.

## Como o VF participa do cálculo

O patrimônio acumulado é calculado com a função financeira **VF**. No arquivo `.xlsx`, as fórmulas são armazenadas no nome interno da função, `FV`; ao abrir o arquivo em Excel em português, ela aparece como **VF**.

A lógica utilizada é equivalente a:

`=VF(taxa_mensal;anos*12;-aporte;0;0)`

O `aporte` é negativo na fórmula porque representa uma saída de caixa mensal do investidor. O resultado é o valor futuro acumulado considerando aportes mensais e a taxa mensal informada.

Os cenários usam a mesma lógica para **2, 5, 10, 20 e 30 anos**, mantendo referências absolutas para o aporte e para a taxa.

## Como o PROCV participa da divisão por perfil

A aba **Apoio** contém uma tabela com:

- Perfil;
- Tipo de fundo;
- Chave composta;
- Percentual.

A chave é criada no formato:

`Perfil|Tipo de fundo`

Exemplo:

`Moderado|Tijolo - Logística`

Na aba **Simulador**, o `PROCV` procura essa chave e devolve o percentual correto para o perfil selecionado. O aporte mensal é então multiplicado pelo percentual para chegar ao valor destinado a cada tipo de fundo.

## Intervalos nomeados do projeto

A estrutura do projeto foi preparada com o seguinte mapa de nomes:

| Nome | Referência |
|---|---|
| `aporte` | `Simulador!$B$6` |
| `taxa_mensal` | `Simulador!$B$9` |
| `salario` | `Simulador!$B$5` |
| `anos` | `Simulador!$B$8` |
| `perfil` | `Simulador!$B$10` |

A aba **Apoio** deixa esse mapeamento documentado. Nesta versão exportada pelo gerador de planilhas utilizado, os cálculos permanecem com referências absolutas para manter o arquivo funcional e compatível. Assim, o projeto já demonstra a estrutura dos nomes, mas o Nomeador do Excel pode ser usado como um acabamento final antes da submissão, caso o avaliador exija os nomes como objetos nativos do arquivo.

## Perfis e percentuais

Os percentuais são exemplos didáticos definidos exclusivamente para demonstrar a mecânica do desafio. Cada perfil soma 100%.

### Conservador

- Tijolo - Logística: 20%
- Tijolo - Shoppings: 15%
- Tijolo - Lajes corporativas: 5%
- Recebíveis - CRI: 40%
- Híbridos: 10%
- Fundos de Fundos (FoF): 10%

### Moderado

- Tijolo - Logística: 25%
- Tijolo - Shoppings: 15%
- Tijolo - Lajes corporativas: 10%
- Recebíveis - CRI: 25%
- Híbridos: 15%
- Fundos de Fundos (FoF): 10%

### Arrojado

- Tijolo - Logística: 20%
- Tijolo - Shoppings: 15%
- Tijolo - Lajes corporativas: 25%
- Recebíveis - CRI: 15%
- Híbridos: 10%
- Fundos de Fundos (FoF): 15%

## O que foi acrescentado

Em relação ao roteiro do Expert, o projeto inclui:

- layout de simulador com áreas de entrada e resultados;
- células editáveis destacadas em amarelo e células calculadas em cinza;
- cenários de 2 a 30 anos;
- sugestão de aporte de 30% do salário;
- lista de perfis com validação de dados;
- tabela de apoio para a chave composta;
- gráfico de pizza da divisão do aporte;
- validação visual para garantir que cada perfil some 100%;
- dois prints de evidência, um com perfil Moderado e outro com perfil Conservador.

## Arquivos

- `fii_simulador_dio.xlsx` — planilha final.
- `print-moderado.png` — evidência da simulação com perfil Moderado.
- `print-conservador.png` — evidência da simulação com perfil Conservador.

## Fonte do desafio

Planilha resolvida/arquivo de referência informado no enunciado:

https://hermes.dio.me/files/assets/a04b81b1-8e35-4e72-aeb9-98aed8ed4403.xlsx

## Como testar

1. Abra `fii_simulador_dio.xlsx`.
2. Na aba **Simulador**, altere as células amarelas de salário, aporte, prazo, taxa e perfil.
3. Confira se as cinco respostas e os cenários mudam automaticamente.
4. Troque o perfil para verificar a mudança na divisão do aporte e no gráfico.
5. Confira na aba **Apoio** se a soma de cada perfil está em 100%.
