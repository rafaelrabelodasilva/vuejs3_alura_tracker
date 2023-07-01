# O projeto

Neste projeto que desenvolvi com o curso da Alura, utilizei o famoso framework Vue, conhecido por sua facilidade de uso, eficiência e escalabilidade, tanto em interfaces simples quanto complexas. O Vue fornece um modelo de programação declarativo e é baseado em HTML, CSS e JavaScript.

No decorrer desse projeto, tive a oportunidade de aprender sobre o Vue.js, aprofundar-me na versão 3 e construir minha primeira aplicação do zero.

Durante todo o percurso, pude percorrer todas as etapas do ciclo de vida de uma aplicação, desde o básico até o avançado, aprimorando minha curva de aprendizado em Front-end.

Ao longo desse caminho, explorei desde a Options API até a Composition API, abordando também temas complexos como gerenciamento de estado com Vuex, roteamento com Vue Router, requisições à API com Axios, entre outros.

Tudo isso foi realizado com o objetivo de aprender na prática e me preparar para dominar um dos frameworks mais populares no mercado de desenvolvimento web.

# Como o projeto foi iniciado

* Instalado o vue CLI

`$ npm install -g @vue/cli`

* Criado o projeto com o vue CLI

`$ vue create alura_tracker`

```
Vue CLI v5.0.8
? Please pick a preset: Manually select features
? Check the features needed for your project: Babel, TS, Linter
? Choose a version of Vue.js that you want to start the project with 3.x
? Use class-style component syntax? No
? Use Babel alongside TypeScript (required for modern mode, auto-detected polyfills, transpiling 
JSX)? Yes
? Pick a linter / formatter config: Basic
? Pick additional lint features: Lint on save
? Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
? Save this as a preset for future projects? N
```

* Após finalizado basta acessar o novo diretório e executar o servidor para ser utilizado em desenvolvimento

`$ yarn serve`


# Dependências

* Vue CLI

* Bulma (Framework CSS)<br>
Colar o link dentro do nosso “index.html”
```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css">
```

* Font awesome (Ícones)<br>
No diretório do projeto inserir o comando abaixo no terminal:
`$ npm i --save-dev @fortawesome/fontawesome-free`

No arquivo "main.ts" fazer o import do CSS do Font Awesome, o arquivo ficará similar ao exemplo abaixo:

```
import { createApp } from 'vue'
import App from './App.vue'

import '@fortawesome/fontawesome-free/css/all.css'

createApp(App).mount('#app')
```

# Fazendo o build da aplicação Vue (manualmente)

Quando o app está finalizado é necessário publicá-lo e deixá-lo disponível para o mundo.
Ao digitar o comando abaixo no diretório principal do projeto, irá rodar e começar a entender tudo que fizemos e começar a compilar todos os nossos componentes.

`$ npm run build`

Após finalizado, será apresentado a pasta "dist" com os arquivos JavaScript, um com as dependências e outro com o código. E para o CSS é a mesma coisa, um com as dependências e outro com o código.

Se analisarmos a pasta "dist" veremos o arquivo "index.html" onde tudo está minificado, porque ele está otimizado para a produção. Esse é o código que subiremos para a produção. E dependemos de ter agora um servidor web para "servir" este arquivo.

O que podemos fazer é no "index.html" usar uma lib em NodeJs só para ver se isso está funcionando.
Deve-se entrar no diretório "dist" e instalar um pacote NPM global que vai me simular como se fosse um servidor HTTP.

`$ npm i -g http-server`

Após finalizado basta rodar no terminal o script abaixo ainda no diretório "dist":

`$ http-server`

Após finalizado estará ouvindo na porta 8080. Lembrando que não temos aquele hot reload, ele não vai ficar tentando comunicar para atualizar automaticamente, porque essa é nossa versão de produção.

Conforme criamos nosso projeto utilizando o CLI do Vue, ele já entregou tudo isso pronto, não precisamos configurar nada. Ele vai utilizar o Babel, o webpack tudo por baixo dos panos e vai compilar a nossa aplicação de uma forma que consigamos subir num servidor web.

Fizemos um teste local usando o pacote do NPM HTTP server que vai simular. Agora precisamos pensar num ambiente de verdade. Nós testamos, fizemos o build, vimos que tudo funciona. Mas agora precisamos deixar isso disponível para o mundo, na internet.

# Publicando o app Vue

Será utilizado o <a href='https://vercel.com/dashboard'>Versel</a>.
Deve ser criado uma conta e logado no site.
Autorizar o github (onde repositório da aplicação está armazenada)

Clicar no botão "Continue to Dashboard"

<!-- # alura_tracker

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/). -->
