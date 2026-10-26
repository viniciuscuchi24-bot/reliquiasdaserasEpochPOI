# Relíquias das Eras

Jogo de plataforma 2D (estilo metroidvania) pelas 30 épocas da história, do Paleolítico à Segunda Guerra (com duas fases do Brasil: Colonial e Imperial).
O visual vem todo da pasta `assets/`, como num jogo normal: trocou a imagem, mudou o jogo.

## Como jogar

- **Versão única (celular e computador)**: `reliquias-das-eras.html`, o jogo inteiro num arquivo só (feito por
  `python3 ferramentas/montar_arquivo_unico.py`). Abre direto no navegador, sem instalar nada e sem internet.
  A pasta do projeto também roda: dois cliques em `index.html` (se o navegador bloquear, rode
  `python3 -m http.server 8000` dentro da pasta e abra `http://localhost:8000`).
- **Tela de início**: Novo jogo, Continuar (volta para o último marco de descanso salvo) e Opções.
  Depois de zerar uma vez, Novo jogo pergunta o modo (História ou Crônicas do Fim).
- **Salvar**: no **marco de descanso** aperte E (ou o botão E no celular): a vida volta e abre o menu com
  Salvar jogo, Opções, Salvar e sair e Levantar. O cristal girando no canto mostra quando está salvando/carregando.
  O progresso (época, moedas, espadas, habilidades, diário, trechos vencidos, runas) fica num banco de dados do
  próprio navegador (IndexedDB; se não der, localStorage). **Cada cópia do jogo tem o seu próprio jogo salvo**
  (e suas opções e o desbloqueio das Crônicas): uma cópia em outra pasta ou com outro nome começa do zero. Para manter
  o progresso ao atualizar, substitua o arquivo antigo pelo novo, com o mesmo nome e no mesmo lugar.
  Nas Crônicas do Fim, morrer apaga o jogo salvo desse modo.
- **Pausa**: Esc (ou Start no controle, ou o botão Menu no celular): Continuar, Opções, Sair para o início.
- **Opções**: Vídeo (tela cheia, brilho, limite de FPS 30/60/sem limite, mostrar FPS, pixels nítidos, tremor da
  tela), Som (volume da música e dos efeitos), **Botões de toque** (mostrar automático/sempre/nunca e a
  **transparência** dos botões, de 0 a 80%, com prévia na hora) e **Controles**: troque a
  tecla do teclado e o botão do controle (gamepad) de cada ação; "Restaurar padrão" volta ao original.
  Tudo fica guardado no navegador.
- **Controles padrão** — teclado: setas ou A/D andar · Espaço pular · X (ou clique) golpe (↑/↓ + golpe = para
  cima / para baixo no ar) · Z, Shift (ou clique direito) esquiva · segure F curar · **R arremessa a cabeça de
  abóbora** (só com o tanque de energia cheio) · E interagir · B Diário · M mapa · Esc pausa · N música · V estilo.
  Controle (Xbox/PlayStation): analógico ou direcional anda · A pular · X golpe · B esquiva · Y curar · RB cabeça ·
  LB interagir · LT diário · Select mapa · Start pausa. Nos menus: direcional escolhe, A confirma, B volta.
- **Vida e energia**: cada máscara de vida é uma **lanterna**; ao levar dano as lanternas trincam e estouram
  (uma por ponto de dano), e acendem de novo ao curar. A energia é o líquido verde da **esfera**; cheia, ela pulsa.
  Com **1 de vida** a abóbora vira lanterna de Halloween: olhos acesos vazando luz amarela, aura quente e
  pedaços de abóbora caindo. Ao **curar** (segurar F), uma aura verde envolve o personagem (`assets/interface/aura_cura.png`).
- **Cabeça de abóbora (R)**: explode no inimigo ou no chão; atravessa as plataformas suspensas (finas, móveis e blocos
  soltos no ar). Nem ela nem a espada atravessam paredes ou portões fechados.
