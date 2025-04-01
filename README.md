# BANK ESPM

### Exercício 1

O exercício 1 é um sistema simples de controle de contas bancárias e seus saldo acessível via terminal (9 pontos), se implementado usando interface gráfica ganha 1 ponto.

O mínimo que o sistema deve ter:

1. Cadastro de cliente (Pessoa Física/Jurídica);

2. Cadastro de contas para o cliente:
- Conta corrente (tem ou não limite);
- Conta poupança (não tem limite e rende);
- Conta rendimento (apenas rende);

3. Permitir saques/depósitos (respeitando as regras das conta);

4. Listar contas e clientes.

5. Remover clientes e suas contas do banco.

Obrigatório:

a. uso de classes, interfaces;

b. sobrecarga de métodos e construtores;

c. uso de casting e listagem por forEach.

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
