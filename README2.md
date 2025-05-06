
# Material de Estudo – Entrevista .NET Sênior

---

## C#

1. **O que é o Garbage Collector no C# e como ele funciona?**  
O Garbage Collector (GC) é um sistema automático de gerenciamento de memória que libera objetos que não estão mais sendo utilizados pela aplicação. Ele atua em ciclos, identifica objetos inacessíveis e libera sua memória.

2. **Qual a diferença entre ref, out e in?**  
- `ref`: exige que a variável seja inicializada antes de ser passada.  
- `out`: não exige inicialização, mas deve ser atribuída dentro do método.  
- `in`: passa o argumento por referência, mas somente leitura.

3. **O que são tipos por valor e tipos por referência?**  
- Valor: armazenado na stack (`int`, `bool`, `struct`).  
- Referência: armazenado na heap (`class`, `string`, `array`).

4. **Qual a diferença entre abstract, virtual e override?**  
- `abstract`: método que deve ser implementado nas subclasses.  
- `virtual`: método com implementação padrão que pode ser sobrescrito.  
- `override`: sobrescreve método virtual ou abstract.

5. **O que é LINQ e para que serve?**  
Permite consultar dados em coleções de forma declarativa, como SQL, direto no C#.

6. **Explique o conceito de async e await.**  
Programação assíncrona: `async` marca o método e `await` aguarda uma `Task`, liberando a thread.

7. **Qual a diferença entre interface e classe abstrata?**  
- Interface: apenas assinaturas.  
- Classe abstrata: pode conter lógica parcial e métodos abstratos.

8. **O que é Boxing e Unboxing?**  
- Boxing: valor → objeto (por referência).  
- Unboxing: objeto → valor.

9. **O que é Nullable<T> ou ? em tipos?**  
Permite que tipos por valor aceitem `null`, ex: `int?`.

10. **Quais são os principais modificadores de acesso em C#?**  
- `public`: qualquer lugar  
- `private`: dentro da classe  
- `protected`: na classe e derivadas  
- `internal`: mesmo assembly  
- `protected internal`, `private protected`: escopos combinados

---

## SOLID

1. **O que é SOLID e qual seu objetivo?**  
Conjunto de 5 princípios de design orientado a objetos para melhorar manutenção e escalabilidade do código.

2. **S - Single Responsibility Principle**  
Uma classe deve ter apenas um motivo para mudar.

3. **O - Open/Closed Principle**  
Aberto para extensão, fechado para modificação.

4. **L - Liskov Substitution Principle**  
Classes derivadas devem substituir suas bases sem quebrar o comportamento esperado.

5. **I - Interface Segregation Principle**  
Múltiplas interfaces específicas são melhores que uma única genérica.

6. **D - Dependency Inversion Principle**  
Dependa de abstrações, não de implementações.

7. **Como aplicar SRP?**  
Separando responsabilidades: uma classe para regras, outra para persistência, etc.

8. **Como aplicar OCP?**  
Com interfaces e herança para estender comportamentos.

9. **Como aplicar DIP?**  
Usando injeção de dependência com containers como `Microsoft.Extensions.DependencyInjection`.

10. **Por que aplicar SOLID?**  
Facilita testes, manutenção e evolução do sistema.

---

## Entity Framework Core

1. **O que é EF Core?**  
ORM da Microsoft para acesso a bancos relacionais via LINQ.

2. **Diferença entre EF Core e EF6?**  
EF Core é mais leve, moderno e multiplataforma.

3. **O que são Migrations?**  
Controle de versão do banco baseado nas classes C#.

4. **DbSet<T> e DbContext?**  
- `DbSet<T>`: representa tabela.  
- `DbContext`: coordena entidades e acesso ao banco.

5. **Change Tracker?**  
Rastreia alterações feitas nas entidades carregadas.

6. **Lazy Loading?**  
Carrega entidades relacionadas automaticamente ao acessar a propriedade.

7. **Relacionamentos 1:1, 1:N, N:N?**  
Feitos com `HasOne`, `WithMany`, `HasMany`, etc.

8. **AsNoTracking()?**  
Desativa tracking, ideal para consultas apenas leitura.

9. **Fluent API?**  
Configuração programática de entidades no `OnModelCreating`.

10. **Transações?**  
Use `Database.BeginTransaction()` para controle manual.

---

## Dapper

1. **O que é o Dapper?**  
Micro ORM rápido que executa SQL e mapeia para objetos.

2. **Dapper vs EF Core?**  
Dapper é mais rápido, mas exige SQL manual.

3. **Como funciona?**  
Mapeia resultados via reflexão otimizada.

4. **É seguro contra SQL Injection?**  
Sim, usando parâmetros nomeados.

