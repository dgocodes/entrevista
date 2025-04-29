# Preparação Completa para Entrevista Dev .NET Senior - Perguntas e Respostas

---

# 1. Experiência com .NET Core

**Pergunta:**
> Fale sobre um projeto que você desenvolveu utilizando .NET Core.

**Resposta:**
> Trabalhei em um projeto de APIs RESTful utilizando .NET Core 6, aplicando Clean Architecture e princípios SOLID. Implementamos padrões como Repository Pattern, Unit of Work e utilizamos o mecanismo de Dependency Injection nativo. Também usamos AutoMapper para conversão de DTOs, FluentValidation para validações e xUnit com Moq para testes unitários.

**Exemplo prático:**
> API de produtos para um e-commerce, integrando com Elasticsearch para busca, banco de dados MySQL, e autenticação JWT.

---

# 2. AWS (DataMesh, Lambda, RDS, DynamoDB, ECS Fargate, API Gateway)

**O que são:**
- **AWS**: Amazon Web Services, plataforma de serviços de computação em nuvem.
- **Lambda**: Serviço de execução de funções serverless.
- **RDS**: Relational Database Service, banco de dados relacional gerenciado.
- **DynamoDB**: Banco de dados NoSQL altamente escalável.
- **ECS Fargate**: Serviço para execução de containers sem precisar gerenciar servidores.
- **API Gateway**: Gerenciamento e exposição de APIs.
- **DataMesh**: Arquitetura descentralizada de dados.

**Pergunta:**
> Como você arquitetaria uma aplicação .NET Core na AWS?

**Resposta:**
> Utilizaria ECS Fargate para hospedagem da aplicação, API Gateway para exposição das APIs, RDS MySQL para dados relacionais e DynamoDB para dados não-relacionais. Secrets Manager para armazenar credenciais sensíveis, e CloudWatch para logs e monitoramento.

**Exemplo prático:**
> Projeto de microserviços em que cada serviço era um container no Fargate, comunicando via EventBridge, com caching Redis usando ElasticCache.

---

# 3. Microserviços e Aplicações Distribuídas

**O que são:**
- **Microserviços**: Arquitetura onde o sistema é dividido em pequenos serviços independentes.
- **Aplicações Distribuídas**: Aplicações cujos componentes estão em diferentes máquinas/redes.

**Pergunta:**
> Quais desafios você enfrentou com microserviços?

**Resposta:**
> O maior desafio é garantir consistência e rastreabilidade. Utilizamos Event Sourcing para garantir integridade dos dados e tracing distribuído com X-Ray. Implementamos Dead Letter Queues para mensagens com erro.

**Exemplo prático:**
> Sistema de pedidos dividido em OrderService, PaymentService e InventoryService, comunicando via Kafka.

---

# 4. Banco de Dados (SQL Server, MySQL, DynamoDB)

**Pergunta:**
> Quando usar DynamoDB ou MySQL?

**Resposta:**
> MySQL é ideal para relações complexas e transações ACID. DynamoDB é recomendado para alta escalabilidade, leitura e escrita rápidas, com menos dependência de relações.

**Exemplo prático:**
> Projeto de catálogo de produtos: DynamoDB para consultas rápidas, MySQL para relações complexas.

---

# 5. Mensageria (Kafka)

**O que é:**
- **Kafka**: Plataforma de streaming distribuída para mensageria de alta performance.

**Pergunta:**
> Como foi seu uso de Kafka em projetos?

**Resposta:**
> Implementamos producers e consumers usando Confluent.Kafka no .NET Core. Utilizamos particionamento para escalabilidade e configuramos Dead Letter Topics para mensagens inválidas.

**Exemplo prático:**
> Sistema de notificações onde eventos de pedido disparavam mensagens para serviços de e-mail, SMS e dashboard.

---

# 6. Docker e Kubernetes

**O que são:**
- **Docker**: Plataforma para criação e execução de containers.
- **Kubernetes (K8s)**: Sistema de orquestração de containers.

**Pergunta:**
> Como você diferencia Docker e Kubernetes?

**Resposta:**
> Docker é usado para criar e rodar containers. Kubernetes é a plataforma de orquestração para gerenciar escalabilidade, alta disponibilidade e auto-reparação de containers.

**Exemplo prático:**
> Utilizamos um cluster EKS (Elastic Kubernetes Service) na AWS para hospedar microserviços.

---

# 7. CI/CD (CodeCommit, CodePipeline, CodeBuild)

**O que é CI/CD?**
> CI/CD significa Integração Contínua (Continuous Integration) e Entrega Contínua (Continuous Delivery).

**O que é CodeCommit?**
> Serviço de repositório de código (Git) da AWS.

