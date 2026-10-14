# Nicho: finanças

Painel de dados escuro e legível. Para explicar juros, aportes e hábitos com números claros.

## Cores e fontes
- Azul profundo de `#0E2A44` até `#050B16`, vidro `rgba(8,16,32,0.82)`, verde `#00D27A`, ouro `#F5C451`, branco azulado `#EAF2FF`.
- Google Fonts: **JetBrains Mono** (números e ticker) e **Inter** (explicações). Carregue antes do render.

## Fundo
Dashboard de painéis escuros com grade azul discreta e bordas de vidro. Grade de meses, barras que separam aporte e juros, curva de crescimento contra a linha dos aportes, relógio quando se fala de tempo. A nota "Simulação, rendimento não garantido" perto dos números.

## Rosto (camada 3)
- O take num cartão escuro ou numa janela lateral que não cobre os números.
- Alterne cartão central, faixa larga e janela ao passar da hipótese para o resultado.
- Rosto dentro do recorte; sem zoom que distorça os gráficos.

## Gráficos por fala (camada 4)
- A hipótese aparece antes do valor.
- A grade de meses se preenche aos poucos; barras e contador crescem de forma coerente.
- A curva se traça; o relógio gira só quando ele fala de tempo.

## Legenda (camada 2)
Mono, maiúscula, numa faixa escura; a palavra ativa em verde.

## Efeitos
- **Texto**: os valores rolam como um contador (algarismos de largura fixa) até o número certo; o ticker corre devagar no topo.
- **Forma virando outra**: as barras mês a mês se fundem na curva de crescimento; a moeda vira um ponto do gráfico.
- **Câmera**: travelling acompanhando a ponta da curva enquanto ela sobe; aproximação no número final.
- **3D**: os painéis de vidro em camadas, com profundidade, que se afastam quando entra o resultado.
- **Rastro e brilho**: a ponta da curva deixa rastro e o último ponto ganha um brilho verde.
- Movimentos contidos e legíveis: o número fica parado tempo suficiente para ler.

## Cuidados
Calcule e confira cada número e premissa a partir da planilha da pessoa. Não simule lucro real nem prometa retorno; isto não é recomendação de investimento.