5. **SELECT com Dapper?**  
```csharp
var user = conn.QueryFirst<User>("SELECT * FROM Users WHERE Id = @Id", new { Id = 1 });
```

6. **Métodos comuns?**  
- `Query`, `QueryFirst`, `QuerySingle`, `Execute`.

7. **Joins e múltiplos objetos?**  
```csharp
conn.Query<A, B, A>("SELECT * FROM A JOIN B ON A.Id = B.AId", (a, b) => { a.B = b; return a; });
```

8. **Transações?**  
Usa `IDbTransaction`.

9. **Insert com retorno de ID?**  
```csharp
var id = conn.QuerySingle<int>("INSERT INTO Table (...) OUTPUT INSERTED.Id VALUES (...)");
```

10. **Quando usar Dapper?**  
Quando performance e controle são mais importantes que abstração.

---

## Microservices

1. **O que são Microservices?**  
Arquitetura em que cada funcionalidade da aplicação é implementada como um serviço independente.

2. **Vantagens:**  
- Escalabilidade independente  
- Deploy separado  
- Isolamento de falhas  
- Times autônomos

3. **Desafios:**  
- Orquestração  
- Comunicação entre serviços  
- Monitoramento e logging  
- Gerenciamento de dados

4. **Síncrono vs Assíncrono?**  
- Síncrono: via HTTP/gRPC  
- Assíncrono: via RabbitMQ, Kafka

5. **O que é um API Gateway?**  
Ponto único de entrada para múltiplos serviços. Gera roteamento, autenticação, cache, etc.

6. **Transações distribuídas?**  
Via Sagas, Eventual Consistency, mensageria.

7. **Autenticação entre serviços?**  
JWT + OAuth2 + IdentityServer.

8. **Service Discovery?**  
Localização automática de serviços. Ferramentas: Consul, Eureka, Kubernetes DNS.

9. **Resiliência?**  
Circuit Breaker, Retry, Timeout (via Polly).

10. **Ferramentas comuns?**  
ASP.NET Core, MassTransit, RabbitMQ, Ocelot, Serilog, Docker, Kubernetes.

---

## Kafka e RabbitMQ

1. **Diferença entre Kafka e RabbitMQ?**  
Kafka: streaming distribuído e persistente.  
RabbitMQ: broker tradicional baseado em filas.

2. **Quando usar Kafka?**  
Alta taxa de throughput, retenção longa, pipelines de dados.

3. **Quando usar RabbitMQ?**  
Roteamento complexo, confiabilidade, baixa latência.

4. **Kafka entrega garantida?**  
Sim: at most once, at least once, exactly once.

5. **RabbitMQ garante ordem?**  
Sim, em uma única fila e consumidor.

6. **Tópicos e partições no Kafka?**  
Tópico = categoria. Partições = paralelismo.

7. **Persistência:**  
Kafka = disco. RabbitMQ = configurável.

8. **Consumo em Kafka?**  
Via consumer groups e offset manual.

9. **.NET Clients?**  
Kafka: Confluent.Kafka  
RabbitMQ: RabbitMQ.Client ou MassTransit

10. **Quando usar cada um?**  
Kafka: eventos em escala. RabbitMQ: filas de tarefas e RPC.

---

## Princípios DRY, KISS, YAGNI

### DRY – Don’t Repeat Yourself  
Evite duplicação de lógica ou dados. Centralize comportamentos repetidos.

### KISS – Keep It Simple, Stupid  
Prefira o simples ao complexo. Soluções simples são mais fáceis de manter.

### YAGNI – You Aren’t Gonna Need It  
Não implemente nada que não for exigido agora.

**Exemplos de aplicação:**  
- Refatorar código repetido → DRY  
- Usar estrutura simples, evitar abstrações prematuras → KISS  
- Evitar criar configurações e parâmetros sem necessidade atual → YAGNI

---

## Domain-Driven Design (DDD)

1. **O que é DDD?**  
Foco em refletir o domínio do negócio em código, com modelagem rica e linguagem ubíqua.

2. **Modelo de Domínio?**  
Conjunto de entidades, value objects, serviços de domínio e agregados.

3. **Entidade?**  
Objeto com identidade única e ciclo de vida.

4. **Value Object?**  
Objeto imutável sem identidade (ex: CPF, Endereço).

5. **Agregado e Agregado Raiz?**  
Agregado: grupo de entidades. Raiz: garante regras e consistência.

6. **Serviço de Domínio?**  
Representa ações do domínio que não pertencem a uma entidade específica.

7. **Linguagem Ubíqua?**  
Vocabulário comum entre devs e especialistas do domínio.

8. **Camadas do DDD?**  
- Domínio  
- Aplicação  
- Infraestrutura  
- Interface/API

