Para que esse teste passe, você deve permitir que o middleware **checksCreateTodosUserAvailability** receba o objeto `user` (considere sempre que o objeto existe) da `request` e chame a função `next` somente no caso do usuário estar no **plano grátis e ainda não possuir 10 _todos_ cadastrados** ou se ele **já estiver com o plano Pro ativado**.

💡 Você pode verificar se o usuário possui um plano Pro ou não a partir da propriedade `user.pro`. Caso seja `true` significa que o plano Pro está em uso.


- **Should not be able to let user create a new todo when is not Pro and already have ten todos**
  Para que esse teste passe, no middleware **checksCreateTodosUserAvailability** você deve retornar uma resposta com status `403` caso o usuário recebido pela requisição esteja no **plano grátis** e **já tenha 10 _todos_ cadastrados**. Você pode também retornar uma mensagem de erro mas isso é opcional.
- **Should be able to let user create infinite new todos when is in Pro plan**
  Para que esse teste passe, você deve permitir que o middleware **checksCreateTodosUserAvailability** receba o objeto `user` (considere sempre que o objeto existe) da `request` e chame a função `next` caso o usuário já esteja com o plano Pro.

    💡 Se você satisfez os dois testes anteriores antes desse, ele já deve passar também.
    


- **Should be able to put user and todo in request when both exits**
  Para que esse teste passe, o middleware **checksTodoExists** deve receber o `username` de dentro do header e o `id` de um _todo_ de dentro de `request.params`. Você deve validar que o usuário exista, validar que o `id` seja um uuid e também validar que esse `id` pertence a um _todo_ do usuário informado.
  Com todas as validações passando, o _todo_ encontrado deve ser passado para o `request` assim como o usuário encontrado também e a função next deve ser chamada.
  É importante que você coloque dentro de `request.user` o usuário encontrado e dentro de `request.todo` o _todo_ encontrado.
- **Should not be able to put user and todo in request when user does not exists**
  Para que esse teste passe, no middleware **checksTodoExists** você deve retornar uma resposta com status `404` caso não exista um usuário com o `username` passado pelo header da requisição.
- **Should not be able to put user and todo in request when todo id is not uuid**
  Para que esse teste passe, no middleware **checksTodoExists** você deve retornar uma resposta com status `400` caso o `id` do _todo_ passado pelos parâmetros da requisição não seja um UUID válido (por exemplo `1234abcd`).
- **Should not be able to put user and todo in request when todo does not exists**
  Para que esse teste passe, no middleware **checksTodoExists** você deve retornar uma resposta com status `404` caso o `id` do _todo_ passado pelos parâmetros da requisição não pertença a nenhum _todo_ do usuário encontrado.
- **Should be able to find user by id route param and pass it to request.user**
  Para que esse teste passe, o middleware **findUserById** deve receber o `id` de um usuário de dentro do `request.params`. Você deve validar que o usuário exista, repassar ele para `request.user` e retornar a chamada da função next.
- **Should not be able to pass user to request.user when it does not exists**
  Para que esse teste passe, no middleware **findUserById** você deve retornar uma resposta com status `404` caso o `id` do usuário \*\*passado pelos parâmetros da requisição não pertença a nenhum usuário cadastrado.

---

Todos os demais testes são os mesmos testes encontrados no desafio 01 com algumas (ou nenhuma) mudanças.

⚠️  Vale reforçar que esse desafio é focado apenas em middlewares e você não precisa modificar o conteúdo das rotas para que os testes passem 💜


# 📅 Entrega

Esse desafio deve ser entregue a partir da plataforma da Rocketseat. Envie o link do repositório que você fez suas alterações. Após concluir o desafio, além de ter mandado o código para o GitHub, fazer um post no LinkedIn é uma boa forma de demonstrar seus conhecimentos e esforços para evoluir na sua carreira para oportunidades futuras.

