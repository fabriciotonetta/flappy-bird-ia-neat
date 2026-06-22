# 🐦 Flappy Bird com Inteligência Artificial (NEAT)

> Uma IA aprende a jogar Flappy Bird sozinha, evoluindo através de
> algoritmos genéticos (NEAT) e redes neurais artificiais — sem nenhuma
> regra de jogo programada manualmente.

![Status](https://img.shields.io/badge/status-concluído-brightgreen)
![Python](https://img.shields.io/badge/python-3.12-blue)
![NEAT](https://img.shields.io/badge/algoritmo-NEAT-orange)

---

## 🎯 Sobre o projeto

Este projeto recria o clássico jogo Flappy Bird inteiramente em Python
(usando Pygame) e treina uma população de redes neurais para jogar de
forma totalmente autônoma. Não existe nenhuma instrução de "como jogar"
escrita no código — a IA aprende por tentativa, erro e seleção natural
simulada, através do algoritmo **NEAT (Neuroevolution of Augmenting
Topologies)**.

A cada geração, dezenas de redes neurais (pássaros) tentam jogar
simultaneamente. As que sobrevivem mais tempo e passam por mais canos
são consideradas "mais aptas" e geram a próxima geração, através de
cruzamento genético e mutações aleatórias — repetindo esse processo até
a IA jogar bem.

O projeto também inclui uma **visualização em tempo real da rede
neural**, mostrando os neurônios se ativando enquanto a IA decide pular
ou não, durante a demonstração final.

## 🧠 Como funciona o aprendizado (resumo técnico)

- **Entradas da rede neural (o que a IA "vê"):** altura do pássaro,
  distância até o topo do próximo cano, distância até a base do
  próximo cano.
- **Saída da rede neural (o que ela decide):** um valor entre 0 e 1.
  Se maior que 0.5, o pássaro pula.
- **Função de fitness (como ela é avaliada):** pontos por tempo de
  sobrevivência + pontos extras por cada cano ultrapassado, com
  penalidade ao colidir.
- **Evolução:** o NEAT gerencia automaticamente o cruzamento, mutação
  e seleção das redes neurais entre as gerações, podendo até adicionar
  novos neurônios à estrutura da rede durante o processo.

## 🛠️ Tecnologias utilizadas

| Tecnologia       | Função no projeto                                   |
|-------------------|------------------------------------------------------|
| Python            | Linguagem principal do projeto                      |
| Pygame            | Motor gráfico do jogo (física, colisão, desenho)    |
| NEAT-Python       | Algoritmo genético / evolução das redes neurais     |
| OpenCV + FFmpeg   | Geração e conversão dos vídeos de demonstração      |
| Google Colab      | Ambiente de desenvolvimento (com tela virtual Xvfb) |

## 📂 Estrutura do projeto
flappy-bird-ia-neat/

│

├── README.md                  → este arquivo

├── DIARIO_DESENVOLVIMENTO.md  → registro diário do processo de criação

├── notebooks/                 → notebook do Google Colab com todo o código

├── docs/                      → descrição detalhada e texto de apresentação

├── screenshots/                → prints do progresso e resultado final

└── models/                    → configuração do NEAT usada no treinamento

## 🚀 Como executar o projeto

1. Abra o notebook `notebooks/flappy_bird_ia_neat.ipynb` no Google Colab.
2. Execute as células em ordem (ou use "Ambiente de execução → Executar tudo").
3. O treinamento roda automaticamente por 30 gerações (leva poucos minutos).
4. Ao final, é exibido um vídeo com o melhor pássaro treinado jogando,
   junto com o painel visual da rede neural em tempo real.

## 📸 Demonstração

> IA jogando com a rede neural visível em tempo real, controlando o
> pássaro através das decisões tomadas pelos 3 neurônios de entrada.

[print08_ia_jogando_rede_neural.png](https://github.com/fabriciotonetta/flappy-bird-ia-neat/blob/main/screenshots/print08_ia_jogando_rede_neural.png.png)

## 🧩 Desafios técnicos superados

Durante o desenvolvimento, alguns problemas reais de engenharia foram
identificados e resolvidos (detalhes completos no
[diário de desenvolvimento](DIARIO_DESENVOLVIMENTO.md)):

- Geração de vídeo incompatível com players de navegador (correção via
  recodificação para H.264 com FFmpeg).
- Bug de física no pulo do pássaro causado por uma variável que nunca
  era atualizada durante a queda.
- Atualização de parâmetros de configuração do NEAT exigidos por uma
  versão mais recente da biblioteca (`no_fitness_termination`,
  parâmetros `response_*`).
- Otimização de performance: o treinamento levava ~6 horas por
  renderizar graficamente todos os frames de todas as gerações; após
  remover a renderização do loop de treinamento (mantendo-a só na
  demonstração final), o tempo caiu para poucos minutos.

## 📔 Diário de Desenvolvimento

O processo completo de construção do projeto, dia a dia, incluindo
decisões técnicas e aprendizados, está documentado em
[DIARIO_DESENVOLVIMENTO.md](DIARIO_DESENVOLVIMENTO.md).

## 👤 Autor

**Fabricio Tonetta**
Projeto desenvolvido como parte de um portfólio de Inteligência
Artificial e Machine Learning, com foco em algoritmos evolutivos e
redes neurais.