- **Espadas e loja**: cada fase tem um **mercador** ao lado do marco de descanso que vende as espadas (cada uma
  aparece a partir da época em que foi inventada) e o **Diário dos Monstros**. As moedas vêm dos monstros
  derrotados e dos chefes. Preços, alcance e dano ficam na lista `SW` de `js/nucleo.js`; as moedas por monstro
  em `MOEDAS_TIPO`.
- **Final**: depois da última época vêm os créditos (rolando sobre `assets/interface/creditos_fundo.webp`) e a
  mensagem final. Na primeira vez que alguém termina, libera o modo **Crônicas do Fim**: morreu, acabou; os
  chefes têm 60% a mais de vida e cada golpe deles quebra duas lanternas. Nomes e mensagem: começo de `js/final.js`.
- **No celular**: os controles de toque aparecem sozinhos (joystick à esquerda; Golpe, Pular, Esquiva, Curar, E e
  Cabeça à direita; Menu, Diário, tela cheia, Estilo, música e Mapa em cima). Melhor com o celular deitado.
  Nos menus é só tocar no item. No iPhone, para tela cheia: Compartilhar → "Adicionar à Tela de Início".

## No site

O jogo também está no site **https://reliquias-das-eras-projeto-epoch-poi.lovable.app/jogar/index.html** (botão ▶ JOGAR). O site é o
projeto do Lovable ligado ao repositório `viniciuscuchi24-bot/reliquias-das-eras-projeto-epoch-poi`; o jogo fica na
pasta `public/jogar/` de lá. Para atualizar o jogo no site: copie `index.html`, `creditos.html`, `js/` e `assets/`
(menos `assets/personagem/`) para `public/jogar/`, envie para o GitHub e clique em **Publicar** no Lovable.
Aberto pelo site, o menu do jogo ganha **Voltar ao site**.

Na primeira visita aparece uma tela de **carregamento** (o cristal e uma barra) enquanto as imagens baixam; sem
ela, o jogo mostraria por alguns instantes os desenhos simples feitos por código até cada imagem chegar. As imagens
dos chefes continuam baixando por trás durante o jogo, e ao trocar de sala a tela fica preta até a sala nova estar
pronta. Da segunda vez em diante o navegador já tem tudo guardado e a tela nem aparece.

## Pastas

O projeto vem em dois zips para caber no limite de 20 MB: `reliquias-das-eras-projeto.zip` (o jogo, o código e as
ferramentas) e `reliquias-das-eras-artes-originais.zip` (as fontes pesadas das artes: `ferramentas/fotos/`,
`ferramentas/referencias/` e as folhas `*_folha`). Descompacte os dois no mesmo lugar: eles se juntam na mesma pasta.
O jogo roda só com o primeiro; o segundo só é preciso para refazer artes com as ferramentas.