**O que é CodePipeline?**
> Serviço de automação de fluxo de build, teste e deploy.

**O que é CodeBuild?**
> Serviço de build para compilar código e executar testes.

**Pergunta:**
> Como você estruturaria um pipeline CI/CD?

**Resposta:**
> Código versionado no CodeCommit. Cada push inicia o CodePipeline que executa build e testes no CodeBuild, e faz deploy automatizado no ECS Fargate.

**Exemplo prático:**
> Pipeline validava testes unitários antes de deploy automático em ambientes de staging e produção.

---

# 8. DevOps, Lean, Ágil

**O que são:**
- **DevOps**: Cultura de integração de desenvolvimento e operações.
- **Lean**: Princípios de eficiência e eliminação de desperdício.
- **Scrum/Kanban**: Metodologias ágeis de organização de trabalho.

**Pergunta:**
> Como DevOps e ágil aparecem no seu dia a dia?

**Resposta:**
> Pratico integração e entrega contínua (CI/CD) com CodePipeline. Participo de dailies, plannings e retrospectivas, usando Scrum ou Kanban.

---

# 9. Monitoramento e Observabilidade

**O que são:**
- **Observabilidade**: Capacidade de entender o que está acontecendo no sistema baseado em logs, métricas e traces.

**Pergunta:**
> Como você implementa observabilidade em aplicações?

**Resposta:**
> Logs estruturados no CloudWatch, métricas customizadas, alarmes e tracing distribuído com AWS X-Ray. Também utilizamos Datadog, Grafana e Dynatrace.

---

# 10. SOLID e Design Patterns

**O que é SOLID?**
> Conjunto de princípios para tornar o código modular e de fácil manutenção.

**Princípios SOLID:**
- S: Single Responsibility Principle (Responsabilidade unica)
- O: Open/Closed Principle (Aberto pra extensão fechado pra modificação)
- L: Liskov Substitution Principle (Uma classe derivada deve ser substituível por sua classe base.)
- I: Interface Segregation Principle (Uma classe não deve ser forçada a implementar interfaces e métodos que não irão utilizar.)
- D: Dependency Inversion Principle (Dependa de abstracoes nao de implementacoes)

- KISS:  "Keep It Simple, Stupid" (Mantenha Simples, Estúpido) e é um princípio de design de software que enfatiza a simplicidade e a clareza do código.
- DRY:   "Don't Repeat Yourself" (Não se repita). É um princípio que visa evitar a duplicação de código, tornando o código mais fácil de manter, legível e menos propenso a erros.
- YAGNI: "You Ain't Gonna Need It" (Você não vai precisar disso), é um princípio de desenvolvimento de software que enfatiza a importância de não adicionar funcionalidades ao código antes de serem realmente necessárias.

**Design Patterns:**
- Repository Pattern: Acesso a dados
- Factory Pattern: Criação de instâncias
- Singleton Pattern: Uma única instância
- Observer Pattern: Publicador/Assinante

---

# 11. System Design

**O que é:**
> Prática de planejar sistemas escaláveis e resilientes.

**Exemplo:**
> Sistema de e-commerce com API Gateway, ECS Fargate, Redis, MySQL e Kafka.

---

# 12. Arquiteturas de Software

**Clean Architecture:**
> Separação em camadas isoladas, independentes.

**Hexagonal Architecture:**
> Núcleo isolado com portas e adaptadores.

**Vertical Slice Architecture:**
> Organização por funcionalidades, não por camadas técnicas.

**Comparativo:**
- Clean: foco na regra de negócio.
- Hexagonal: foco na independência.
- Vertical Slice: foco em funcionalidades.

---
# 13. Status codes

**1xx - Informativo**

- 100 Continue: O servidor recebeu o começo da solicitação e o cliente pode continuar.
- 101 Switching Protocols: O servidor aceita mudar o protocolo de comunicação.

(Em geral, 1xx é pouco usado no dia a dia.)

**2xx - Sucesso**

- 200 OK: A requisição foi bem-sucedida. Resposta padrão para sucesso.
- 201 Created: Um novo recurso foi criado (geralmente após um POST).
- 204 No Content: A requisição foi processada, mas não há conteúdo para retornar.

**3xx - Redirecionamento**

- 301 Moved Permanently: O recurso foi movido permanentemente para outra URL.
- 302 Found (ou "Temporarily Moved"): O recurso foi encontrado em outra URL (temporário).
- 304 Not Modified: O recurso não foi modificado (usado em cache de navegador).

**4xx - Erro do cliente**

