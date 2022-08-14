# Hello SQLite!

Este projeto inclui um script de servidor [Node.js](https://nodejs.org/en/about/) que usa um banco de dados [SQLite](https://www.sqlite.org) persistente. O aplicativo também inclui um front-end com duas páginas da Web que se conectam ao banco de dados usando a API do servidor. 📊

A página inicial apresenta ao usuário uma enquete onde ele pode escolher uma opção e, em seguida, a página apresenta os resultados em um gráfico. A página de administração exibe o log das escolhas anteriores e permite que o usuário o limpe fornecendo uma chave de administrador (você pode configurar isso seguindo os passos em `TODO.md`). 🔒
## Prerequisites

Para obter o melhor uso deste projeto, você deve estar familiarizado com JavaScript e ter um pouco de experiência em Node.js – confira [Hello Node](https://glitch.com/~glitch-hello-node) se você tiver já não!
## O que há neste projeto?

← `README.md`: Esse é este arquivo, onde você pode dizer às pessoas o que seu site legal faz e como você o construiu.

← `package.json`: Os pacotes NPM para as dependências do seu projeto.

← `.env`: O ambiente é limpo quando você remixa inicialmente o projeto, mas você adicionará um novo valor de variável env quando seguir os passos em `TODO.md` para configurar uma chave admin.

### Servidor e banco de dados

← `server.js`: O script do servidor Node.js para seu novo site. O JavaScript define os endpoints na API do site. A API processa solicitações, conecta-se ao banco de dados usando o script `sqlite` em `src` e envia informações de volta ao cliente (as páginas da web que compõem a interface do usuário do aplicativo, construídas usando os modelos Handlebars em `src/pages` ).

← `/src/sqlite.js`: O script do banco de dados trata da configuração e conexão com o banco de dados SQLite. Os endpoints da API `server.js` chamam as funções no script do banco de dados para gerenciar os dados.

← `/src/data.json`: O arquivo de configuração de dados inclui o script do gerenciador de banco de dados–`server.js` lê a propriedade `database` para importar o script correto.

Quando o aplicativo é executado, os scripts criam o banco de dados:

← `.data/choices.db`: Seu banco de dados é criado e colocado na pasta `.data`, um diretório oculto cujo conteúdo não é copiado quando um projeto é remixado. Você pode ver o conteúdo de `.data` no console selecionando __Tools__ > __Logs__.

### User interface

← `public/style.css`: The style rules that define the site appearance.

← `src/pages`: The handlebars files that make up the site user interface. The API in `server.js` sends data to these templates to include in the HTML.

← `src/pages/index.hbs`: The site homepage presents a form when the user first visits. When the visitor submits a preference through the form, the app calls the `POST` endpoint `/`, passing the user selection. The `server.js` endpoint updates the database and returns the user choices submitted so far, which the page presents in a chart (using [Chart.js](https://www.chartjs.org/docs/)–you can see the code in the page `head`).

← `src/pages/admin.hbs`: The admin page presents a table displaying the log of most recent picks. You can clear the list by setting up your admin key (see `TODO.md`). If the user attempts to clear the list without a valid key, the page will present the log again.

← `src/seo.json`: When you're ready to share your new site or add a custom domain, change SEO/meta settings in here.

## Try this next 🏗️

Take a look in `TODO.md` for steps in setting up your admin key and adding to the site functionality.

💡 __Want to use the server script as an API without using the front-end UI? No problem! Just send a query parameter `?raw=json` with your requests to return JSON, like this (replace the first part of the URL to match your remix): `glitch-hello-sqlite.glitch.me?raw=json`__

___Check out [Blank SQLite](https://glitch.com/~glitch-blank-sqlite) for a minimal demo of get, post, put, and delete methods.___

![Glitch](https://cdn.glitch.com/a9975ea6-8949-4bab-addb-8a95021dc2da%2FLogo_Color.svg?v=1602781328576)

## You built this with Glitch!

[Glitch](https://glitch.com) is a friendly community where millions of people come together to build web apps and websites.

- Need more help? [Check out our Help Center](https://help.glitch.com/) for answers to any common questions.
- Ready to make it official? [Become a paid Glitch member](https://glitch.com/pricing) to boost your app with private sharing, more storage and memory, domains and more.