```
index.html              página do jogo: layout, controles de toque e tamanho da tela; carrega os arquivos abaixo
js/
  config.js             estilo inicial e caminhos dos sons
  dados.js              as 30 épocas (nomes, textos das runas)
  nucleo.js             física, inimigos, combate
  fases.js              monta cada fase: área inicial (runa, marco, mercador) + trechos com portões (tabela PLANO), peças móveis
  entrada.js            teclado, mouse e controle (gamepad) com teclas trocáveis; as opções guardadas no navegador
  loja.js               o mercador (loja de espadas) e o Diário dos Monstros
  salvar.js             o progresso salvo (IndexedDB, com reserva no localStorage) e o cristal de salvar/carregar
  menus.js              tela de início animada, Opções (vídeo, som, controles), menu do marco de descanso e pausa
  final.js              créditos, mensagem final e o modo Crônicas do Fim
  trechos.js            os 9 tipos de trecho, com variantes de desenho (A, B, C), e suas regras
  chefes.js             os 4 chefes (como lutam) e um desenho simples de reserva; a Máquina Enigma voa pela arena
                        com os rotores girando em volta e desce para recarregar (hora de bater)
  chefes_arte.js        desenha os chefes, ataques e ajudantes com as imagens de assets/chefes
  arenas.js             o cenário próprio de cada luta contra chefe (Coliseu, navio, fábrica, casamata)
  interface.js          caixas de texto em pergaminho, barra de vida dos chefes, fonte de pixel dos menus,
                        lanternas da vida (quebrando) e a esfera do tanque de energia
  recursos.js           carregador de imagens
  carregando.js         tela de carregamento (baixa as imagens antes do título) e espera da sala nova
  cenario.js            desenha terreno, plataformas, objetos, fundo e camadas a partir do estilo
  efeitos.js            efeitos animados: rio, água/lava/lama nos fossos, partículas no ar
  personagem.js         desenha o personagem (parado, andar, pulo, queda, golpes, dano, morte), o rastro dos golpes,
                        as asas do pulo duplo e a abóbora acesa com 1 de vida
  monstros.js           desenha os inimigos a partir das folhas de sprite (parado, andando, ataque, dano, morte)
  desenho.js            monta cada quadro (fundo, mundo, inimigos, jogador, interface)
  toque.js              controles de celular, música e sons
assets/
  audio/                musica.mp3, pulo.mp3, esquiva.mp3 e chefes/ (a música de cada luta contra chefe)
  hallokin/             o personagem em uso (Hallokin): hallokin.png (corpo, uma linha por animação), golpes.png
                        (rastro laranja dos golpes), impactos.png, cabeca.png (a abóbora do R), asas.png, hallokin.js e
                        olhos.png/olhos.js (os olhos acesos com 1 de vida, mesma grade da folha)
  personagem/           o personagem antigo (o cronista, uma roupa por época) — não é carregado; veja abaixo como voltar
  monstros/             monstros.js (manifesto) + cogumelo/, golem_laranja/, voador/ (uma imagem por animação);
                        monstros_era.js + automato/, caldeira/, ornitoptero/ (épocas industriais) e tanque/, mina/,
                        zepelim/ (guerras do século XX) — trocam o desenho dos monstros nessas épocas
  objetos/              objetos.png + objetos.js: runas, fragmentos, alavancas, braseiros, portões, espinhos
  chefes/               chefes.js (manifesto) + legionario/, espectro/, colosso/, enigma/ (animações, ataques, retrato)
  interface/            interface.js + caixa.png (pergaminho das caixas de texto), a moldura/barra de vida dos chefes,
                        espadas.png (ícones da loja), creditos_fundo.webp (a pintura dos créditos),
                        lanterna.png (vida), esfera.png + esfera_vidro.png (tanque), cristal.png (ícone de salvar),
                        fonte.png (fonte de pixel) e os manifestos hud.js e fonte.js
  titulo/               cena.png (a tela de início, 480x270, ampliada 2x), logo.png e titulo.js (posições)
  estilos/
    pantano/            estilo "Pântano encantado"
      estilo.js         recortes e regras deste estilo (o "mapa" das imagens)
      imagens/          arte do pacote (terreno, objetos, camadas)
      fundos/           e0.webp … e29.webp: fundo de cada época (foto real + céu do estilo)
    cemiterio/          estilo "Cemitério gótico" (mesma organização)
ferramentas/
  montar_cenarios.py    gera os fundos das épocas a partir das fotos
  fotos/                01.jpg … 30.jpg (fotos reais; 15 e 22 são pinturas, veja abaixo) e creditos.json
  pintar_cenas_brasil.py  pinta as cenas do Brasil Colonial (fotos/15.jpg) e Imperial (fotos/22.jpg); depois
                        rode python3 ferramentas/montar_cenarios.py 14 21 (dá para trocar por fotos de verdade)
  gerar_monstros_era.py desenha os 6 monstros das épocas industriais e das guerras (assets/monstros/monstros_era.js)
  montar_arquivo_unico.py  gera ../reliquias-das-eras.html: o jogo inteiro num arquivo só (celular e computador)
  pintar_titulo.py      pinta a tela de início em pixel art (floresta, portal com o disco da ampulheta) e o logotipo
  gerar_hud.py          lanternas da vida, esfera do tanque, cristal de salvar e os olhos acesos do Hallokin
                        (a partir das imagens em referencias/)
  gerar_fonte.py        a fonte de pixel dos menus e da HUD (fontes/jersey-10 na grade original, licença SIL OFL)
  referencias/          lanterna.webp, esfera_ui.webp, cristal.gif e aura_cura.gif (as imagens de referência da interface)
  fontes/               Jersey 10 e Jersey 15 (SIL Open Font License, OFL-Jersey.txt)
  hallokin_folha.png    folha original do Hallokin (SHADOW Series - Hallokin, free)
  recortar_hallokin.py  recorta a folha e gera assets/hallokin, inclusive o golpe para baixo (pogo)
  personagem_folha.webp  folha de arte do personagem antigo (uma linha por época)
  recortar_personagem.py  recorta a folha e gera assets/personagem (python3 ferramentas/recortar_personagem.py)
  gerar_asas.py         desenha as asas do pulo duplo (assets/personagem/asas.png)
  gerar_bainha.py       desenha a espada embainhada na cintura, uma por arma (assets/personagem/bainha.png)
  gerar_cortes.py       desenha o golpe: rastro do corte em meia-lua e a espada na mão, um por arma (cortes.png, laminas.png)
  gerar_objetos.py      desenha objetos.png (runas, fragmentos, portões, mercador, diário...) em pixel art
  chefes_folha.webp      folha de arte dos chefes
  recortar_chefes.py    recorta a folha e gera assets/chefes (python3 ferramentas/recortar_chefes.py)
creditos.html           créditos das artes e das fotos
```