9. **Service de Aplicação vs Domínio?**  
- Aplicação: orquestra regras e persistência.  
- Domínio: contém lógica de negócio pura.

10. **Repositório?**  
Interface que encapsula persistência de agregados.

---

## Listas em C#

1. **O que é List<T>?**  
Coleção genérica de objetos com acesso por índice.

2. **Diferença de Array e List<T>?**  
Array tem tamanho fixo; List<T> é dinâmica e tem métodos úteis.

3. **Adicionar, remover, acessar:**  
```csharp
var lista = new List<string>();  
lista.Add("Item");  
lista.Remove("Item");  
var primeiro = lista[0];
```

4. **Filtrar com LINQ:**  
```csharp
var filtrados = lista.Where(x => x.StartsWith("A")).ToList();
```

5. **Ordenar:**  
```csharp
lista.Sort();  
lista.OrderBy(x => x.Prop).ToList();
```

6. **IEnumerable vs ICollection vs List:**  
- IEnumerable: leitura  
- ICollection: leitura + escrita  
- List: implementação completa

7. **Evitar nulls:**  
```csharp
public List<Produto> Produtos { get; set; } = new();
```

8. **Verificar vazia:**  
```csharp
if (!lista.Any()) { ... }
```

9. **Remover item em foreach?**  
Evitar! Use `for` ou lista auxiliar.

10. **Comparar listas:**  
```csharp
list1.SequenceEqual(list2)
```

---

## AWS

1. **O que é AWS?**  
Plataforma de serviços em nuvem da Amazon.

2. **Serviços comuns com .NET:**  
- EC2, S3, RDS, DynamoDB, SQS, SNS, Lambda

3. **Enviar para o S3:**  
```csharp
await s3.PutObjectAsync(new PutObjectRequest { BucketName = "bucket", FilePath = "arquivo.txt" });
```

4. **IAM?**  
Gerencia usuários e permissões com políticas.

5. **AWS Lambda?**  
Funções serverless acionadas por eventos.

6. **SQS vs SNS:**  
- SQS = fila  
- SNS = pub/sub

7. **Amazon RDS?**  
Banco relacional gerenciado (SQL Server, PostgreSQL...).

8. **Monitorar apps:**  
Com CloudWatch: logs, métricas, alertas.

9. **Secrets Manager?**  
Armazena e recupera senhas/segredos com segurança.

10. **Autenticação apps .NET:**  
Via AccessKey/Secret ou roles IAM associadas a instâncias.

---

## Docker e Kubernetes

1. **Docker?**  
Plataforma para empacotar aplicações em containers.

2. **Container vs VM?**  
Container compartilha kernel, VM simula hardware completo.

3. **Dockerfile?**  
Script para construir imagem.  
```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:7.0  
COPY . /app  
WORKDIR /app  
ENTRYPOINT ["dotnet", "MinhaApp.dll"]
```

4. **Imagem vs Container?**  
- Imagem: blueprint  
- Container: instância em execução

5. **Docker Compose?**  
Orquestra múltiplos containers com YAML.

6. **Kubernetes?**  
Orquestrador de containers com deploy, escalonamento, recovery.

7. **Pods, Deployments e Services?**  
- Pod: unidade mínima  
- Deployment: estratégia de deploy  
- Service: expõe pods

8. **Escalonamento?**  
Via Horizontal Pod Autoscaler (HPA).

9. **Persistência de dados:**  
Volumes (Docker) ou PV/PVC (Kubernetes).

10. **.NET + Docker + K8s:**  
Build → Push no ECR → Deploy no EKS com Helm/YAML

---

## CI/CD – CodeCommit, CodeBuild, CodePipeline

1. **O que é CI/CD?**  
Prática de integração e entrega contínuas com automação de testes e deploys.

2. **CodeCommit?**  
Repositório Git gerenciado pela AWS.

3. **CodeBuild?**  
Serviço de build que compila código, roda testes, gera artefatos.

4. **CodePipeline?**  
Orquestrador de todo o processo de CI/CD.

5. **Fluxo típico:**  
Commit → Pipeline → Build → Testes → Deploy

6. **buildspec.yml:**  
Define comandos de build/teste.  
```yaml
phases:  
  build:  
    commands:  
      - dotnet build
```

7. **Controle de acesso:**  
Via IAM policies e roles.

8. **Testes no build?**  
Sim. Basta configurar com `dotnet test` no buildspec.

9. **Deploy com ECS:**  
Build de imagem → Push no ECR → Atualizar ECS no Pipeline.

10. **Alternativas AWS:**  
GitHub Actions, GitLab CI, Amplify, CDK, CloudFormation.

---

## Design Patterns

