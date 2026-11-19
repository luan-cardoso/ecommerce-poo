## POO: Sistema de E-commerce
#### Projeto que simula uma pequena loja virtual. A ideia é fazer aplicar os principais conceitos de Programação Orientada a Objetos em um cenário próximo de um projeto profissional com C# e .NET.

#### O sistema deverá permitir:
- Cadastrar clientes.
- Cadastrar produtos físicos e digitais.
- Criar pedidos para os clientes.
- Adicionar e remover produtos dos pedidos.
- Calcular valores e descontos.
- Calcular frete.
- Processar pagamentos.
- Controlar o status dos pedidos.
- Exibir resumo do pedido.

#### Não foi implementada Clean Architecture completa neste momento.

#### Etapa 1 — Classes, objetos e encapsulamento
- Criar as classes Cliente e Produto.

##### Cliente
- Nome.
- E-mail.
- CPF.

##### Produto
- Identificador.
- Nome.
- Preço.
- Indicador de ativo.

##### Conceitos trabalhados:
- Classes e objetos.
- Atributos e métodos.
- Construtores.
- Encapsulamento.
- Propriedades get e private set.
- Modificadores de acesso.
- Validação de estado.

##### Regras:
1. O cliente não pode ser criado com nome vazio.
2. O e-mail deve possuir um formato válido.
3. O preço do produto não pode ser negativo.
4. O preço não pode ser alterado diretamente de qualquer lugar do sistema.
5. As propriedades devem expor somente os níveis de acesso necessários.


#### Etapa 2 — Herança, abstração e polimorfismo
- Trabalhar com diferentes tipos de produtos.

##### Produto físico:
- Deve possuir peso.
- Deve possuir quantidade em estoque.
- Deve calcular seu frete considerando o peso.

##### Produto digital:
- Deve possuir uma URL para download.
- Não deve possuir custo de frete.

##### Conceitos trabalhados:
- Herança.
- Classes abstratas.
- Métodos abstratos.
- Polimorfismo.
- virtual e override.
- Palavra-chave base.
- Reutilização de código.


#### Etapa 3 — Associação, agregação e composição
- Implementar os pedidos.

##### Criar as classes Pedido e ItemPedido.

##### Um pedido deverá possuir:
- Um cliente.
- Uma lista de itens.
- Data de criação.
- Status.
- Número identificador.

##### Cada item deverá possuir:
- Um produto.
- Uma quantidade.
- O preço unitário no momento em que foi adicionado.

##### A lista de itens deve ser privada. Os demais objetos devem interagir com ela por meio de métodos como:
- AdicionarItem()
- RemoverItem()
- CalcularSubtotal()

##### Regras:
1. Um pedido pode possuir vários itens.
2. Um item pertence a um pedido.
3. Não deve ser possível adicionar uma quantidade menor ou igual a zero.
4. Não deve ser possível adicionar um produto inativo.
5. Não deve ser possível adicionar um produto físico sem estoque suficiente.
6. Não deve ser possível adicionar ou remover itens de pedidos já finalizados.
7. O pedido deve calcular seu subtotal.

##### Conceitos trabalhados:
- Associação.
- Agregação.
- Composição.
- Relacionamentos entre objetos.
- Coleções de objetos.
- Encapsulamento de coleções.
- Responsabilidade de cada classe.


#### Etapa 4 — Interfaces e contratos
- Implementar duas interfaces:

##### IPagamento
- Deve definir um contrato para processar pagamentos.
- Criar as implementações: PagamentoPix, PagamentoCartaoCredito

##### IDesconto
- Deve definir um contrato para calcular descontos.
- Criar as implementações: DescontoPercentual, DescontoValorFixo

##### Implementa as interfaces, o sistema deve aceitar novas formas de pagamento e descontos sem precisar modificar toda a lógica do pedido.

##### Conceitos trabalhados:
- Interfaces.
- Implementação de contratos.
- Diferença entre interfaces e classes abstratas.
- Polimorfismo por interfaces.
- Baixo acoplamento.
- Extensibilidade.

#### Etapa 5 — Serviços e injeção de dependência
- Criar a classe CheckoutService. Ela será responsável por coordenar a finalização do pedido.

##### O checkout deverá:
1. Receber um pedido.
2. Verificar se ele pode ser finalizado.
3. Calcular o subtotal.
4. Calcular o desconto.
5. Calcular o frete.
6. Calcular o valor final.
7. Processar o pagamento.
8. Atualizar o status do pedido de acordo com o resultado.

##### O serviço deve receber suas dependências pelo construtor.

##### O cálculo do frete poderá ser feito pelo comportamento polimórfico dos produtos.

##### o CheckoutService não deve conhecer os detalhes internos das implementações concretas de pagamento e desconto.

##### Conceitos trabalhados:
- Composição de objetos.
- Injeção de dependência.
- Inversão de dependência.
- Separação de responsabilidades.
- Acoplamento e coesão.

#### Etapa 6 — Enums, exceções e estados
Criar um enum chamado StatusPedido.

##### StatusPedido deverá conter:
- Criado
- AguardandoPagamento
- Pago
- Cancelado

##### Regras:
1. Não pode pagar um pedido cancelado.
2. Não pode cancelar um pedido já pago.
3. Não pode adicionar produtos depois da finalização.
4. Não pode processar pagamentos com valor negativo.

##### Conceitos trabalhados:
- Enums.
- Estados de objetos.
- Tratamento de exceções.
- Exceções personalizadas.
- Invariantes de domínio.