## Como mudar o visual

1. **Trocar uma arte**: substitua o arquivo em `assets/estilos/<estilo>/imagens/` por outro com o
   mesmo nome. Se o desenho mudar de lugar dentro da imagem, ajuste o recorte em `estilo.js`.
2. **Recortes**: em `estilo.js` cada peça é `[x, y, largura, altura]` dentro da imagem.
   - `chao.topo`: faixa de cima do chão (repete na horizontal)
   - `chao.ladoEsq / ladoDir`: paredes na beira dos fossos e nas torres (repetem na vertical)
   - `chao.pontaEsq / pontaDir`: quinas (opcional, ex.: lajes de pedra do cemitério)
   - `bloco`: peças próprias para torres e blocos (se faltar, usa as do chão)
   - `espinhos`: qual desenho de espinhos vai no fundo dos fossos
   - `teto.borda` e `teto.tijolo`: borda de baixo do teto e parede repetida
   - `plataforma.esquerda / meio / direita`: as três partes da plataforma fina
   - `objetos`: decoração do chão; `peso` é a chance de aparecer, `escala` o tamanho
   - `camadas`: camadas na frente do fundo, com `parallax` (0 = parada, 1 = anda junto com o chão)
3. **Fundo de uma época**: edite `assets/estilos/<estilo>/fundos/eN.webp` direto (1536x540),
   ou troque a foto em `ferramentas/fotos/` e rode `python3 ferramentas/montar_cenarios.py`
   (precisa de `pip install pillow numpy scipy`).
4. **Personagem (Hallokin)**: `assets/hallokin/hallokin.png` tem uma linha por animação (parado, andar,
   pulo, queda, ataque, ataque no ar, ataque para cima, dano, morte, ataque para baixo) e um quadro por coluna
   (96x96); `golpes.png` tem só o rastro laranja dos golpes, na mesma grade. Nas armas de alcance maior o corte
   se solta e voa até onde a arma acerta. Para refazer tudo a partir da folha original:
   `python3 ferramentas/recortar_hallokin.py` (ele também monta o golpe para baixo, que não existe na folha:
   corpo da queda + rastro do golpe para cima virado para baixo). É o mesmo personagem em todas as épocas.
   **Voltar ao personagem antigo** (o cronista, com uma roupa por época): no `index.html` troque
   `assets/hallokin/hallokin.js` por `assets/personagem/personagem.js`. Os arquivos dele continuam em
   `assets/personagem/` (folhas `eraNN.png`, golpe `cortes.png`/`laminas.png`, bainha; ferramentas
   `recortar_personagem.py`, `gerar_cortes.py`, `gerar_bainha.py`). As asas do pulo duplo são de
   `ferramentas/gerar_asas.py`.
5. **Monstros**: troque os PNG em `assets/monstros/<monstro>/` (uma tira de quadros por animação) e
   ajuste `quadro`, `centro`, `pe`, `escala` e o número de quadros em `assets/monstros/monstros.js`.