1. **O que são Design Patterns?**  
Padrões reutilizáveis para problemas comuns de design.

2. **Tipos:**  
- Criacionais (Factory, Singleton)  
- Estruturais (Adapter, Decorator)  
- Comportamentais (Strategy, Observer)

3. **Singleton:**  
Uma única instância global.  
```csharp
private static readonly Logger _instance = new Logger();
```

4. **Factory:**  
Cria objetos encapsulando lógica de instância.

5. **Abstract Factory:**  
Cria famílias de objetos compatíveis.

6. **Strategy:**  
Permite trocar algoritmo em tempo de execução.

7. **Repository:**  
Encapsula acesso ao banco de dados.

8. **Mediator:**  
Centraliza comunicações (ex: MediatR).

9. **Decorator:**  
Adiciona comportamento sem modificar o objeto.

10. **Aplicação no .NET:**  
Utilização comum com DI, MediatR, validação, repositórios.

---

## Circuit Breaker

1. **O que é?**  
Previne chamadas repetidas para serviços instáveis.

2. **Quando usar?**  
Serviços externos sujeitos a falhas.

3. **Estados:**  
Closed → Open → Half-Open → Closed

4. **Transições:**  
- Falhas → Open  
- Timeout → Half-Open  
- Sucesso → Closed

5. **Polly em .NET:**  
```csharp
Policy.Handle<Exception>().CircuitBreakerAsync(3, TimeSpan.FromSeconds(30));
```

6. **Open = chamadas bloqueadas.**  
Resposta imediata de falha.

7. **Retry vs Circuit Breaker:**  
Retry tenta repetir, CB evita sobrecarga.

8. **Combinar policies:**  
Com `Policy.WrapAsync`.

9. **Monitoramento:**  
Logs, métricas, Application Insights.

10. **Riscos de não usar:**  
Sobrecarga, falhas em cascata, downtime.

---

## HTTP Status Codes

1. **O que são?**  
Indicadores do resultado da requisição HTTP.

2. **Categorias:**  
- 1xx: Informativos  
- 2xx: Sucesso  
- 3xx: Redirecionamento  
- 4xx: Cliente  
- 5xx: Servidor

3. **200 OK:**  
Requisição bem-sucedida.

4. **201 Created:**  
Recurso criado (ex: POST).

5. **204 No Content:**  
Sem conteúdo na resposta.

6. **400 Bad Request:**  
Erro de requisição malformada.

7. **401 vs 403:**  
- 401: Não autenticado  
- 403: Sem permissão

8. **404 Not Found:**  
Recurso não encontrado.

9. **500 Internal Server Error:**  
Erro inesperado no servidor.

10. **ASP.NET Core:**  
```csharp
return NotFound();  
return Ok(obj);  
return Created(...);  
return BadRequest(erro);
```

---

## Arquitetura de Software

1. **O que é?**  
Estrutura de alto nível da aplicação.

2. **Monolito vs Microsserviços:**  
Monolito = 1 app.  
Microsserviços = serviços independentes.

3. **Arquitetura em Camadas:**  
UI, Aplicação, Domínio, Infraestrutura.

4. **Arquitetura Hexagonal:**  
Domínio isolado com adaptadores externos.

5. **Clean Architecture:**  
Domínio no centro. Sem dependência externa.

6. **SOLID + Arquitetura:**  
Código desacoplado e testável.

7. **Cross-cutting concerns:**  
Log, autenticação, cache → Middlewares/Decorators.

8. **Separar domínio da infra?**  
Facilita testes e manutenções.

9. **CQRS:**  
Separar leitura (query) de escrita (command).

10. **Escolher arquitetura:**  
Baseado na complexidade, escala e tempo de vida do projeto.

---

## Redis

1. **O que é Redis?**  
Banco chave-valor em memória, usado como cache e armazenamento rápido.

2. **Quando usar Redis?**  
- Cache  
- Sessões  
- Locks  
- Contadores  
- Ranking

3. **Vantagens como cache?**  
Rapidez e suporte a expiração (TTL).

4. **Redis vs banco relacional:**  
Não relacional, baseado em memória.

5. **.NET com Redis:**  
```csharp
var db = ConnectionMultiplexer.Connect("localhost").GetDatabase();
```

6. **TTL (Time to Live):**  
```csharp
db.StringSet("key", "value", TimeSpan.FromMinutes(5));
```

7. **Persistência?**  
Opcional. Redis suporta AOF e RDB.

8. **Locks distribuídos:**  
Comando `SETNX` ou bibliotecas como RedLock.

9. **Escalável?**  
Sim, com clustering e replicação.

10. **Desvantagens:**  
- Volatilidade  
- RAM limitada  
- Risco de perda sem persistência

---
