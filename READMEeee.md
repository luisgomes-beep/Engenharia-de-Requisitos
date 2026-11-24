<div align="center">

# 🏠 MOBCASA

### Plataforma web para divulgação de imóveis à venda e apoio às etapas iniciais de negociação

![Status](https://img.shields.io/badge/status-documentação-2e7d32?style=for-the-badge)
![Tipo](https://img.shields.io/badge/plataforma-web-1565c0?style=for-the-badge)
![UFAM](https://img.shields.io/badge/UFAM-ICET-6a1b9a?style=for-the-badge)
![Período](https://img.shields.io/badge/período-2026.2-ef6c00?style=for-the-badge)

**Documentação de Requisitos e Especificação do Sistema**

Universidade Federal do Amazonas · Instituto de Ciências Exatas e Tecnologia · Engenharia de Software
Disciplina de Gerência de Configuração · Docente: Walter Viana

</div>

---

## 👥 Equipe

| Integrante |
|---|
| Letícia Abreu |
| Luís Gustavo |
| Paolla Gabriele |

---

## 📑 Sumário

1. [Introdução](#1-introdução)
   - 1.1. [Descrição Geral do Software](#11-descrição-geral-do-software)
   - 1.2. [Descrição dos Usuários](#12-descrição-dos-usuários)
2. [Requisitos Gerais do Software](#2-requisitos-gerais-do-software)
   - 2.1. [Requisitos Funcionais](#21-requisitos-funcionais)
   - 2.2. [Requisitos Não Funcionais](#22-requisitos-não-funcionais)
   - 2.3. [Regras de Negócio](#23-regras-de-negócio)
3. [Diagramas UML](#3-diagramas-uml)
   - 3.1. [Diagramas de Casos de Uso](#31-diagramas-de-casos-de-uso)
   - 3.2. [Diagramas de Sequência](#32-diagramas-de-sequência)
   - 3.3. [Diagramas de Atividades](#33-diagramas-de-atividades)

---

## 1. Introdução

### 1.1. Descrição Geral do Software

O **MOBCASA** é uma plataforma web que facilita a **busca e a negociação de imóveis à venda**. Voltada à divulgação de imóveis, a plataforma também apoia as etapas iniciais da negociação entre quem anuncia e quem deseja comprar.

> Visitantes pesquisam e visualizam anúncios. Clientes agendam visitas, enviam propostas e acompanham o financiamento. Corretores cadastram imóveis e analisam propostas. Analistas financeiros registram o andamento dos financiamentos e administradores gerenciam contas e permissões.

### 1.2. Descrição dos Usuários

| Perfil | Descrição | Funcionalidades |
|---|---|---|
| 👤 **Visitante** | Pessoa que acessa a plataforma sem sessão ativa. | Criar conta, pesquisar imóveis e visualizar anúncios. |
| 🧑‍💼 **Cliente** | Usuário autenticado interessado em um imóvel. | Agendar visita, enviar proposta, acompanhar financiamento e encerrar sessão. |
| 🏢 **Corretor** | Usuário autorizado a publicar e negociar imóveis. | Cadastrar imóvel, analisar proposta e encerrar sessão. |
| 💰 **Analista Financeiro** | Usuário autorizado a atualizar solicitações de financiamento. | Registrar atualizações do financiamento e encerrar sessão. |
| 🛡️ **Administrador** | Usuário com privilégio administrativo. | Gerenciar usuários e permissões e encerrar sessão. |

---

## 2. Requisitos Gerais do Software

### 2.1. Requisitos Funcionais

| ID | Requisito | Descrição | Caso de uso |
|---|---|---|---|
| **RF01** | Criar conta | O visitante informa os dados solicitados; o sistema valida as informações, verifica se não há conta duplicada e cria a conta. | UC01 |
| **RF02** | Realizar login | O usuário informa suas credenciais; o sistema verifica se estão corretas e se a conta está ativa, e apresenta a área correspondente ao perfil. | UC02 |
| **RF03** | Pesquisar imóveis | O usuário busca anúncios por palavras-chave e/ou filtros; o sistema exibe os imóveis encontrados ou um aviso caso não existam resultados. | UC03 |
| **RF04** | Visualizar anúncio | O sistema apresenta fotos, preço, descrição, características e disponibilidade do imóvel selecionado. | UC04 |
| **RF05** | Cadastrar imóvel | O corretor informa os dados do imóvel e adiciona imagens; o sistema valida os campos obrigatórios e registra o anúncio. | UC05 |
| **RF06** | Agendar visita | O cliente escolhe uma data e um horário disponíveis; o sistema registra a solicitação como pendente de confirmação. | UC06 |
| **RF07** | Enviar proposta | O cliente informa valor e condições; o sistema registra a proposta para análise e informa seu identificador. | UC07 |
| **RF08** | Analisar proposta | O corretor consulta as propostas recebidas, registra o resultado ou solicita negociação; o sistema atualiza o estado e mantém o histórico. | UC08 |
| **RF09** | Acompanhar financiamento | O cliente consulta o andamento da solicitação e o analista financeiro autorizado registra novas atualizações. | UC09 |
| **RF10** | Gerenciar usuários | O administrador acessa uma conta e altera seu estado ou suas permissões; o sistema verifica a autorização e registra as alterações. | UC10 |
| **RF11** | Encerrar sessão | O sistema encerra a sessão do usuário, bloqueia as funcionalidades protegidas e o redireciona para a página pública ou para o login. | UC11 |

### 2.2. Requisitos Não Funcionais

> Identificados a partir das restrições e dos fluxos dos casos de uso e dos diagramas da modelagem.

| ID | Categoria | Descrição |
|---|---|---|
| **RNF01** | Plataforma | O sistema é uma plataforma web, acessada com conexão à internet. |
| **RNF02** | Segurança | O acesso às funcionalidades protegidas exige autenticação, e cada usuário acessa somente as funções permitidas ao seu perfil. |
| **RNF03** | Segurança | Após o encerramento da sessão, as funcionalidades protegidas exigem nova autenticação. |
| **RNF04** | Rastreabilidade | O sistema mantém o histórico das alterações de estado das propostas e registra as alterações de contas e permissões. |
| **RNF05** | Usabilidade | O sistema informa o resultado das operações e apresenta mensagens claras em caso de erro, bloqueio ou ausência de resultados. |
| **RNF06** | Persistência | Imóveis, propostas e demais dados são armazenados em banco de dados. |

### 2.3. Regras de Negócio

| ID | Regra | Descrição | Origem |
|---|---|---|---|
| **RN01** | Conta única | Campo inválido ou conta já existente impede a conclusão do cadastro. | UC01 |
| **RN02** | Conta ativa | Credenciais inválidas ou conta inativa impedem o acesso ao sistema. | UC02 |
| **RN03** | Acesso por perfil | Após o login, o usuário acessa apenas as funções permitidas ao seu perfil. | UC02 |
| **RN04** | Filtros de pesquisa | Filtros inválidos devem ser corrigidos ou ignorados com mensagem clara; nenhum resultado deve gerar aviso. | UC03 |
| **RN05** | Anúncio indisponível | Anúncio removido ou indisponível deve gerar mensagem adequada. | UC04 |
| **RN06** | Cadastro de imóvel | Somente corretor autenticado e autorizado cadastra imóveis; campos obrigatórios ausentes ou dados inconsistentes impedem o cadastro. | UC05 |
| **RN07** | Agendamento de visita | O cliente deve estar autenticado e o anúncio disponível para visita. | UC06 |
| **RN08** | Horário disponível | Horário indisponível ou dados inválidos impedem o envio; o sistema deve sugerir nova seleção quando possível. | UC06 |
| **RN09** | Estado da visita | Toda solicitação de visita é registrada como pendente de confirmação. | UC06 |
| **RN10** | Envio de proposta | O cliente deve estar autenticado; se o imóvel não estiver aceitando propostas, o sistema bloqueia o envio. | UC07 |
| **RN11** | Análise de proposta | Somente usuários autorizados podem alterar o estado de uma proposta, e a alteração fica registrada no histórico. | UC08 |
| **RN12** | Financiamento | A plataforma não deve indicar aprovação antes da decisão formal da instituição financeira. | UC09 |
| **RN13** | Atualização de financiamento | O analista financeiro registra atualizações somente quando autorizado. | UC09 |
| **RN14** | Gestão de usuários | Usuários sem permissão administrativa não podem gerenciar contas e permissões. | UC10 |
| **RN15** | Encerramento de sessão | Após o encerramento, as funcionalidades protegidas exigem nova autenticação. | UC11 |

---

## 3. Diagramas UML

> Os diagramas foram transcritos da modelagem do MOBCASA para **Mermaid**, formato que o GitHub renderiza automaticamente.

### 3.1. Diagramas de Casos de Uso

#### Diagrama de Casos de Uso – Sistema MOBCASA

```mermaid
flowchart LR
    V(["👤 Visitante"])
    C(["🧑‍💼 Cliente"])
    COR(["🏢 Corretor"])
    AF(["💰 Analista Financeiro"])
    ADM(["🛡️ Administrador"])

    subgraph SIS["Sistema MOBCASA"]
        direction TB
        UC01(["UC01<br/>Criar conta"])
        UC02(["UC02<br/>Realizar login"])
        UC03(["UC03<br/>Pesquisar imóveis"])
        UC04(["UC04<br/>Visualizar anúncio"])
        UC05(["UC05<br/>Cadastrar imóvel"])
        UC06(["UC06<br/>Agendar visita"])
        UC07(["UC07<br/>Enviar proposta"])
        UC08(["UC08<br/>Analisar proposta"])
        UC09(["UC09<br/>Acompanhar financiamento"])
        UC10(["UC10<br/>Gerenciar usuários"])
        UC11(["UC11<br/>Encerrar sessão"])

        A1(["Exibir aviso de<br/>nenhum resultado"])
        A2(["Aplicar filtros<br/>de pesquisa"])
        A3(["Validar dados<br/>do imóvel"])
        A4(["Verificar disponibilidade<br/>de horário"])
        A5(["Validar dados<br/>da proposta"])
        A6(["Atualizar status<br/>do financiamento"])
        A7(["Validar permissões<br/>administrativas"])
    end

    V --- UC01
    V --- UC03
    V --- UC04
    C --- UC06
    C --- UC07
    C --- UC09
    C --- UC11
    COR --- UC02
    COR --- UC05
    COR --- UC08
    AF --- UC08
    AF --- A6
    ADM --- UC10
    ADM --- UC11

    UC01 --- UC02

    A1 -. "«extend»" .-> UC03
    A2 -. "«extend»" .-> UC03
    UC05 -. "«include»" .-> A3
    UC06 -. "«include»" .-> A4
    UC07 -. "«include»" .-> A5
    UC09 -. "«include»" .-> A6
    UC10 -. "«include»" .-> A7

    classDef ator fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#1b1b1b
    classDef uc fill:#d6e9f8,stroke:#1565c0,stroke-width:1.5px,color:#1b1b1b
    classDef sub fill:#fff8e1,stroke:#ef6c00,stroke-width:1px,color:#1b1b1b
    class V,C,COR,AF,ADM ator
    class UC01,UC02,UC03,UC04,UC05,UC06,UC07,UC08,UC09,UC10,UC11 uc
    class A1,A2,A3,A4,A5,A6,A7 sub
```

#### Especificação dos Casos de Uso

<details>
<summary><b>UC01 – Criar conta</b></summary>

> O visitante informa os dados solicitados pelo sistema. O sistema verifica se as informações são válidas e se não existe uma conta duplicada. Após a validação, a conta é criada e o usuário pode realizar o login.

| Campo | Descrição |
|---|---|
| **Ator principal** | Cliente/Visitante |
| **Resumo** | O usuário cria uma conta para acessar as funcionalidades autenticadas. |
| **Pré-condições** | O usuário não possui sessão ativa e tem acesso à internet. |
| **Pós-condições** | Conta criada e usuário pode realizar login. |
| **Fluxo principal** | 1. Seleciona criar conta.<br>2. Informa os dados solicitados.<br>3. Envia o formulário.<br>4. O sistema valida os dados e verifica duplicidade.<br>5. O sistema registra a conta e informa o resultado. |
| **Restrições/validações** | Se houver campo inválido ou conta já existente, o sistema informa o problema e não conclui o cadastro. |

</details>

<details>
<summary><b>UC02 – Realizar login</b></summary>

> O usuário informa suas credenciais para acessar o sistema. O sistema verifica se os dados estão corretos e se a conta está ativa. Se estiver tudo certo, o usuário entra na área correspondente ao seu perfil.

| Campo | Descrição |
|---|---|
| **Ator principal** | Cliente, Corretor, Analista Financeiro, Administrador |
| **Resumo** | O usuário entra no sistema com suas credenciais. |
| **Pré-condições** | O usuário possui uma conta ativa. |
| **Pós-condições** | Sessão autenticada e acesso às funções permitidas ao perfil. |
| **Fluxo principal** | 1. Informa credenciais.<br>2. Solicita entrada.<br>3. O sistema valida as credenciais.<br>4. O sistema inicia a sessão e apresenta a área correspondente ao perfil. |
| **Restrições/validações** | Credenciais inválidas ou conta inativa impedem o acesso. |

</details>

<details>
<summary><b>UC03 – Pesquisar imóveis</b></summary>

> O usuário pode realizar uma busca utilizando palavras-chave ou filtros. O sistema consulta os anúncios disponíveis de acordo com os critérios informados. Por fim, são apresentados os imóveis encontrados ou uma mensagem caso não existam resultados.

| Campo | Descrição |
|---|---|
| **Ator principal** | Visitante/Cliente |
| **Resumo** | O usuário procura anúncios por critérios de interesse. |
| **Pré-condições** | Existem anúncios publicados ou a pesquisa pode retornar vazia. |
| **Pós-condições** | Lista de resultados ou aviso de que não há resultados. |
| **Fluxo principal** | 1. Acessa a pesquisa.<br>2. Informa palavras-chave e/ou filtros.<br>3. O sistema consulta os anúncios publicados.<br>4. Exibe os resultados. |
| **Restrições/validações** | Filtros inválidos devem ser corrigidos ou ignorados com mensagem clara; nenhum resultado deve gerar aviso. |

</details>

<details>
<summary><b>UC04 – Visualizar anúncio</b></summary>

> O usuário seleciona um imóvel que deseja conhecer melhor. O sistema apresenta informações como fotos, preço, descrição e características do imóvel. Caso o anúncio esteja indisponível, o sistema apresenta uma mensagem informando a situação.

| Campo | Descrição |
|---|---|
| **Ator principal** | Visitante/Cliente |
| **Resumo** | O usuário consulta os detalhes de um imóvel anunciado. |
| **Pré-condições** | O anúncio existe e está visível publicamente. |
| **Pós-condições** | Detalhes do anúncio apresentados. |
| **Fluxo principal** | 1. Seleciona um imóvel.<br>2. O sistema exibe fotos, preço, descrição, características e disponibilidade cadastradas. |
| **Restrições/validações** | Anúncio removido ou indisponível deve gerar mensagem adequada. |

</details>

<details>
<summary><b>UC05 – Cadastrar imóvel</b></summary>

> O corretor informa os dados do imóvel e adiciona as imagens necessárias. O sistema verifica se os campos obrigatórios foram preenchidos corretamente. Depois da validação, o anúncio é registrado e pode ser publicado.

| Campo | Descrição |
|---|---|
| **Ator principal** | Corretor |
| **Resumo** | O corretor publica um novo imóvel para venda. |
| **Pré-condições** | O corretor está autenticado e autorizado. |
| **Pós-condições** | Anúncio registrado como disponível ou aguardando publicação, conforme configuração. |
| **Fluxo principal** | 1. Acessa cadastro de imóvel.<br>2. Preenche dados e adiciona imagens.<br>3. Envia.<br>4. O sistema valida os campos.<br>5. Registra o anúncio e informa o resultado. |
| **Restrições/validações** | Campos obrigatórios ausentes ou dados inconsistentes impedem o cadastro. |

</details>

<details>
<summary><b>UC06 – Agendar visita</b></summary>

> O cliente acessa o anúncio e solicita uma visita ao imóvel. Ele escolhe uma das datas e horários disponíveis no sistema. Depois de confirmar, a solicitação é registrada e fica aguardando confirmação.

| Campo | Descrição |
|---|---|
| **Ator principal** | Cliente |
| **Resumo** | O cliente solicita uma visita ao imóvel. |
| **Pré-condições** | O cliente está autenticado e o anúncio está disponível para visita. |
| **Pós-condições** | Solicitação registrada como pendente de confirmação. |
| **Fluxo principal** | 1. Abre o anúncio.<br>2. Seleciona agendar visita.<br>3. Escolhe data e horário disponíveis.<br>4. Confirma a solicitação.<br>5. O sistema registra e notifica o estado. |
| **Restrições/validações** | Horário indisponível ou dados inválidos impedem o envio; o sistema deve sugerir nova seleção quando possível. |

</details>

<details>
<summary><b>UC07 – Enviar proposta</b></summary>

> O cliente seleciona um imóvel que aceita propostas de compra. Ele informa o valor e as condições que deseja oferecer. Após a confirmação, o sistema registra a proposta para que ela seja analisada.

| Campo | Descrição |
|---|---|
| **Ator principal** | Cliente |
| **Resumo** | O cliente registra uma oferta de compra. |
| **Pré-condições** | O cliente está autenticado e o imóvel aceita propostas. |
| **Pós-condições** | Proposta registrada e disponível para análise comercial. |
| **Fluxo principal** | 1. Abre o anúncio.<br>2. Seleciona enviar proposta.<br>3. Informa valor e condições solicitadas.<br>4. Confirma.<br>5. O sistema registra a proposta e informa seu identificador. |
| **Restrições/validações** | Se o imóvel não estiver aceitando propostas, o sistema bloqueia o envio. |

</details>

<details>
<summary><b>UC08 – Analisar proposta</b></summary>

> O corretor consulta as propostas que foram recebidas. Ele pode analisar uma proposta e registrar o resultado ou solicitar uma negociação. O sistema atualiza o estado da proposta e mantém o histórico da alteração.

| Campo | Descrição |
|---|---|
| **Ator principal** | Corretor |
| **Resumo** | O corretor consulta e atualiza o estado comercial de uma proposta. |
| **Pré-condições** | O corretor está autenticado e autorizado a tratar a proposta. |
| **Pós-condições** | Proposta atualizada e cliente pode acompanhar o estado. |
| **Fluxo principal** | 1. Consulta propostas recebidas.<br>2. Abre uma proposta.<br>3. Registra o resultado ou solicita negociação.<br>4. O sistema salva a alteração e registra o histórico. |
| **Restrições/validações** | Somente usuários autorizados podem alterar o estado. |

</details>

<details>
<summary><b>UC09 – Acompanhar financiamento</b></summary>

> O cliente pode consultar o andamento da sua solicitação. O analista financeiro autorizado também pode registrar novas atualizações. Dessa forma, o sistema mantém o estado do financiamento atualizado para os usuários autorizados.

| Campo | Descrição |
|---|---|
| **Ator principal** | Cliente/Analista Financeiro |
| **Resumo** | O cliente consulta o andamento e o analista autorizado registra atualizações de uma solicitação. |
| **Pré-condições** | A solicitação foi registrada e o usuário possui permissão adequada. |
| **Pós-condições** | Estado atualizado disponível aos usuários autorizados. |
| **Fluxo principal** | 1. O cliente abre a área de financiamento.<br>2. O sistema exibe o estado disponível.<br>3. O analista, quando autorizado, registra a atualização.<br>4. O sistema salva a mudança. |
| **Restrições/validações** | A plataforma não deve indicar aprovação antes de decisão formal da instituição financeira. |

</details>

<details>
<summary><b>UC10 – Gerenciar usuários</b></summary>

> Essa função é realizada pelo administrador do sistema. Ele pode acessar uma conta e alterar suas permissões conforme necessário. O sistema verifica a autorização e registra as alterações realizadas.

| Campo | Descrição |
|---|---|
| **Ator principal** | Administrador |
| **Resumo** | O administrador controla contas e permissões. |
| **Pré-condições** | O administrador está autenticado com privilégio administrativo. |
| **Pós-condições** | Alterações de conta e permissões registradas. |
| **Fluxo principal** | 1. Abre a área administrativa.<br>2. Localiza a conta.<br>3. Altera estado ou permissões permitidas.<br>4. Confirma.<br>5. O sistema valida autorização e registra a alteração. |
| **Restrições/validações** | Usuários sem permissão administrativa não podem executar esta função. |

</details>

<details>
<summary><b>UC11 – Encerrar sessão</b></summary>

> O usuário seleciona a opção para sair da sua conta. O sistema encerra a sessão e bloqueia o acesso às funcionalidades protegidas. Depois disso, o usuário é direcionado para a página pública ou para a tela de login.

| Campo | Descrição |
|---|---|
| **Ator principal** | Cliente/Corretor/Analista Financeiro/Administrador |
| **Resumo** | O usuário encerra seu acesso autenticado. |
| **Pré-condições** | Existe sessão ativa. |
| **Pós-condições** | Sessão encerrada e acesso protegido bloqueado. |
| **Fluxo principal** | 1. Seleciona sair.<br>2. O sistema encerra a sessão.<br>3. Redireciona para a página pública ou login. |
| **Restrições/validações** | Após o encerramento, funcionalidades protegidas exigem nova autenticação. |

</details>

### 3.2. Diagramas de Sequência

#### Diagrama de Sequência – Cadastrar imóvel

```mermaid
sequenceDiagram
    autonumber
    actor Corretor
    participant Interface
    participant Controlador
    participant BD as Banco de dados

    Corretor->>Interface: Seleciona a opção "Cadastrar Imóvel"
    Corretor->>Interface: Preenche o formulário com os dados do imóvel (endereço, valor, fotos, etc.)
    Interface->>Controlador: Envia os dados para validação
    Controlador->>BD: Salva o imóvel no banco de dados
    BD-->>Controlador: Confirmação de cadastro
    Controlador-->>Interface: Retorna sucesso da operação
    Interface-->>Corretor: Exibe mensagem de sucesso
```

#### Diagrama de Sequência – Visualizar imóvel

```mermaid
sequenceDiagram
    autonumber
    actor Cliente
    participant Interface
    participant Controlador
    participant BD as Banco de dados

    Cliente->>Interface: Seleciona um imóvel na lista de resultados
    Interface->>Controlador: Solicita detalhes do imóvel (id do imóvel)
    Controlador->>BD: Busca dados do imóvel (id do imóvel)
    BD-->>Controlador: Retorna dados do imóvel
    Controlador-->>Interface: Envia informações do imóvel (fotos, descrição, valor, etc.)
    Interface-->>Cliente: Exibe detalhes do imóvel na tela
```

#### Diagrama de Sequência – Enviar proposta

```mermaid
sequenceDiagram
    autonumber
    actor Cliente
    participant Interface
    participant Controlador
    participant BD as Banco de dados

    Cliente->>Interface: Seleciona imóvel e clica em "Enviar proposta"
    Interface->>Controlador: Envia dados da proposta (valor, condições, mensagem)
    Controlador->>BD: Salva proposta
    BD-->>Controlador: Confirmação de salvamento
    Controlador-->>Interface: Retorna mensagem de sucesso
    Interface-->>Cliente: Exibe confirmação de envio
```

### 3.3. Diagramas de Atividades

#### Diagrama de Atividades – Agendar visita

```mermaid
flowchart TD
    INICIO((" ")) --> A1["Acessar anúncio do imóvel"]
    A1 --> A2["Selecionar 'Agendar visita'"]
    A2 --> A3["Consultar horários disponíveis"]
    A3 --> D{"Há horário<br>disponível?"}

    D -- "[Disponível]" --> B1["Selecionar data e horário"]
    B1 --> B2["Confirmar solicitação"]
    B2 --> B3["Registrar visita como<br>pendente de confirmação"]
    B3 --> B4["Notificar cliente e corretor"]
    B4 --> FIM((" "))

    D -- "[Indisponível]" --> C1["Exibir aviso de<br>indisponibilidade"]
    C1 --> C2["Sugerir outros horários"]
    C2 --> A3

    classDef ini fill:#212121,stroke:#212121,color:#ffffff
    classDef acao fill:#fff3c4,stroke:#8d6e00,stroke-width:1.5px,color:#1b1b1b
    classDef dec fill:#ffe0b2,stroke:#ef6c00,stroke-width:2px,color:#1b1b1b
    class INICIO,FIM ini
    class A1,A2,A3,B1,B2,B3,B4,C1,C2 acao
    class D dec
```

---

<div align="center">

**MOBCASA** · Documentação de Requisitos e Especificação do Sistema
UFAM · ICET · Engenharia de Software · Outubro/2026

</div>
