# Análise de Requisitos do Aplicativo de Gerenciamento Financeiro Pessoal

## 1 - Identificação de necessidades e definição de requisitos

**Necessidade:** Os usuários precisam de uma maneira de acompanhar suas transações financeiras, criar orçamentos, visualizar relatórios financeiros, configurar lembretes de pagamento e definir metas financeiras.

**Requisitos funcionais:** O aplicativo deve permitir que os usuários registrem transações, criem orçamentos, visualizem relatórios, configurem lembretes e definam metas. O aplicativo também deve oferecer a opção de sincronizar com as contas bancárias do usuário.

**Requisitos não funcionais:** O aplicativo deve ser seguro, fácil de usar e rápido. Deve ser compatível com os principais sistemas operacionais de smartphones e deve seguir as diretrizes de design de cada plataforma.

## 2 - Análise de requisitos
### 2.1 - Cadastro de Contas 

Os usuários devem ser capazes de cadastrar contas, como contas bancárias ou uma conta "carteira". Cada conta deve ter um nome e um saldo inicial.

### 2.2 - Registro e Adição de Transações

Os usuários devem ser capazes de registrar e adicionar todas as suas transações financeiras, incluindo receitas e despesas. Ao adicionar uma transação, eles devem ser capazes de especificar um valor, uma descrição, uma categoria (por exemplo, alimentação, transporte, etc.) e a conta associada. Eles também devem ser capazes de definir a data da transação. A descrição é opcional, mas pode ajudar a fornecer mais detalhes sobre a transação.

### 2.3 - Visualização do Saldo Geral

Os usuários devem ser capazes de visualizar o saldo geral de todas as suas contas. O aplicativo deve calcular esse saldo somando todas as transações de receita e subtraindo todas as transações de despesa.

### 2.4 - Navegação
A barra inferior do aplicativo deve incluir botões para as seguintes telas: Home, Fluxo de Caixa, Adicionar Transação, Relatórios e Gestão de Cartões de Crédito.

### 2.5 - Fluxo de Caixa 

Os usuários devem ser capazes de visualizar um relatório de fluxo de caixa, que lista o saldo de cada mês.

### 2.6 - Visualização de relatórios financeiros

O aplicativo deve fornecer relatórios e gráficos que resumem as finanças do usuário. Isso pode incluir um resumo de receitas e despesas, uma visão geral do orçamento e uma análise de gastos por categoria.

### 2.7 - Visualização de relatórios financeiros

O aplicativo deve fornecer relatórios e gráficos que resumem as finanças do usuário. Isso pode incluir um resumo de receitas e despesas, uma visão geral do orçamento e uma análise de gastos por categoria.

### 2.8 - Relatórios

Os usuários devem ser capazes de visualizar relatórios que fornecem insights sobre seus hábitos de gastos e economias. Os relatórios podem incluir gráficos de categorias de despesas, histórico de gastos e economias ao longo do tempo, entre outros.

### 2.9 - Configuração de lembretes de pagamento

Os usuários devem ser capazes de configurar lembretes para pagamentos futuros, como contas ou parcelas de empréstimos. O aplicativo deve notificar o usuário quando esses pagamentos estiverem próximos.

### 2.10 - Definição de metas financeiras

Os usuários devem ser capazes de definir metas financeiras, como economizar para uma grande compra ou pagar uma dívida. O aplicativo deve ajudar o usuário a acompanhar seu progresso em direção a essas metas.

### 2.11 - Sincronização com contas bancárias

Para facilitar o registro de transações e a criação de relatórios, o aplicativo pode oferecer a opção de sincronizar com as contas bancárias do usuário.

### 2.12 - Gestão de Cartões de Crédito (Fase 2)

Na segunda fase do desenvolvimento, os usuários devem ser capazes de gerenciar seus cartões de crédito no aplicativo. Eles devem ser capazes de adicionar transações como despesas comuns ou compras no cartão de crédito. As transações do cartão de crédito devem ser refletidas no saldo geral, na projeção de saldo e em outros aspectos do aplicativo.

## 3 - Design do sistema

**Arquitetura de software:** O aplicativo será desenvolvido usando a arquitetura Clean Architecture, que promove a separação de preocupações e a independência do código. Esta arquitetura divide o sistema em camadas, permitindo uma maior flexibilidade e facilitando os testes.

