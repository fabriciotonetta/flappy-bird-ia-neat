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
