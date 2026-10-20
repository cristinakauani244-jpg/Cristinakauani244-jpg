## Olá! Eu sou a kauani cristina💎

Sou estudante de Análise e Desenvolvimento de Sistemas na Universidade Cidade de São Paulo (UNICID).

Sou apaixonada pela área de tecnologia e estou sempre em busca de novos conhecimentos, desafios e oportunidades para aprimorar minhas habilidades.
Acredito que cada projeto é uma oportunidade de aprender, evoluir e transformar ideias em soluções!
Vamos nos conectar e compartilhar conhecimento!
## 💻 Linguagens e tecnologias

![Tecnologias](https://skillicons.dev/icons?i=html,css,js,python,figma)


![Meus stats](https://github-readme-stats.vercel.app/api?username=cristinakauani244-jpg&show_icons=true&theme=dark)

![Linguagens](https://github-readme-stats.vercel.app/api/top-langs/?username=cristinakauani244-jpg&layout=compact&theme=dark)

<img height="150" src="https://github-readme-stats.vercel.app/api?username=cristinakauani244-jpg&show_icons=true&theme=dark" />
<img height="150" src="https://github-readme-stats.vercel.app/api/top-langs/?username=cristinakauani244-jpg&layout=compact&theme=dark" />

name: generate pacman graph

on:
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 20
    steps:
      - name: generate contribution graph SVGs
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}
          games: 'pacman'

      - name: push SVGs to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

 
