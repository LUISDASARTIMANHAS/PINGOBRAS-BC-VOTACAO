#TODO🚧

A página __Admin__ do site permite que o usuário limpe o banco de dados de votos – mas somente se uma chave válida for fornecida. Este é um exemplo simplificado de autenticação que verifica se a chave inserida pelo usuário corresponde à do `.env`.

## Configurando sua chave de administrador

Para configurar seu aplicativo para permitir a limpeza do histórico:

* Em seu arquivo `.env`, encontre a variável chamada `ADMIN_KEY` e dê a ela uma string de texto como valor.
* Com a página __Admin__ aberta na visualização, insira o mesmo valor e pressione o botão __Limpar histórico de log__ – desta vez, deve permitir que você limpe o histórico.

Consulte o endpoint `reset` em `server.js` para saber como isso funciona.

## Continue! 🚀

Seu novo site é todo seu, então não importa se você o quebrar! Tente fazer uma edição.

Siga as etapas para permitir que o usuário visualize os resultados sem primeiro enviar um voto:

A página inicial mostra os votos lançados até o momento quando o usuário conclui a enquete, mas você pode permitir que eles vejam o gráfico imediatamente.

1. Adicione um link para `src/pages/index.hbs` após o formulário, que enviará um parâmetro de consulta para o script do servidor:

```
<p>
 <a href="/?results=true">Mostrar resultados</a>
</p>
```

2. Estenda o ponto de extremidade `server.js` `GET` `/` para enviar um sinalizador se o usuário solicitou os resultados:

```
// Resultados solicitados pelo usuário
params.results = request.query.results;
```

Clique no link __Mostrar resultados__ para ver os resultados sem votar!

_Dica: se você acabou de limpar o log, certifique-se de votar novamente para que haja alguns resultados para mostrar._ 🙈