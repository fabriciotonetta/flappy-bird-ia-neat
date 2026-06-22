# Como apresentar este projeto a um recrutador

## Versão curta (30 segundos, tipo "elevator pitch")

"Eu desenvolvi um projeto onde uma Inteligência Artificial aprende a
jogar Flappy Bird sozinha, sem eu programar nenhuma regra de 'como
jogar'. Usei um algoritmo genético chamado NEAT, que evolui redes
neurais ao longo de gerações: começa com IAs completamente aleatórias
e, através de seleção natural simulada, elas vão melhorando até
conseguirem jogar bem. O projeto também mostra visualmente, em tempo
real, a rede neural 'pensando' enquanto decide pular ou não."

## Versão completa (para entrevista técnica)

"O projeto recria o Flappy Bird do zero em Python com Pygame e treina
uma população de 50 redes neurais simultaneamente, usando a biblioteca
NEAT-Python. Cada rede recebe como entrada a posição do pássaro e a
distância até o próximo obstáculo, e decide se deve pular. A cada
geração, avalio o desempenho de cada rede através de uma função de
fitness — dando pontos por tempo de sobrevivência e por obstáculos
ultrapassados — e o próprio algoritmo NEAT cuida da seleção, cruzamento
e mutação genética para gerar a próxima geração.

Um desafio técnico interessante foi que, ao desenvolver no Google
Colab, que é um ambiente sem tela física, precisei configurar uma tela
virtual e capturar os frames do jogo para gerar vídeos de demonstração.
Também identifiquei e corrigi um gargalo de performance: o treinamento
estava levando 6 horas porque eu estava renderizando graficamente cada
frame durante o treino inteiro; ao remover essa renderização do loop
de treinamento (mantendo-a só na demonstração final com o melhor
resultado), o tempo caiu para poucos minutos."

## Pontos a destacar, se perguntarem "o que você aprendeu?"

- Como representar um problema de decisão em tempo real como entradas
  e saídas de uma rede neural.
- Como funciona aprendizado evolutivo (NEAT), diferente de redes
  neurais treinadas por backpropagation tradicional.
- Depuração de bugs sutis de lógica (que não geram erro, só
  comportamento incorreto) através de observação cuidadosa.
- Otimização de performance identificando o real gargalo de um
  processo (renderização gráfica vs. cálculo puro).
- Adaptação a mudanças de versão de bibliotecas, lendo e interpretando
  mensagens de erro para corrigir configurações.

## Se perguntarem "por que esse projeto, e não outro mais comum?"

"Escolhi esse projeto porque ele me obrigou a entender, na prática,
conceitos fundamentais de IA — redes neurais, funções de fitness,
seleção e mutação — sem depender de um dataset pronto ou de uma
biblioteca que já resolve tudo. Eu precisei pensar em como traduzir o
'jogar bem' em números (fitness), e isso me deu uma base muito mais
sólida do que só rodar um modelo pré-treinado."
