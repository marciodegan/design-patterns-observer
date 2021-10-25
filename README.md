## Design Pattern - Observer

### Notes:
- Continuação do: https://github.com/marciodegan/design-pattern-command

- No exemplo anterior, apesar de separadas as acoes na classe GeraPedidoHandler, a classe crescerá a medida que novas ações precisem ser implementadas.
- Acabamos precisando instanciar a classe de cada ação, chamar os métodos, etc.
- Também se utilizarmos injeção de dependencias, o construtor também irá aumentar cada vez mais, pois a cada nova ação, será preciso receber um novo parametro no construtor.
- Para resolver, vamos extrair as ações para uma classe separada.
- Utilizando o polimorfismo, transformamos as ações em um atributo do tipo List.
- Todas as classes de ação tem um método "executar()", então criamos um interface onde só é definido o método executar().
- Agora cada classe de ação implementa a interface.
- E a classe GeraPedidoHandler agora recebe no construtor, ao inves de recebe diversas classes, agora recebe a lista de ações representada pela interface.
- Agora com um forEach é só executar todas as ações.
- Na hora de instanciar o handler, posso passar as ações que eu quero passar para o Handler, através de um Array.asList.
- GeraPedidoHandler handler = new GeraPedidoHandler(Arrays.asList(new SalvarPedidoNoBancoDeDados(), new EnviarEmailPedido()));
#### Observer
- As classes observer/ouvinte neste caso são a EnviarEmailPedido e SalvarPedido...a ideía é de ao inves de chamar classe por classe...vc simplesmente notifica...acabei de disparar um evento...que estiver observando vai ser notificado e vai executar a sua propria acao...é um exemplo de inversão de controle...e assim diminuimos o acoplamento.
- É mais interessante separar cada ação em uma classe separada;

Deixar a implementação de todas as tarefas de um caso de uso da aplicação na mesma classe pode trazer problemas:
- Dificuldade de manutenção;
- Classes muito grandes e difíceis de ler;
- Problemas quando precisar alterar a implementação de uma das tarefas.
