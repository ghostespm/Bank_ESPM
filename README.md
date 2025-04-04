# Sistema de Controle de Contas Bancárias

Este é um exercício simples de controle de contas bancárias, onde o sistema gerencia clientes e suas respectivas contas. O sistema pode ser acessado via terminal e tem como objetivo praticar conceitos de programação orientada a objetos.

## Pontuação
- Implementação básica via terminal: **9 pontos**
- Implementação com interface gráfica: **+1 ponto**

## Funcionalidades Mínimas

O sistema deve implementar as seguintes funcionalidades:

1. **Cadastro de Cliente**:
   - Permitir o cadastro de clientes, que podem ser **Pessoa Física** ou **Pessoa Jurídica**.
   
2. **Cadastro de Contas**:
   - O sistema deve permitir o cadastro de **contas correntes** (com ou sem limite), **contas poupança** (sem limite e com rendimento) e **contas de rendimento** (somente com rendimento).

3. **Operações Bancárias**:
   - O sistema deve permitir **saques** e **depósitos**, respeitando as regras de cada tipo de conta.

4. **Listagem de Clientes e Contas**:
   - O sistema deve permitir listar todos os **clientes** cadastrados e suas respectivas **contas**.

5. **Remoção de Clientes e Contas**:
   - O sistema deve permitir a **remoção de clientes**, juntamente com suas **contas**.

## Requisitos Obrigatórios

A implementação do sistema deve seguir os seguintes requisitos:

- **Uso de classes**: A estrutura do sistema deve ser orientada a objetos.
- **Uso de interfaces**: Interfaces devem ser utilizadas para representar contratos de comportamento.
- **Sobrecarga de métodos e construtores**: A sobrecarga de métodos e construtores é obrigatória para permitir diferentes formas de criar e manipular objetos.
- **Uso de casting**: O sistema deve fazer uso de **casting** para manipular diferentes tipos de objetos.
- **Listagem com forEach**: A listagem de clientes e contas deve ser feita utilizando o método **forEach**.

### Diagrama de Classes do Banco

``` mermaid
classDiagram
    class Banco {
        - String name
        - List~Cliente~ clientes
        - List~Conta~ contas
        + adicionarCliente(Cliente cliente)
        + removerCliente(Cliente cliente)
        + listarClientes()
        + adicionarConta(Conta conta)
        + removerConta(Conta conta)
        + listarContas()
        + transferir(String chavePixOrigem, String chavePixDestino, double valor)
    }

    class Cliente {
        - String id
        - String name
        + getId() String
        + getName() String
    }

    class PessoaFisica {
        - String cpf
        + getCpf() String
    }

    class PessoaJuridica {
        - String cnpj
        + getCnpj() String
    }

    class Conta {
        - String id
        # double saldo
        - Cliente cliente
        - List~Transacao~ transacoes
        + sacar(double valor)
        + depositar(double valor)
        + getSaldo() double
        + getTransacoes() List~Transacao~
    }

    class ContaCorrente {
        - double limite
        + sacar(double valor)
    }

    class ContaPoupanca {
        - double taxaRendimento
        + sacar(double valor)
        + aplicarRendimento()
    }

    class ContaRendimento {
        - double taxaRendimento
        + aplicarRendimento()
    }

    class Transacao {
        - String tipo
        - double valor
        - LocalDateTime dataHora
        + getTipo() String
        + getValor() double
        + getDataHora() LocalDateTime
    }

    class Terminal {
        - Banco banco
        + run()
    }

    class Util {
        + isCpf(String cpf) boolean
    }

    Banco *-- Cliente
    Banco *-- Conta
    Cliente <|-- PessoaFisica
    Cliente <|-- PessoaJuridica
    Conta o-- Cliente
    Conta <|-- ContaCorrente
    Conta <|-- ContaPoupanca
    Conta <|-- ContaRendimento
    Conta *-- Transacao
    Terminal ..> Banco
```
