# 📔 Diário de Desenvolvimento

Aqui registro o progresso, decisões e aprendizados durante a construção
do projeto Flappy Bird com IA (NEAT).

---

## Dia 1 — Planejamento e estrutura inicial

**O que foi feito:**
- Criação do repositório no GitHub
- Definição da estrutura de pastas (notebooks, docs, screenshots, models)
- Escrita do README inicial

**O que aprendi:**
- Repositório é o "histórico versionado" do projeto
- Commits bem descritos contam a "história" de como o projeto foi construído
- Organização de pastas segue padrão usado em projetos reais de IA/Data Science

**Próximos passos:**
- Configurar o ambiente no Google Colab
- Instalar as bibliotecas necessárias (pygame, neat-python)
---

## Dia 2 — Configuração do ambiente

**O que foi feito:**
- Criação do notebook no Google Colab
- Instalação de Pygame e NEAT-Python
- Configuração de uma tela virtual (xvfb) para rodar o jogo
  em um ambiente sem monitor físico

**O que aprendi:**
- Servidores em nuvem não têm tela física, então é preciso simular
  uma ("tela virtual") para rodar aplicações gráficas
- Essa é a mesma técnica usada profissionalmente para testes
  automatizados e treinamento de IA em servidores remotos

**Próximos passos:**
- Programar o jogo Flappy Bird (pássaro, canos, pontuação, colisão)
---

## Dia 3 — Criação do pássaro (Bird)

**O que foi feito:**
- Criação da classe Bird, representando o pássaro do jogo
- Implementação da física de pulo e queda (gravidade, velocidade, ângulo)
- Desenho do pássaro usando formas geométricas (círculos e triângulo)

**O que aprendi:**
- Como simular gravidade e pulo usando fórmulas de movimento acelerado
- Como organizar comportamento e dados de um objeto do jogo usando uma classe em Python
---

## Dia 4 — Criação dos canos (Pipe) e do chão (Base)

**O que foi feito:**
- Criação da classe Pipe, com geração aleatória da altura do espaço (gap)
- Implementação da detecção de colisão entre pássaro e canos
- Criação da classe Base, com efeito de "chão infinito" usando duas faixas

**O que aprendi:**
- Como simular movimento de cenário usando duas cópias de uma imagem/forma
  que se alternam (loop infinito)
- Como detectar colisão entre objetos usando retângulos (bounding boxes)
- Uso de números aleatórios (random) para gerar variação no jogo
---

## Dia 5 — Loop do jogo e primeiro teste visual

**O que foi feito:**
- Criação da função que desenha todos os elementos do jogo em cada frame
- Implementação do loop principal do jogo (mover, verificar, desenhar)
- Captura dos frames do jogo e geração de um vídeo .mp4 para visualização
  dentro do Google Colab (já que não há tela física no ambiente)
- Primeiro teste visual funcional do jogo, com uma decisão de pulo simples
  e temporária (a IA real será implementada na próxima etapa)

**O que aprendi:**
- Estrutura clássica de um "game loop": mover → verificar regras → desenhar
- Como capturar frames de uma aplicação Pygame e transformá-los em vídeo
  usando OpenCV, contornando a limitação de não haver tela física no Colab

**Próximos passos:**
- Substituir a decisão de pulo simples pela Inteligência Artificial (NEAT)
- Treinar uma população de pássaros simultaneamente
---

## Dia 6 — Correção de bugs no teste visual

**O que foi feito:**
- Identificado que o vídeo gerado pelo OpenCV (codec mp4v) não era
  reproduzido corretamente nos players de navegador; corrigido
  convertendo o vídeo para o codec H.264 usando ffmpeg
- Corrigido bug na lógica provisória de pulo do pássaro: a condição
  inicial verificava uma variável (`velocidade`) que nunca era
  atualizada durante a queda, fazendo o pássaro nunca pular
- Ajustada a condição de pulo para se basear na posição vertical do
  pássaro (`y > 600`), mantendo-o numa faixa de altura estável

**O que aprendi:**
- Nem todo arquivo de vídeo "válido" é reproduzível em qualquer player;
  o codec de gravação importa para compatibilidade com navegadores
- Importância de testar e observar o comportamento visual do jogo
  cuidadosamente, pois bugs de lógica nem sempre geram erros/avisos,
  apenas comportamento incorreto
- A função de teste visual ainda não verifica colisão entre o pássaro
  e os canos — isso será implementado formalmente na Etapa 5, junto
  com a lógica completa do jogo e a IA
---

## Dia 7 — Configuração do NEAT

**O que foi feito:**
- Criação do arquivo de configuração do NEAT (config-feedforward.txt)
- Definição da estrutura da rede neural: 3 entradas (altura do pássaro,
  distância até o topo e até a base do próximo cano) e 1 saída (pular ou não)
- Definição do tamanho da população (50 redes neurais por geração)

**O que aprendi:**
- O que é o algoritmo NEAT e como ele evolui redes neurais através de
  seleção, cruzamento e mutação, sem precisar de exemplos prontos
- Como definir entradas e saídas de uma rede neural de acordo com o
  problema que ela precisa resolver
- Estrutura de um arquivo de configuração do NEAT-Python
---

## Dia 8 — Suporte a múltiplos pássaros e colisão ativa

**O que foi feito:**
- Criação da função "encontrar_cano_proximo", que identifica qual cano
  cada pássaro deve observar para tomar decisões
- Adaptação do loop do jogo para suportar uma lista de vários pássaros
  simultâneos, cada um avaliado de forma independente
- Ativação da detecção de colisão: pássaros que batem em canos ou saem
  da tela são removidos da população em tempo real
- Atualização da função de salvar vídeo para já converter automaticamente
  para o codec H.264 (correção da etapa anterior incorporada de forma definitiva)

**O que aprendi:**
- Como gerenciar uma lista de objetos que precisa ser modificada (remoção
  de itens) durante o próprio loop que a percorre, sem causar erros
- Por que percorrer listas de trás para frente ao remover itens evita
  bugs de "saltar" elementos
- Como cada "indivíduo" de uma população em NEAT é avaliado de forma
  independente, mas compartilhando o mesmo ambiente (os mesmos canos)
