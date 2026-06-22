# Descrição Detalhada do Projeto

## Nome do projeto
Flappy Bird com Inteligência Artificial (NEAT)

## Resumo executivo
Recriação do jogo Flappy Bird em Python, na qual uma população de redes
neurais aprende a jogar de forma totalmente autônoma através do
algoritmo evolutivo NEAT (Neuroevolution of Augmenting Topologies),
sem nenhuma regra de decisão programada manualmente.

## Problema resolvido
Demonstrar, na prática, como um algoritmo de aprendizado por reforço
evolutivo pode resolver um problema de controle em tempo real (decidir
"pular ou não" a cada instante) a partir de zero conhecimento prévio,
unicamente por meio de seleção, cruzamento genético e mutação.

## Abordagem técnica
- O jogo foi implementado do zero com Pygame, incluindo física de
  gravidade/pulo, geração procedural de obstáculos e detecção de
  colisão.
- Uma população de 50 redes neurais (genomas) é avaliada simultaneamente
  a cada geração, controlando 50 pássaros independentes no mesmo
  ambiente.
- Cada rede recebe 3 entradas sensoriais (posição do pássaro e
  distâncias até o próximo obstáculo) e produz 1 saída (decisão de
  pular), através de uma rede neural feedforward.
- Uma função de fitness recompensa sobrevivência prolongada e
  ultrapassagem de obstáculos, guiando a pressão seletiva da evolução.
- Ao final do treinamento, o melhor genoma é utilizado em uma
  demonstração com visualização gráfica em tempo real da ativação dos
  neurônios e dos pesos das conexões.

## Resultados obtidos
A população evoluiu de um comportamento aleatório (fitness médio
próximo de zero, nas primeiras gerações) para pássaros capazes de
ultrapassar múltiplos obstáculos consecutivos, evidenciando o
aprendizado progressivo característico da neuroevolução.

## Ambiente de desenvolvimento
Todo o desenvolvimento foi realizado no Google Colab, um ambiente em
nuvem sem interface gráfica nativa. Para viabilizar a execução de uma
aplicação Pygame nesse contexto, foi configurada uma tela virtual
(Xvfb), e os frames renderizados foram capturados e convertidos em
vídeo (OpenCV + FFmpeg) para visualização dentro do próprio notebook.

## Aprendizados e desafios de engenharia
O desenvolvimento envolveu a depuração de bugs de física, incompatibi-
lidades de codec de vídeo, ajustes de configuração por mudanças de
versão de biblioteca, e uma otimização significativa de performance ao
identificar que a renderização gráfica era o principal gargalo de
tempo durante o treinamento (redução de aproximadamente 6 horas para
poucos minutos).