6. **Runas, fragmentos, portões**: edite `assets/objetos/objetos.png` num editor de imagem, ou mude os
   desenhos em `ferramentas/gerar_objetos.py` e rode `python3 ferramentas/gerar_objetos.py`.
7. **Caixas de texto e barra de vida dos chefes**: troque `assets/interface/caixa.png`, `vida_moldura.png` e
   `vida_barra.png`; em `assets/interface/interface.js` ficam as margens que não esticam, o vão da barra e as cores do texto.
8. **Estilo inicial**: `estiloInicial` em `js/config.js`.
9. **Criar um estilo novo**: copie a pasta `assets/estilos/pantano` com outro nome, troque o `id`
   e o `nome` dentro do `estilo.js`, ponha suas imagens e acrescente no `index.html`:
   `<script src="assets/estilos/SEU_ESTILO/estilo.js"></script>`. A tecla V passa a incluir ele.

## Como as fases funcionam

Cada época é uma fase longa: área inicial (runa, marco de descanso, item) e depois **trechos**
em sequência, cada um fechado por um portão que só abre quando você vence o desafio:

| Trecho | O que fazer |
|---|---|
| saltos | atravessar vãos (um deles exige a esquiva no ar) e ativar a alavanca |
| espinhos | cruzar um fosso quicando nas estacas (↓ + golpe no ar) |
| escalada | subir numa torre: pulo duplo (Asas) antes de Constantinopla, Garras depois |
| alavancas | acertar 3 alavancas com a espada (uma no alto, outra numa ilha) |
| guardioes | derrotar todos os inimigos do trecho |
| fragmentos | pegar 3 fragmentos nas plataformas e levar ao mecanismo |
| arena | as portas fecham e chegam 3 ondas de inimigos |
| escuro | acender 3 braseiros no escuro (a Lanterna aumenta a visão) |
| corrida | a alavanca abre o portão por poucos segundos |

Cada tipo tem variantes de desenho, e cada época usa uma combinação própria:

| Variante | saltos | espinhos | escalada | alavancas | guardiões | fragmentos | arena | escuro | corrida |
|---|---|---|---|---|---|---|---|---|---|
| A | ilhas e vão longo | estacas em linha | torre | ilha e pendurada | dois lados | escada | plana | dois fossos | três fossos |
| B | pilares no fosso | zigue-zague | degraus / coluna do teto | patamar + fosso | patamar central | pilares | bloco central | no alto + plataforma móvel | obstáculos e teto baixo |
| C | plataformas móveis | estacas que sobem e descem | — | — | fosso com plataforma móvel | — | dois fossos | — | — |

A tabela `PLANO` em `js/fases.js` diz os trechos de cada época, por exemplo `'saltos:C'` — dá para trocar à vontade.
As habilidades (Esquiva Veloz, Asas, Garras, Lanterna) são pegas só de encostar, com explicação na
tela, e o trecho seguinte já pede a habilidade nova.
Durante a fase não aparecem balões de dica (nem nos trechos nem nos chefes): os balões de texto ficam só para
as runas, os fragmentos, o objeto do Presente no fim da fase e as habilidades. O que fazer em cada trecho aparece
curto no canto de cima, e avisos rápidos ("Passagem aberta", "Onda 2 de 3") viram uma linha de texto no alto da tela.
As dicas antigas continuam no código (`dica` em `js/trechos.js` e `DICA_CHEFE` em `js/chefes.js`) para consulta.
O golpe e a explosão da cabeça não atravessam paredes nem portões fechados (`alcancavel` em `js/nucleo.js`).

Chefes (`js/chefes.js`), cada um com sua arena própria (`js/arenas.js`):

