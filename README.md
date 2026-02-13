# modelagem-ecommerce-dio

Perfeito. Aqui está a versão limpa, sem marcadores, pronta para copiar e colar no GitHub:

E-commerce Database Modeling
Overview

Modelagem relacional de um sistema de e-commerce desenvolvida em MySQL, com foco em normalização (até 3FN), integridade referencial e consistência das regras de negócio.

O modelo contempla clientes PF e PJ, pedidos, produtos, pagamentos, entregas, estoque, fornecedores e vendedores terceiros.

Estrutura do Modelo
Cliente (Especialização PF/PJ)

Uma conta pode ser Pessoa Física (PF) ou Pessoa Jurídica (PJ), mas nunca ambas.

Cliente
idCliente (PK)
TipoCliente ('PF' ou 'PJ')
Endereco
DataCadastro
Status

Cliente_PF
idCliente (PK, FK → Cliente)
CPF
DataNascimento

Cliente_PJ
idCliente (PK, FK → Cliente)
CNPJ
RazaoSocial
InscricaoEstadual

Pedido

Pedido
idPedido (PK)
idCliente (FK → Cliente)
DataPedido
ValorTotal
StatusPedido

Relacionamento: Cliente 1:N Pedido

Produto

Produto
idProduto (PK)
Nome
Descricao
Valor (DECIMAL)
Categoria
Ativo

Produto_Pedido (N:N)

Produto_Pedido
idProdutoPedido (PK)
idPedido (FK → Pedido)
idProduto (FK → Produto)
Quantidade
ValorUnitarioNoMomento
DescontoAplicado

Pagamentos

FormaPagamento
idFormaPagamento (PK)
idCliente (FK → Cliente)
Tipo
Detalhes
Ativo

Relacionamento: Cliente 1:N FormaPagamento

Pagamento
idPagamento (PK)
idPedido (FK → Pedido)
idFormaPagamento (FK → FormaPagamento)
Valor
Status
DataPagamento

Relacionamentos:
Pedido 1:N Pagamento
FormaPagamento 1:N Pagamento

Entrega

Entrega
idEntrega (PK)
idPedido (FK → Pedido)
CodigoRastreio
StatusAtual
Transportadora
DataEnvio
DataPrevista
DataEntregaReal

Relacionamento: Pedido 1:N Entrega

HistoricoStatusEntrega
idHistorico (PK)
idEntrega (FK → Entrega)
Status
DataAtualizacao
Observacao

Relacionamento: Entrega 1:N HistoricoStatusEntrega

Estoque

Estoque
idEstoque (PK)
Localizacao
EstoqueMinimo

Produto_Estoque (N:N)
idProdutoEstoque (PK)
idProduto (FK → Produto)
idEstoque (FK → Estoque)
QuantidadeDisponivel
QuantidadeReservada

Objetivo

Demonstrar domínio em modelagem relacional, aplicação de regras de negócio no banco de dados e construção de estrutura escalável para sistemas transacionais.
