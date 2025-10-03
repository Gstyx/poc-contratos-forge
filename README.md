# PoC: Contratos Inteligentes para Simulação de Ataque de Oráculo

Este repositório contém o ambiente on-chain para uma Prova de Conceito (PoC) que demonstra uma vulnerabilidade de manipulação de oráculo em um ecossistema DeFi simulado. Os contratos foram desenvolvidos utilizando Solidity e o framework Foundry.

Este é o "mundo" onde o agente autônomo irá operar.

## ⛓️ Stack Tecnológica

* **Linguagem:** Solidity
* **Framework:** Foundry (Forge / Anvil)

## 📄 Contratos

* `src/SimpleDEX.sol`: Uma exchange descentralizada simplificada, configurada com baixa liquidez para servir como um oráculo de preços vulnerável.
* `src/LendingProtocol.sol`: Um protocolo de empréstimo que confia cegamente no preço fornecido pela `SimpleDEX` para calcular o valor do colateral dos usuários.
* `src/TokenA.sol`: Um token ERC20 padrão utilizado como ativo no ecossistema.

## ⚙️ Como Utilizar

### Pré-requisitos
* [Foundry](https://getfoundry.sh/) instalado.

### Testando a Vulnerabilidade
Para validar a existência do exploit de forma isolada, execute os testes do Forge:
```bash
# Instalar dependências (OpenZeppelin)
forge install

# Compilar os contratos
forge build

# Rodar o teste de exploração
forge test --vv
```

### Implantando em um Ambiente Local
Para criar um ambiente vivo para o agente interagir, use o script de implantação com o Anvil.
```bash
# Terminal 1: Inicie a blockchain local
anvil

# Terminal 2: Implante os contratos
# (substitua pela sua chave privada do Anvil)
forge script script/Deploy.s.sol --rpc-url [http://127.0.0.1:8545](http://127.0.0.1:8545) --broadcast --private-key SUA_CHAVE_PRIVADA_DO_ANVIL
```

## 🔗 Repositórios do Projeto

* **Este Repositório (On-Chain):** `https://github.com/Gstyx/poc-contratos-forge`
* **Agente Autônomo (Off-Chain):** `https://github.com/Gstyx/poc-agente-deno`
