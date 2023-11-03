`request.param` geralmente é mais utilizado para parametros simples

No `route param` os valores são obrigatórios. No endereço eles precisam ser informados para que não ocorra erro na aplicação.

Ex:
```js
app.get("/message/:id/:user", (request, response) => {
    const { id, user } = request.params;
    response.send(`
    Mensagem ID: ${id}.
    Usuário: ${user}.
    `);
});
```

No `query params` os valores são opcionais. Caso eu não informe um parâmetro, a aplicação continua funcional.

```js

app.get("/users", (request, response) => {
    const { page, limit } = request.query;

    response.send(`Página: ${page}. Mostrar: ${limit}.`);
})
```

Sempre que possóvel devolver as informacoes como `json` (quando utilizar o método SEND). Esse e o padrão mais utilizado nas API's.


Em `controlers` podem haver no máximo 5 métodos:
- `index` - GET para listar vários registros.
- `show` - GET para exibir um registro.
- `create` - POST para criar um registro.
- `update` - PUT para atualizar um registro.
- `delete` - DELETE para remover um registro.

Se forem necessárioss mais métodos, seria interessante criar um `controller` separado.