| Fase | Chefe | Arena | Como luta |
|---|---|---|---|
| 7 | Legionário de Pedra | ruínas do Coliseu: arcos de pedra, colunas, estandartes, sacadas de mármore, braseiros | escudo bloqueia de frente, investida, lanças, salto |
| 14 | Espectro da Caravela | navio atracado no cais: casco, convés, mastros, vergas (plataformas), velas rasgadas, cordas e o mar | voa, some, mergulha, canhão, onda; chama morcegos |
| 23 | Colosso a Vapor | fábrica: tijolos, janelões, engrenagens, canos, fornalhas, correntes, passarelas | pisão, colunas de vapor, engrenagens; superaquece (dano dobrado) |
| 30 | Máquina Enigma | casamata: concreto, seteiras, sacos de areia, holofote, alarmes, vigas | voa pela arena com três rotores girando em volta do núcleo; raios mirados, colunas de laser, bombardeio, mísseis e drones; desce para recarregar (aí os rotores e, depois, o núcleo ficam ao alcance) |

As arenas se misturam com o estilo escolhido: o chão continua o do estilo (só o navio troca pelo casco),
tudo é pintado em pixels de 2 px, recebe o tom e o escurecimento do estilo e aparece aos poucos na entrada,
com um pontilhado. O que não se mexe é pintado uma vez por fase e depois só copiado (fica leve).

A arte dos chefes vem de `ferramentas/chefes_folha.webp`. Para trocar: edite a folha (ou as imagens em
`assets/chefes/<chefe>/`) e, se mudar a folha, rode `python3 ferramentas/recortar_chefes.py`; as caixas de
recorte de cada animação ficam no começo desse arquivo.

## Música de cada fase

Em `js/config.js`, `musicasPorFase` liga o número da fase a um arquivo de música, por exemplo
`{ 1: 'assets/audio/fases/paleolitico.mp3', 5: 'assets/audio/fases/nilo.mp3' }`.
Fases sem música própria tocam a música principal.

**Música dos chefes**: `musicasChefes` (também em `js/config.js`) liga cada chefe a uma música que toca enquanto ele
está acordado: Legionário → `estudo.mp3`, Espectro → `espirito.mp3`, Colosso → `industria.mp3`, Máquina Enigma →
`sinistro.mp3` (pasta `assets/audio/chefes/`). A troca é suave; quando o chefe cai, a música da fase volta de onde parou.

## O que ainda é desenhado por código

Os cenários das arenas dos chefes (`js/arenas.js`, em pixel art), os efeitos que se mexem (água, lava e lama,
chuva, neve, faíscas), o líquido da esfera, os vaga-lumes e feixes de luz da tela de início e partes da interface
(mapa, diálogos), em `js/efeitos.js`, `js/menus.js`, `js/interface.js` e `js/desenho.js`.

## Créditos e licenças

- Pântano: Fantasy Swamp Forest, de @theflavare. A versão grátis permite usar em jogos e trabalhos
  escolares, mas **não permite modificar nem redistribuir o pacote** (veja `LICENCA_DO_PACOTE.md`).
- Cemitério: pacote "Final", de Anokolisa (uso livre, crédito opcional).
- Monstros: "Forest Monsters FREE" (cogumelo), "Golems Free Version" (golem) e "Flying Forest Enemies FREE"
  (cogumelo voador), pacotes grátis do itch.io.
  Os zips não trazem arquivo de licença: confira a página de cada pacote antes de publicar o jogo.
- Runas, fragmentos, portões e espinhos: desenhados para o jogo (`ferramentas/gerar_objetos.py`).
- Fotos: Wikimedia Commons; autor e licença de cada uma em `creditos.html`.
- Tela de início: pintura feita para o jogo (`ferramentas/pintar_titulo.py`), seguindo o modelo de composição da tela do ARCO (sem usar a arte dele).
- Fonte dos menus e do logotipo: Jersey 10 / Jersey 15 (The Soft Type Project), licença SIL OFL.
- Cristal de salvar/carregar: animação do jogo Duelyst (Counterplay Games), cujos arquivos foram liberados como domínio público (CC0) em 2023.
- Esfera do tanque de energia: recortada da imagem de referência enviada (um kit de interface de jogo; autor não identificado — confira a licença antes de publicar fora da escola).
- Lanterna da vida: redesenhada em pixel art a partir da imagem de referência enviada.
- Aura verde da cura: animação enviada pela equipe (ferramentas/referencias/aura_cura.gif; autor não identificado — confira a licença antes de publicar fora da escola).
