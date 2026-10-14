---
name: bolo-de-camadas
description: Edita um vídeo falado (você falando para a câmera) num reel vertical 1080×1920 com motion graphics em 5 camadas — o take, a legenda palavra por palavra, o rosto num card, gráficos que desenham o que você fala, zoom e som em cada movimento — com o Claude Code e o Remotion (ou HyperFrames). Tem estilos prontos por nicho (corretor de imóveis, personal trainer, professor de inglês, chef, finanças) e um modelo para criar o estilo de qualquer outra profissão. Use quando a pessoa quiser editar um reel/vídeo falado, fazer motion graphics, legendas animadas, ou mencionar um desses nichos.
---

# Bolo de camadas

Um reel falado bem editado é um bolo de **5 camadas**, uma em cima da outra. A pessoa só grava a fala; o resto é código.

1. **O take** — a fala gravada (já cortada pela pessoa). É a base: não recorte nem mude a cor sem pedirem.
2. **A legenda** — palavra por palavra, cada uma no seu tempo (transcrição com tempos), 1 a 3 palavras por vez, a palavra de ênfase destacada.
3. **O rosto num card** — o take recortado num quadro (cartão, faixa, janela, bolha ou tela cheia), que muda de formato quando o assunto muda.
4. **O gráfico** — em cima, um visual que desenha o que está sendo falado, sincronizado na palavra. Um visual novo a cada 2–3 s.
5. **Zoom e som** — zoom no rosto nas palavras de ênfase e um efeito sonoro em cada movimento.

## Primeiro: qual é o nicho?

Se a pessoa ainda não disse, pergunte qual estilo ela quer e mostre as opções:

| Nicho | Arquivo | Visual |
|---|---|---|
| Corretor de imóveis | `nichos/corretor.md` | editorial, escuro quente com dourado, fotos do imóvel e planta |
| Personal trainer | `nichos/personal.md` | transmissão esportiva, preto com verde-lima, números grandes |
| Professor de inglês | `nichos/ingles.md` | lousa de giz, correção em vermelho, marca-texto |
| Chef | `nichos/chef.md` | cozinha alegre, cartão de receita, checklist de ingredientes |
| Finanças | `nichos/financas.md` | painel de dados escuro, barras, curva de crescimento |
| Outra profissão | `nichos/novo-nicho.md` | crie o estilo com a pessoa a partir do modelo |

Leia **só** o arquivo do nicho escolhido. Para outra profissão, siga `nichos/novo-nicho.md`, monte o estilo junto com a pessoa e salve como `nichos/<profissao>.md` antes de editar.

## O passo a passo (5 passos)

1. **Pasta e projeto.** Num terminal: `mkdir meu-reel && cd meu-reel`, crie o projeto (`npx create-video@latest` para Remotion, ou `npx hyperframes init meu-reel --resolution portrait` para HyperFrames) e abra o `claude` dentro da pasta. Coloque o take na pasta pública do projeto (`public/` no Remotion).
2. **Referências.** Peça 2 ou 3 vídeos de referência (Pinterest, Google, reels que a pessoa goste) e guarde em `refs/`. Você não assiste vídeo: extraia quadros para olhar (`ffmpeg -i refs/ref-1.mp4 -vf fps=1 refs/ref-1-%02d.jpg`) e anote o que copiar (ritmo, tipo de transição, como o texto entra), sem copiar marcas nem conteúdo alheio.
3. **Roteiro de diretor, passo a passo.** Transcreva o take com tempos (no Remotion: `@remotion/install-whisper-cpp`; confira nomes próprios e números). Monte uma tabela de cenas — tempo, palavras faladas, formato do rosto, o que entra e como se mexe — e **mostre para a pessoa aprovar antes de escrever o código**. Escreva como um diretor: "texto que se mexe", "uma forma virando outra", "câmera em movimento", "imagens 3D", com detalhes.
4. **Código e render.** Escreva as cenas, confira no preview (`npx remotion studio`) e gere quadros de teste (stills) dos momentos principais para a pessoa ver. Só depois do OK, renderize: `npx remotion render` (ou `npx hyperframes render`). O vídeo é desenhado quadro a quadro.
5. **Ajustes falando.** A pessoa pede em palavras ("deixa mais suave", "troca um pouco essa cor", "esse texto entra cedo"). Mude curvas, durações, cores e tempos; mostre de novo antes de renderizar o final.

## Regras comuns a todos os nichos

**Formato e áreas seguras** (master 1080×1920, 30 ou 60 fps):
- Gráficos em y=250–800; rosto em y=820–1300; legenda por volta de y=1360–1480.
- A interface do Instagram cobre a parte de baixo a partir de y=1520 e a coluna da direita (~130 px, os botões): nada importante ali.
- Margens laterais ≥90 px. O primeiro quadro é a capa: o título do gancho já aparece inteiro no quadro 1.

**Sincronia:** cada visual entra na palavra que o nomeia (uns 4 quadros antes dela). Um visual novo a cada 2–3 s; mude o formato do rosto ou o fundo a cada ~5 s para não cansar.

**Os efeitos** (use os do estilo do nicho, com moderação — cada efeito precisa de uma função):
- *Texto que se mexe*: letras ou palavras entram uma a uma (atraso de ~0,1 s entre elas), com peso e direção; a palavra de ênfase ganha cor ou escala.
- *Forma virando outra*: em vez de um card novo surgir do nada, a forma que está na tela se transforma na próxima (círculo → estrela, barra → curva, etiqueta → quadro).
- *Câmera em movimento*: aproximação lenta, panorâmica entre elementos, um leve balanço contínuo para nada ficar parado.
- *3D*: um cartão que gira no eixo, camadas em perspectiva, uma planta que se levanta.
- *Chegadas suaves*: ease-out (rápido no início, assentando devagar) em ~0,5–0,7 s, saindo de um leve desfoque e de 94 % do tamanho. Sem "mola" exagerada que passa do ponto, a não ser que o nicho peça energia (personal).
- *Rastro*: o que viaja pela tela deixa um rastro curto; marcas claras sobre fundo escuro podem ter um brilho leve.

**Som:**
- Um efeito em cada batida visual: *whoosh* nas transições, *pop* ou *click* no que chega, *riser* + impacto nas revelações.
- Texto que se digita na tela tem som de teclado durante exatamente o tempo da digitação (se a pessoa estiver falando o texto, sem teclado).
- Use bibliotecas livres (Mixkit, Freesound CC0) e nunca sons de marcas.
- A voz fica por volta de −20 LUFS; os efeitos mais altos 3–6 LU abaixo dela. Música só se pedirem, bem baixa (uns 15 LU abaixo da voz).

**Honestidade:**
- Logos reais (do site oficial ou Wikimedia) sempre que a fala citar uma marca.
- Prints e fotos reais, com autorização.
- Nunca invente números, preços, resultados, depoimentos ou telas de app; se for ilustração ou simulação, escreva isso na tela.

**Antes do render final:** mostre stills dos momentos principais e confira no celular se nada fica atrás da interface do Instagram.

Exemplos de pedidos prontos em `exemplos/prompts.md`.