- 400 Bad Request: A requisição é inválida (sintaxe errada, parâmetros inválidos, etc.).
- 401 Unauthorized: Falta autenticação ou token inválido.
- 403 Forbidden: Autenticado, mas sem permissão para acessar.
- 404 Not Found: O recurso solicitado não foi encontrado.
- 409 Conflict: Conflito na requisição (por exemplo, duplicidade de dados).
- 422 Unprocessable Entity: A requisição está correta, mas não pode ser processada (dados inválidos para regras de negócio).

**5xx - Erro do servidor**

- 500 Internal Server Error: Erro inesperado no servidor.
- 502 Bad Gateway: O servidor recebeu uma resposta inválida de outro servidor (erro de gateway/proxy).
- 503 Service Unavailable: O servidor está temporariamente indisponível (sobrecarga, manutenção).
- 504 Gateway Timeout: O servidor não recebeu resposta a tempo de outro servidor (timeout).

**Dicas rápidas**

2xx: Tudo certo ✅
3xx: Redirecionamento ↪️
4xx: Culpa do cliente ⚠️
5xx: Culpa do servidor 🔥

---

# 13. Status codes

# Perguntas Adicionais

**Pergunta:**
> Como você faz troubleshooting em uma aplicação distribuída?

**Resposta:**
> Faço tracing distribuído, monitoro logs e analiso métricas.

**Pergunta:**
> Já precisou fazer rollback de um deployment? Como procedeu?

**Resposta:**
> Utilizamos estratégias como Blue/Green Deployment.

**Pergunta:**
> Como garantir resiliência em ambientes distribuídos?

**Resposta:**
> Retry policies, circuit breakers, fallback, multi-AZ.

**Pergunta:**
> Como gerencia segredos e variáveis sensíveis na AWS?

**Resposta:**
> AWS Secrets Manager e encriptação com KMS.

**Pergunta:**
> Como faz tuning de performance em APIs .NET Core?

**Resposta:**
> Otimização de queries, caching, compressão de respostas e ajuste de pool de conexões.

---
# 14. Verbos HTTP

Os **verbos HTTP** (também chamados de métodos) definem a ação que será realizada em um recurso da web. Abaixo estão os principais verbos:

## GET
- **Descrição**: Recupera dados de um recurso.
- **Exemplo**: Buscar a lista de produtos.
- **Características**:
  - Não altera o estado do servidor (é seguro).
  - Pode ser armazenado em cache.

| **Path Parameter**     | **Query Parameter**      |
| Identifica um recurso	 | Filtra ou organiza dados |
| Obrigatório	           | Opcional                 |
| Parte da rota	         | Depois do ?              |

## POST
- **Descrição**: Cria um novo recurso.
- **Exemplo**: Adicionar um novo produto.
- **Características**:
  - Pode alterar o estado do servidor.
  - Normalmente utilizado para envios de formulários.

## PUT
- **Descrição**: Atualiza um recurso existente ou cria um novo se ele não existir.
- **Exemplo**: Atualizar as informações de um produto.
- **Características**:
  - A operação é **idempotente** (múltiplas chamadas têm o mesmo efeito).

## PATCH
- **Descrição**: Atualiza parcialmente um recurso existente.
- **Exemplo**: Alterar apenas o preço de um produto.
- **Características**:
  - Não exige enviar todos os dados do recurso.
  - Pode ou não ser idempotente, dependendo da implementação.

## DELETE
- **Descrição**: Remove um recurso.
- **Exemplo**: Deletar um produto da base de dados.
- **Características**:
  - Pode ser idempotente (repetir a operação geralmente não gera erro).

## OPTIONS
- **Descrição**: Recupera os métodos HTTP suportados por um recurso.
- **Exemplo**: Verificar se `POST` é aceito em um endpoint.
- **Características**:
  - Usado frequentemente em pré-flights de CORS.

## HEAD
- **Descrição**: Similar ao `GET`, mas retorna apenas os cabeçalhos, sem o corpo.
- **Exemplo**: Checar se um recurso foi modificado sem baixar seu conteúdo.
- **Características**:
  - Útil para verificações rápidas de status.

---

# Resumo Rápido

| Verbo   | Ação principal                     | Idempotente | Altera servidor |
|---------|------------------------------------|-------------|-----------------|
| GET     | Ler um recurso                     | Sim         | Não             |
| POST    | Criar um recurso                   | Não         | Sim             |
| PUT     | Criar/atualizar um recurso         | Sim         | Sim             |
| PATCH   | Atualizar parte de um recurso      | Depende     | Sim             |
| DELETE  | Excluir um recurso                 | Sim         | Sim             |
| OPTIONS | Obter métodos suportados           | Sim         | Não             |
| HEAD    | Ler metadados de um recurso        | Sim         | Não             |


