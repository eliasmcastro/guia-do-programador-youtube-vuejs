<h1 align="center">
  <img alt="Logo" src=".github/logo_vue.png" width="130px" />
</h1>

<h3 align="center">
  Curso de Vue.js
</h3>

<p align="center">
  <a href="https://www.youtube.com/playlist?list=PLJ_KhUnlXUPteacVhunyK5M8SKIadeED0">Curso básico de Vue.js</a>
</p>

<p align="center">Por Victor Lima - Guia do Programador</p>

<p align="center">
  <a href="#como-executar-o-projeto">Como executar o projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="#anotações">Anotações</a>
</p>

<p align="center">Pokedex</p>

<p align="center">
  <img alt="Front-end" src=".github/frontend.png" width="90%">
</p>

## Como executar o projeto

### Requisitos

- [Node.js](https://nodejs.org)

### Clonar este repositório

```bash
git clone https://github.com/eliasmcastro/guia-do-programador-youtube-vuejs.git
```

### Projeto Conceitos

- `cd guia-do-programador-youtube-vuejs/conceitos` para entrar na pasta
- `npm install` para instalar as dependências do projeto
- `npm run serve` para iniciar o servidor de desenvolvimento
- Acessar http://localhost:8080

_Obs: Esse projeto não possui nenhuma lógica que faz sentido, apenas exemplos de conceitos básicos do Vue.js_

### Projeto Pokedex

- `cd guia-do-programador-youtube-vuejs/pokedex` para entrar na pasta
- `npm install` para instalar as dependências do projeto
- `npm run serve` para iniciar o servidor de desenvolvimento
- Acessar http://localhost:8080

Exemplo de listagem e busca de pokémons

## Anotações

### Ambiente de desenvolvimento

- [Node.js & NPM](https://nodejs.org)
  - O Node.js deve ser instalado via [package manager](https://nodejs.org/en/download/package-manager) utilizando o Chocolatey no Windows
    - Instalar o [Chocolatey](https://chocolatey.org/install)
    - Executar `cinst nodejs-lts` para instalar o Node.js
    - Executar `node -v` e `npm -v` para verificar se a instalação deu certo
- [Visual Studio Code](https://code.visualstudio.com)
  - Instalar o Visual Studio Code
  - Extensões
    - Tema do Dracula Official
    - Material Icon Theme
    - Vetur
  - Fontes
    - [Fira Code](https://github.com/tonsky/FiraCode)
- [Vue CLI](https://cli.vuejs.org)
  - O Vue CLI é um sistema completo para o desenvolvimento rápido de Vue.js
  - Para realizar a instalação, execute `npm install -g @vue/cli`

### Criando um projeto

- Executar `vue create nomeprojeto` para criar o o projeto
  - A pasta public é onde fica todos os arquivos acessíveis pelos usuários finais
  - A pasta src é onde fica todo o código da nossa aplicação
  - O arquivo package.json serve para guardar as informações de versões das dependências do projeto
- Executar `npm run serve` para inicializar o servidor em http://localhost:8080
