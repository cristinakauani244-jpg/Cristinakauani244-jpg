## Olá! Eu sou a kauani cristina💎

Sou estudante de Análise e Desenvolvimento de Sistemas na Universidade Cidade de São Paulo (UNICID).

Sou apaixonada pela área de tecnologia e estou sempre em busca de novos conhecimentos, desafios e oportunidades para aprimorar minhas habilidades.
Acredito que cada projeto é uma oportunidade de aprender, evoluir e transformar ideias em soluções!
Vamos nos conectar e compartilhar conhecimento!
## 💻 Linguagens e tecnologias

![Tecnologias](https://skillicons.dev/icons?i=html,css,js,python,figma)

name: generate snake animation

on:
  schedule:
    - cron: '0 */12 * * *'
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: generate snake svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - name: push to the snake-output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: snake-output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

