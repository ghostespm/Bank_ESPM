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
    class Conta {
        - String id
        # double saldo
        - Cliente cliente
        + sacar(double valor)
        + depositar(double valor)
    }
    class Cliente {
        - String id
        - String nome
        - List<Conta> contas
    }
    class PessoaFisica {
        - String cpf
    }
    class PessoaJuridica {
        - String cnpj
    }
    class ContaCorrente {
        - double limite
        + sacar(double valor)
    }
    class ContaPoupanca {
        + sacar(double valor)
    }
    Conta *-- Cliente
    Conta <|-- ContaCorrente
    Conta <|-- ContaPoupanca
    Cliente <|-- PessoaFisica
    Cliente <|-- PessoaJuridica
```
