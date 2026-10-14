# 🎂 Bolo de camadas

**Você só grava a fala. O Claude Code monta o resto: legenda, rosto, gráficos, zoom e som.**

Skill para o Claude Code que edita um vídeo falado (você falando para a câmera) num reel vertical 1080×1920 com motion
graphics, em 5 camadas:

1. **O take** — a sua fala gravada
2. **A legenda** — palavra por palavra, no tempo certo
3. **O rosto num card** — que muda de formato quando o assunto muda
4. **O gráfico** — que desenha o que você está falando
5. **Zoom e som** — zoom na ênfase e um som em cada movimento

Os vídeos são feitos com o [Remotion](https://www.remotion.dev) (vídeo em código React, desenhado quadro a quadro) ou com o
[HyperFrames](https://hyperframes.dev).

Criado por [@cauhi](https://www.instagram.com/cauhi) · [cauhi.com](https://cauhi.com)

---

## Escolha o seu nicho

Quando você usa a skill, o Claude pergunta qual estilo você quer:

| Nicho | Visual |
|---|---|
| 🏠 Corretor de imóveis | editorial, escuro quente com dourado, fotos do imóvel e planta |
| 💪 Personal trainer | transmissão esportiva, preto com verde-lima, números grandes |
| 🇺🇸 Professor de inglês | lousa de giz, correção em vermelho, marca-texto |
| 🧁 Chef | cozinha alegre, cartão de receita, checklist de ingredientes |
| 📈 Finanças | painel de dados escuro, barras e curva de crescimento |
| ✨ Outra profissão | o Claude cria o estilo com você a partir de um modelo |

Todos com os efeitos novos: texto que se mexe, uma forma virando outra, câmera em movimento, 3D e rastro.

Não tem a sua profissão? Comenta **NICHO** e a sua profissão no meu reel que eu crio o estilo. Ou peça para o Claude criar
com o modelo `nichos/novo-nicho.md`.

## O que você precisa

- O **Claude Code** (precisa de um plano pago do Claude ou de uso da API)
- **Node.js** e **ffmpeg** instalados
- Um **vídeo seu falando** (gravado no celular serve), já cortado do jeito que você gosta

## Como instalar

**No Claude Code**
```bash
git clone https://github.com/pcauhi/bolo-de-camadas ~/.claude/skills/bolo-de-camadas
```

**No claude.ai**
1. Baixe o [`bolo-de-camadas.zip`](https://github.com/pcauhi/bolo-de-camadas/releases/latest/download/bolo-de-camadas.zip).
2. No Claude, vá em **Configurações → Capacidades → Skills** e envie o `.zip`.

(Para renderizar o vídeo você precisa do Claude Code no seu computador; no claude.ai dá para planejar o estilo e as cenas.)

## Como usar: os 5 passos

1. **Pasta e projeto**
   ```bash
   mkdir meu-reel && cd meu-reel
   npx create-video@latest
   claude
   ```
   Coloque o seu vídeo na pasta `public/` do projeto e diga:
   > Usa a skill bolo-de-camadas no estilo corretor. O meu take está em public/take.mp4.
2. **Referências** — mande 2 ou 3 vídeos de referência (Pinterest, Google) na pasta `refs/`.
3. **Descreva como um diretor, passo a passo** — texto que se mexe, uma forma virando outra, câmera em movimento,
   imagens 3D. O Claude mostra a tabela de cenas para você aprovar antes de escrever o código.
4. **Render** — o Remotion transforma o código em vídeo, quadro a quadro: `npx remotion render`.
5. **Ajustes falando** — "deixa mais suave", "troca um pouco essa cor".

Mais pedidos prontos em [`exemplos/prompts.md`](exemplos/prompts.md).

## Custos

A skill é grátis. O Claude Code precisa de um plano pago do Claude ou de uso da API. O Remotion é grátis para pessoas
físicas e empresas de até 3 pessoas; acima disso precisa da licença de empresa (veja
[remotion.dev/license](https://www.remotion.dev/license)). O HyperFrames é Apache-2.0.

## Licença

[MIT](LICENSE): use, modifique e compartilhe à vontade, mantendo o crédito.