**Camada de Apresentação (Presentation Layer):** Esta camada será implementada usando o padrão Model-View-Intent (MVI). O MVI é um padrão de arquitetura unidirecional que torna o fluxo de dados previsível e fácil de entender, proporcionando uma maneira eficiente de lidar com os estados da UI.

**Interface do Usuário (UI):** A interface do usuário será construída usando Jetpack Compose.

**Coroutines:** Para lidar com operações assíncronas e melhorar a performance do aplicativo, serão utilizadas Coroutines. 

**Testes:** Os testes serão realizados usando JUnit, MockK e Espresso.

**Modelagem de Dados:** O aplicativo contará com um modelo de dados robusto e eficiente para armazenar e gerenciar as informações do usuário. As principais entidades do modelo de dados incluirão:

- **Transações:** Cada transação terá atributos como:
  - **ID:** Um identificador único para a transação.
  - **Valor:** O valor da transação.
  - **Data:** A data em que a transação ocorreu.
  - **Categoria:** A categoria da transação (por exemplo, alimentação, transporte, etc.).
  - **Descrição:** Uma descrição opcional da transação.
  - **Tipo:** O tipo de transação, que pode ser de entrada (receita) ou saída (despesa).
  - **Conta:** A conta associada à transação.

- **Orçamentos:** Cada orçamento estará associado a uma categoria específica e terá atributos como:
  - **ID:** Um identificador único para o orçamento.
  - **Valor Alocado:** O valor alocado para a categoria no orçamento.
  - **Valor Gasto:** O valor atualmente gasto na categoria.
  - **Mês de Referência:** O mês a que o orçamento se refere.

- **Lembretes:** Cada lembrete terá atributos como:
  - **ID:** Um identificador único para o lembrete.
  - **Descrição:** Uma descrição do lembrete.
  - **Data e Hora:** A data e hora para o lembrete.
  - **Status:** Um status para indicar se o lembrete foi concluído ou não.

- **Metas:** Cada meta terá atributos como:
  - **ID:** Um identificador único para a meta.
  - **Descrição:** Uma descrição da meta.
  - **Valor Alvo:** O valor alvo da meta.
  - **Valor Atual:** O valor atual economizado em direção à meta.
  - **Data de Vencimento:** A data de vencimento da meta.

- **Contas:** Cada conta terá atributos como:
  - **ID:** Um identificador único para a conta.
  - **Nome:** O nome da conta.
  - **Saldo Inicial:** O saldo inicial da conta.

Essas entidades serão relacionadas de maneira a facilitar consultas eficientes e fornecer uma experiência de usuário fluida. A modelagem de dados será projetada para ser escalável, permitindo a adição de novas funcionalidades no futuro.

## 4 - Implementação

**Tecnologias:** O aplicativo será desenvolvido usando Kotlin para Android e futuramente Swift para iOS. Para o backend, será usado Node.js com um banco de dados Postgres.
## 5 - Teste

### Estratégia de Teste
- **Testes Unitários**: Implementação de testes unitários para validar cada função e método individualmente.
- **Testes de Integração**: Verificação da comunicação e funcionamento conjunto das diferentes partes do aplicativo.
- **Testes de Carga**: Avaliação da capacidade do aplicativo de suportar um grande número de usuários simultâneos.
- **Testes de Interface do Usuário**: Garantia de que a interface seja intuitiva e amigável.
- **Testes de Segurança**: Assegurar a proteção contra ameaças, dada a sensibilidade das informações financeiras.
- **Testes de Aceitação do Usuário**: Confirmação de que o aplicativo atende às necessidades e expectativas dos usuários.
- **CI/CD**: Adoção de Integração Contínua e Entrega Contínua para detecção e correção rápida de problemas.

## 6 - Manutenção

### Estratégia de Manutenção
- **Monitoramento Contínuo**: Observação constante do desempenho do aplicativo para prevenção de problemas.
- **Atualizações Regulares**: Implementação de melhorias, correções de segurança e novas funcionalidades.
- **Backups Regulares**: Proteção dos dados dos usuários através de backups frequentes.
- **Documentação Atualizada**: Manutenção da documentação do código e infraestrutura para facilitar o onboarding e resolução de problemas.
- **Feedback dos Usuários**: Coleta e análise do feedback para aprimoramento contínuo do aplicativo.
- **Testes Automatizados**: Uso de testes automatizados para verificação rápida de regressões.
- **Refatoração Regular**: Melhoria contínua do código para manter a clareza e eficiência.
- **Treinamento da Equipe**: Atualização constante da equipe com treinamentos sobre melhores práticas e novas tecnologias.
