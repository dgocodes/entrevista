**C#**

1. O que é o Garbage Collector no C# e como ele funciona?

O Garbage Collector (GC) é um sistema automático de gerenciamento de memória que libera objetos que não estão mais sendo utilizados pela aplicação. Ele atua em ciclos, identifica objetos inacessíveis e libera sua memória. Isso ajuda a prevenir vazamentos de memória sem que o desenvolvedor precise fazer a liberação manual.

2. Qual a diferença entre ref, out e in?

ref: exige que a variável seja inicializada antes de ser passada.

out: não exige inicialização, mas deve ser atribuída dentro do método.

in: passa o argumento por referência, mas somente leitura.

3. O que são tipos por valor e tipos por referência?

Valor (ex: int, bool, struct): armazenam os dados diretamente na stack.

Referência (ex: class, string, array): armazenam um ponteiro para o local da heap onde os dados estão.

4. Qual a diferença entre abstract, virtual e override?

abstract: método que deve ser implementado pelas classes filhas.

virtual: método com uma implementação padrão que pode ser sobrescrito.

override: indica que o método está sobrescrevendo um método virtual ou abstract.

5. O que é LINQ e para que serve?

LINQ (Language Integrated Query) permite consultar coleções de dados (como arrays, listas, banco, XML) de forma declarativa, similar a SQL, diretamente em C#.

6. Explique o conceito de async e await

São usados para programação assíncrona. async marca o método como assíncrono e await pausa sua execução até que uma Task seja concluída, liberando a thread para outras operações.

7. Qual a diferença entre interface e classe abstrata?

interface: define apenas a assinatura dos membros, sem implementação.

classe abstrata: pode conter implementação parcial, métodos abstratos e propriedades.

8. O que é Boxing e Unboxing?

Boxing: converte um tipo por valor em um tipo por referência (ex: int → object).

Unboxing: extrai o tipo por valor de dentro do objeto.

9. O que é Nullable<T> ou ? em tipos?

Permite que tipos por valor aceitem null. Ex: int? pode ter null, int não pode.

10. Quais são os principais modificadores de acesso em C#?

public: acessível por qualquer parte.

private: acessível somente dentro da classe.

protected: acessível na classe e nas derivadas.

internal: acessível dentro do mesmo assembly.

protected internal e private protected: combinações específicas de escopo.

---

**SOLID**

1. O que é SOLID e qual seu objetivo?
SOLID é um acrônimo para cinco princípios de design orientado a objetos que visam melhorar a manutenção, extensibilidade e legibilidade do código. Foi popularizado por Robert C. Martin (Uncle Bob).

2. O que significa o 'S' – Single Responsibility Principle?
Princípio da Responsabilidade Única: uma classe deve ter apenas um motivo para mudar. Ou seja, ela deve ter apenas uma responsabilidade ou função bem definida.

3. O que significa o 'O' – Open/Closed Principle?
Princípio Aberto/Fechado: uma classe deve estar aberta para extensão, mas fechada para modificação. Isso significa que o comportamento pode ser estendido sem alterar o código existente.

4. O que significa o 'L' – Liskov Substitution Principle?
Princípio da Substituição de Liskov: classes derivadas devem poder ser usadas no lugar das classes base sem quebrar a aplicação. Ou seja, o comportamento esperado não deve mudar.

5. O que significa o 'I' – Interface Segregation Principle?
Princípio da Segregação de Interfaces: uma classe não deve ser forçada a implementar métodos que não usa. É melhor ter várias interfaces pequenas e específicas do que uma única interface grande.

6. O que significa o 'D' – Dependency Inversion Principle?
Princípio da Inversão de Dependência: módulos de alto nível não devem depender de módulos de baixo nível, ambos devem depender de abstrações. Evita acoplamento direto entre classes.

7. Como aplicar SRP (Single Responsibility) na prática?
Dividindo funcionalidades em classes separadas, por exemplo: uma classe para persistência, outra para regras de negócio, outra para validação.

8. Como o OCP (Open/Closed) se aplica no dia a dia?
Utilizando interfaces e herança, podemos criar novas funcionalidades (ex: novos tipos de pagamento) sem alterar classes existentes.

9. Como o DIP (Dependency Inversion) é usado em C#?
Por meio de injeção de dependência (DI) usando interfaces e IoC containers, como o Microsoft.Extensions.DependencyInjection.

10. Qual a importância de SOLID em projetos reais?
Aplicar SOLID ajuda a criar sistemas mais modulares, fáceis de testar, dar manutenção e escalar, evitando efeitos colaterais ao modificar o código.

---

**Entity Framework Core**

1. O que é o Entity Framework Core?
É um ORM (Object-Relational Mapper) da Microsoft que permite trabalhar com banco de dados relacional usando objetos C#. Ele traduz consultas LINQ em SQL e faz o mapeamento entre classes e tabelas.

2. Qual a diferença entre EF Core e EF 6?
EF Core é uma reescrita moderna, multiplataforma e mais leve que o EF 6. Ele oferece melhor desempenho, suporte a .NET moderno, LINQ mais poderoso e mapeamentos mais flexíveis.

3. O que são Migrations no EF Core?
Migrations permitem versionar o esquema do banco de dados com base no modelo de classes. Comandos como Add-Migration e Update-Database aplicam essas mudanças automaticamente no banco.

4. O que são DbSet<T> e DbContext?

DbSet<T> representa uma tabela no banco de dados.

DbContext gerencia o ciclo de vida das entidades, rastreia alterações e realiza operações de CRUD no banco.

5. O que é o Change Tracker no EF Core?
É o componente que rastreia alterações nas entidades carregadas, identificando o que foi modificado, inserido ou excluído antes de salvar no banco com SaveChanges().

6. Como funciona o Lazy Loading no EF Core?
É o carregamento automático de entidades relacionadas quando a propriedade de navegação é acessada. Requer proxies ou carregamento manual com .Include().

7. Como aplicar relacionamentos (1:1, 1:N, N:N) no EF Core?
Por meio de propriedades de navegação e o uso de métodos como .HasOne(), .WithMany(), .HasForeignKey() no OnModelCreating. Desde o EF Core 5, o relacionamento N:N é suportado nativamente.

8. Como funciona o AsNoTracking()?
Desativa o rastreamento de mudanças nas entidades retornadas pela consulta, melhorando o desempenho em operações apenas de leitura.

9. O que é Fluent API no EF Core?
É uma forma de configurar o mapeamento entre classes e tabelas diretamente no código, usando o método OnModelCreating no DbContext, oferecendo mais controle do que os data annotations.

10. Como tratar transações no EF Core?
Pode-se usar Database.BeginTransaction() para agrupar várias operações em uma transação explícita. Também é possível usar transações implícitas com SaveChanges().

---

**Dapper**

1. O que é o Dapper?
Dapper é um micro-ORM (Object-Relational Mapper) desenvolvido pela equipe do Stack Overflow. Ele mapeia resultados de consultas SQL para objetos C# de forma rápida e leve, sem abstrair o SQL.

2. Quais as principais diferenças entre Dapper e EF Core?

Dapper: mais performático, controle total do SQL, sem tracking ou migrations.

EF Core: mais completo, oferece abstração, migrations, LINQ e tracking automático.

3. Como o Dapper funciona internamente?
Ele usa reflexão e geração de código IL para mapear resultados de queries diretamente para objetos, minimizando overhead e mantendo alta performance.

4. Dapper é seguro contra SQL Injection?
Sim, desde que se use parâmetros nomeados (@param) corretamente, o Dapper realiza o binding de parâmetros, prevenindo SQL Injection.

5. Como fazer um SELECT com Dapper?

csharp
Copiar
Editar
var sql = "SELECT * FROM Produtos WHERE Id = @Id";
var produto = connection.QueryFirstOrDefault<Produto>(sql, new { Id = 1 });
6. O que são métodos como Query, QueryFirst, Execute no Dapper?

Query<T>(): retorna múltiplos registros.

QueryFirst<T>(): retorna o primeiro registro.

QueryFirstOrDefault<T>(): primeiro ou default.

Execute(): para comandos INSERT, UPDATE e DELETE.

7. Como mapear relações (joins) com Dapper?
Com Query usando lambda para mapear múltiplos objetos:

csharp
Copiar
Editar
connection.Query<Pedido, Cliente, Pedido>(
    "SELECT * FROM Pedidos p JOIN Clientes c ON p.ClienteId = c.Id",
    (pedido, cliente) => { pedido.Cliente = cliente; return pedido; }
);
8. O Dapper tem suporte a transações?
Sim. Pode-se usar transações com IDbTransaction:

csharp
Copiar
Editar
using var tx = connection.BeginTransaction();
// Executa comandos com `transaction: tx`
tx.Commit();
9. Como fazer um INSERT com retorno de ID no Dapper?

csharp
Copiar
Editar
var sql = "INSERT INTO Produtos (Nome) VALUES (@Nome); SELECT CAST(SCOPE_IDENTITY() as int)";
var id = connection.QuerySingle<int>(sql, new { Nome = "Produto A" });
10. Quais os casos ideais para usar Dapper em vez de EF Core?

Quando a performance é crítica.

Em consultas complexas e específicas.

Quando o controle total sobre o SQL é necessário.

Em aplicações com poucas regras de domínio e foco em acesso direto ao banco.

---

**Microservices**

1. O que são Microservices?
Microservices são uma abordagem arquitetural onde uma aplicação é dividida em pequenos serviços independentes, que se comunicam entre si geralmente por HTTP ou mensageria, e que podem ser desenvolvidos, implantados e escalados separadamente.

2. Quais as principais vantagens dos Microservices?

Escalabilidade independente

Desenvolvimento paralelo entre times

Resiliência e isolamento de falhas

Deploys independentes

Tecnologias variadas por serviço (polyglot)

3. Quais os principais desafios dos Microservices?

Complexidade na orquestração e deploy

Gerenciamento de dados distribuídos

Monitoramento e observabilidade

Latência e falhas de rede

Controle de transações distribuídas

4. Qual a diferença entre comunicação síncrona e assíncrona entre microserviços?

Síncrona: geralmente via HTTP/REST ou gRPC, o cliente espera a resposta.

Assíncrona: via mensagens (ex: RabbitMQ, Kafka), não bloqueia a chamada e é ideal para desacoplamento.

5. O que é um API Gateway e qual seu papel em microservices?
É uma camada intermediária que centraliza chamadas de APIs, roteando requisições para os serviços corretos, além de aplicar autenticação, cache, logging e rate limiting.

6. Como lidar com transações distribuídas em microservices?
Usando padrões como Sagas (coordenadas ou coreografadas), eventual consistency e mensageria, ao invés de tentar manter transações ACID entre bancos diferentes.

7. Como gerenciar a autenticação e autorização entre microservices?

Com JWT (JSON Web Token) e OAuth2

Utilizando um Identity Provider centralizado (como IdentityServer, Keycloak)

Cada serviço valida o token sem armazenar sessões.

8. O que é Service Discovery?
É o processo de localizar dinamicamente os endereços dos microservices. Pode ser implementado com ferramentas como Consul, Eureka ou via DNS em ambientes como Kubernetes.

9. Como garantir resiliência entre microservices?
Utilizando padrões como:

Retry

Circuit Breaker

Timeouts

Fallbacks
Ferramentas como Polly no .NET ajudam a implementar esses padrões.

10. Quais ferramentas você usaria em uma arquitetura baseada em microservices no .NET?

ASP.NET Core para criação dos serviços

MassTransit ou CAP para mensageria

RabbitMQ, Kafka para filas

Ocelot como API Gateway

Polly para resiliência

Docker/Kubernetes para deploy

Serilog/Seq/Elastic Stack para logging

Prometheus/Grafana para métricas

---

**Kafka e RabbitMQ**

1. Qual a principal diferença entre Kafka e RabbitMQ?

RabbitMQ é um message broker tradicional baseado em filas, com suporte a padrões como Work Queues, Pub/Sub e RPC.

Kafka é uma plataforma de streaming distribuída, ideal para processamento de eventos em larga escala com retenção de mensagens e alta taxa de throughput.

2. Em quais casos Kafka é mais indicado?

Alta taxa de mensagens por segundo (milhões)

Processamento de eventos em tempo real

Retenção longa de mensagens

Pipelines de dados, analytics e event sourcing

3. Em quais casos RabbitMQ é mais indicado?

Simplicidade de uso

Processamento transacional e confiável de mensagens

Mensageria tradicional com confirmação de entrega

Cenários que exigem roteamento complexo com tópicos e headers

4. Kafka garante entrega de mensagens?
Sim, com três modos de entrega:

At most once: pode perder mensagens

At least once: pode duplicar

Exactly once: exige configuração adicional, disponível em contextos específicos

5. RabbitMQ garante ordem das mensagens?
Sim, dentro da mesma fila, as mensagens são entregues na ordem. Porém, com múltiplos consumidores em paralelo, essa ordem pode ser comprometida.

6. O que são tópicos e partições no Kafka?

Um tópico é como uma categoria para mensagens.

Cada tópico pode ter várias partições, que armazenam mensagens em ordem e permitem escalabilidade horizontal.

7. Como funciona a persistência de mensagens em Kafka e RabbitMQ?

Kafka armazena mensagens em disco por padrão, com retenção configurável (por tempo ou tamanho).

RabbitMQ também pode persistir mensagens se configurado, mas o foco principal é a entrega imediata.

8. Como é feito o consumo de mensagens no Kafka?
Consumidores fazem parte de consumer groups, e cada partição de um tópico é atribuída a apenas um consumidor do grupo. Isso garante paralelismo e balanceamento automático.

9. O que usar em .NET para integrar com Kafka e RabbitMQ?

Kafka: biblioteca Confluent.Kafka

RabbitMQ: RabbitMQ.Client ou MassTransit (que suporta ambos)

10. Kafka ou RabbitMQ: Qual escolher?
Depende do caso:

Use Kafka para alto volume, retenção, streaming, logs de eventos.

Use RabbitMQ para integração entre serviços, baixa latência e confiabilidade simples.

---

**Princípios de Desenvolvimento – DRY, KISS, YAGNI**

🔁 DRY – Don’t Repeat Yourself
Conceito: Evite duplicação de lógica ou código. Toda peça de conhecimento deve ter uma representação única, não duplicada, dentro do sistema.

Objetivo: Melhorar a manutenção e a clareza do código.

Exemplo ruim: múltiplas funções fazendo o mesmo cálculo com código copiado.

Exemplo bom: extrair lógica repetida para um método reutilizável.

👌 KISS – Keep It Simple, Stupid
Conceito: Mantenha o código o mais simples possível. Soluções simples são mais fáceis de entender, manter e menos propensas a bugs.

Objetivo: Evitar complexidade desnecessária.

Exemplo ruim: usar padrões complexos onde uma função resolveria.

Exemplo bom: preferir estruturas simples até que a complexidade seja realmente necessária.

🚫 YAGNI – You Aren’t Gonna Need It
Conceito: Não implemente funcionalidades que você acha que vai precisar no futuro. Só implemente o que é necessário agora.

Objetivo: Evitar desperdício de tempo e complexidade prematura.

Exemplo ruim: criar uma estrutura genérica sem haver demanda real.

Exemplo bom: desenvolver apenas as funcionalidades pedidas e refatorar quando necessário.

---

**Domain-Driven Design (DDD)**

1. O que é Domain-Driven Design (DDD)?
É uma abordagem de desenvolvimento de software centrada no modelo do domínio da aplicação, com foco em representar as regras de negócio de forma clara, usando linguagem ubíqua e separando responsabilidades em camadas.

2. O que é o "Modelo de Domínio"?
É a representação do negócio em código. Inclui entidades, agregados, serviços de domínio e objetos de valor, e busca refletir a lógica da área de negócio de forma precisa e expressiva.

3. O que é uma Entidade em DDD?
Uma entidade é um objeto que possui identidade própria e contínua no tempo, mesmo que seus atributos mudem. Exemplo: um Pedido com Id.

4. O que é um Objeto de Valor (Value Object)?
É um tipo de objeto imutável que não possui identidade. É identificado apenas por seus atributos. Exemplo: Endereco, CPF.

5. O que é um Agregado e o que é o Agregado Raiz?
Um agregado é um conjunto de entidades e objetos de valor que formam uma unidade de consistência.
O agregado raiz é a entidade principal que controla o acesso às outras partes do agregado.

6. O que é um Serviço de Domínio?
É uma classe que representa uma operação que pertence ao domínio, mas não se encaixa naturalmente em uma entidade ou value object. Deve ser stateless.

7. O que é a Linguagem Ubíqua?
É um vocabulário comum compartilhado entre desenvolvedores e especialistas do negócio, usado tanto no código quanto na comunicação verbal, para evitar ambiguidades.

8. Como o DDD organiza o projeto em camadas?
DDD tradicionalmente utiliza as seguintes camadas:

Domínio (entidades, value objects, serviços)

Aplicação (casos de uso)

Infraestrutura (acesso a dados, serviços externos)

Interface/API (entrada/saída)

9. Qual a diferença entre Service de Domínio e Service de Aplicação?

Serviço de domínio: contém regras de negócio puras, sem dependência de infraestrutura.

Serviço de aplicação: orquestra operações e interage com o domínio, repositórios e outros serviços.

10. O que é um Repositório em DDD?
Um repositório fornece uma abstração para persistência, permitindo obter e armazenar agregados sem expor detalhes da infraestrutura (ex: banco de dados).

---

**Listas em C#**

1. O que é List<T> em C#?
É uma coleção genérica que representa uma lista fortemente tipada de objetos acessíveis por índice. Faz parte do namespace System.Collections.Generic.

2. Qual a diferença entre List<T> e Array?

Array: tamanho fixo, mais performático em operações básicas.

List<T>: tamanho dinâmico, oferece métodos úteis como Add, Remove, Find, Where.

3. Como adicionar, remover e acessar itens em uma lista?

csharp
Copiar
Editar
var lista = new List<string>();
lista.Add("Item1");
lista.Remove("Item1");
var primeiro = lista[0];
4. Como filtrar uma lista usando LINQ?

csharp
Copiar
Editar
var nomes = lista.Where(n => n.StartsWith("A")).ToList();
5. Como ordenar uma List<T>?

csharp
Copiar
Editar
lista.Sort(); // Para tipos que implementam IComparable
lista.OrderBy(x => x.Propriedade).ToList(); // Com LINQ
6. Qual a diferença entre IEnumerable<T>, ICollection<T> e List<T>?

IEnumerable<T>: apenas leitura sequencial, ideal para LINQ.

ICollection<T>: permite manipulação (Add, Remove).

List<T>: implementação concreta de ICollection<T> com acesso por índice.

7. Como evitar NullReferenceException ao trabalhar com listas?
Inicializando a lista:

csharp
Copiar
Editar
public List<Produto> Produtos { get; set; } = new();
8. Como verificar se uma lista está vazia ou contém elementos?

csharp
Copiar
Editar
if (!lista.Any()) { ... }
if (lista.Count == 0) { ... }
9. O que acontece quando removemos um item de uma lista dentro de um foreach?
Vai lançar exceção (InvalidOperationException). Soluções:

Usar for ao invés de foreach

Criar uma lista auxiliar com os itens a remover

10. Como comparar listas em C#?

SequenceEqual compara itens em ordem:

csharp
Copiar
Editar
list1.SequenceEqual(list2)
Para comparação sem ordem, usar Set ou ordenação + comparação.

---

**AWS**

1. O que é a AWS?
Amazon Web Services é uma plataforma de computação em nuvem da Amazon que oferece serviços sob demanda, como computação, armazenamento, banco de dados, mensagens, autenticação, entre outros.

2. Quais serviços AWS são mais utilizados em aplicações .NET?

EC2 (máquinas virtuais)

S3 (armazenamento de objetos)

RDS (banco de dados relacional)

DynamoDB (NoSQL)

SQS (fila de mensagens)

SNS (notificações)

Lambda (funções serverless)

Secrets Manager (segredos)

CloudWatch (logs e métricas)

3. Como um sistema .NET pode enviar arquivos para o S3?
Utilizando o pacote AWSSDK.S3:

csharp
Copiar
Editar
var s3 = new AmazonS3Client();
await s3.PutObjectAsync(new PutObjectRequest {
    BucketName = "meu-bucket",
    Key = "arquivo.txt",
    FilePath = "caminho/local/arquivo.txt"
});
4. O que é IAM e qual sua importância?
IAM (Identity and Access Management) gerencia usuários, permissões e papéis. Ele é essencial para aplicar o princípio de menor privilégio e proteger o acesso a recursos AWS.

5. Como funciona o AWS Lambda?
Lambda permite executar código sem provisionar servidores. Ideal para tarefas pequenas e event-driven. Em .NET, você pode escrever handlers usando C# e publicá-los diretamente com o AWS Toolkit ou CLI.

6. Qual a diferença entre SQS e SNS?

SQS: sistema de filas (mensageria assíncrona ponto a ponto).

SNS: sistema de notificações (pub/sub), envia mensagens para múltiplos assinantes.

7. O que é o Amazon RDS?
É um serviço gerenciado de banco de dados relacional. Você pode usar SQL Server, PostgreSQL, MySQL, entre outros, com backups automáticos, escalabilidade e alta disponibilidade.

8. Como monitorar aplicações .NET na AWS?
Com CloudWatch, é possível enviar logs, métricas customizadas, configurar alarmes e visualizar dashboards.

9. O que é o AWS Secrets Manager?
Serviço para armazenar e gerenciar senhas, tokens e chaves de API com segurança. Pode ser integrado com a aplicação para recuperar segredos em tempo de execução.

10. Como autenticar uma aplicação .NET com a AWS?
Utilizando chaves de acesso (AccessKey/Secret) ou um perfil IAM associado à instância (quando hospedado na AWS). Melhor prática: usar IAM Role com permissões mínimas necessárias.

---

**Docker e Kubernetes**

1. O que é Docker e para que serve?
Docker é uma plataforma que permite empacotar aplicações e suas dependências em containers, garantindo portabilidade, consistência e facilidade de deploy em qualquer ambiente.

2. Qual a diferença entre container e máquina virtual?

Container: compartilha o kernel do host, mais leve e rápido para iniciar.

Máquina Virtual: simula hardware completo, com sistema operacional isolado, mais pesada.

3. Como funciona um Dockerfile?
É um script com instruções para construir uma imagem Docker. Exemplo básico para .NET:

dockerfile
Copiar
Editar
FROM mcr.microsoft.com/dotnet/aspnet:7.0
COPY . /app
WORKDIR /app
ENTRYPOINT ["dotnet", "MinhaApp.dll"]
4. O que é uma imagem e o que é um container?

Imagem: blueprint imutável com o código e dependências da aplicação.

Container: instância executável de uma imagem.

5. O que é o Docker Compose e quando usar?
Ferramenta para definir e rodar múltiplos containers com um único arquivo docker-compose.yml. Ideal para orquestrar ambientes locais com banco, API, cache, etc.

6. O que é o Kubernetes e qual seu papel?
Kubernetes (k8s) é uma plataforma de orquestração de containers. Ele gerencia o deploy, escalabilidade, balanceamento de carga, atualizações e saúde dos containers em um cluster.

7. O que são Pods, Deployments e Services no Kubernetes?

Pod: menor unidade executável; encapsula um ou mais containers.

Deployment: define como os pods devem ser criados, escalados e atualizados.

Service: expõe os pods para acesso interno ou externo, garantindo descoberta e balanceamento.

8. Como escalar uma aplicação no Kubernetes?
Usando kubectl scale ou configurando autoescalonamento com Horizontal Pod Autoscaler (HPA), baseado em CPU/memória.

9. Como persistir dados em containers/Kubernetes?
Com o uso de volumes:

Docker: volumes ou bind mounts

Kubernetes: PersistentVolume (PV) e PersistentVolumeClaim (PVC)

10. Como um desenvolvedor .NET pode usar Docker + Kubernetes?

Criando imagens com Docker e publicando no Docker Hub ou ECR

Usando Helm ou arquivos YAML para deploy em clusters

Integrando com Azure Kubernetes Service (AKS) ou Amazon EKS

Fazendo CI/CD com Docker build/push e kubectl apply

---

**CI/CD – CodeCommit, CodePipeline e CodeBuild (AWS)**

1. O que é CI/CD?
CI/CD (Integração Contínua / Entrega Contínua) é uma prática de DevOps onde o código é integrado, testado e entregue automaticamente em ambientes de produção ou homologação de forma contínua e confiável.

2. O que é o CodeCommit?
É o repositório Git da AWS. Similar ao GitHub, GitLab e Bitbucket, mas totalmente gerenciado pela AWS. Integra facilmente com serviços como CodePipeline e IAM.

3. O que é o CodeBuild?
Serviço de build contínuo da AWS. Ele compila o código, executa testes e gera artefatos (como pacotes, imagens, etc). Você configura com um buildspec.yml.

4. O que é o CodePipeline?
Serviço de orquestração de pipelines de CI/CD. Ele automatiza o fluxo de integração, testes, build e deploy. Conecta serviços como CodeCommit, CodeBuild, S3, ECS, Lambda, etc.

5. Qual é o fluxo típico de CI/CD com CodeCommit, CodeBuild e CodePipeline?

Desenvolvedor faz push para o CodeCommit.

CodePipeline detecta a mudança.

Aciona o CodeBuild para compilar e testar.

Deploy automático em S3, ECS, Lambda, etc.

6. Como funciona o buildspec.yml no CodeBuild?
É o arquivo de configuração do processo de build. Exemplo básico:

yaml
Copiar
Editar
version: 0.2
phases:
  build:
    commands:
      - dotnet build
artifacts:
  files:
    - '**/*'
7. Como controlar quem acessa o pipeline?
Com políticas de IAM. Você pode definir quem pode iniciar, editar ou visualizar pipelines, builds e repositórios, além de usar roles para serviços.

8. É possível integrar testes automatizados no CodeBuild?
Sim, basta adicionar comandos de teste no buildspec.yml, como:

yaml
Copiar
Editar
- dotnet test
Os resultados podem ser exportados como relatórios.

9. Como fazer deploy de uma aplicação .NET no ECS usando CI/CD?

Criar imagem Docker no CodeBuild

Fazer push no Amazon ECR

Configurar passo no CodePipeline que aciona ECS (Fargate ou EC2)

ECS atualiza os containers com a nova imagem

10. Quais alternativas AWS para CI/CD além do trio CodeCommit/CodeBuild/CodePipeline?

GitHub Actions + AWS CLI

GitLab CI/CD + AWS CLI

AWS Amplify (para front-end)

AWS CloudFormation / CDK (infraestrutura como código com deploys automatizados)

---

**Design Patterns**

1. O que são Design Patterns?
São soluções reutilizáveis para problemas comuns de design de software. São boas práticas documentadas para estruturar código de forma mais flexível, escalável e legível.

2. Quais são os 3 grupos clássicos de Design Patterns?

Criacionais: tratam da criação de objetos (ex: Singleton, Factory)

Estruturais: tratam da composição de classes/objetos (ex: Adapter, Decorator)

Comportamentais: tratam da comunicação entre objetos (ex: Strategy, Observer)

3. O que é o padrão Singleton e quando usá-lo?
Garante que uma classe tenha uma única instância e fornece um ponto global de acesso. Exemplo clássico: loggers, cache, configurações globais.

4. Como implementar o Singleton em C#?

csharp
Copiar
Editar
public sealed class Logger {
    private static readonly Logger _instance = new Logger();
    public static Logger Instance => _instance;
    private Logger() { }
}
5. O que é o padrão Factory e quando usá-lo?
Oculta a lógica de criação de objetos, centralizando a instância em uma fábrica. Útil quando a lógica de criação varia conforme parâmetros.

6. Qual a diferença entre Factory e Abstract Factory?

Factory cria um único tipo de objeto.

Abstract Factory cria famílias de objetos relacionados, garantindo compatibilidade entre eles.

7. O que é o padrão Strategy?
Permite definir múltiplas implementações intercambiáveis de um algoritmo, encapsulando-as em classes distintas. É útil para eliminar condicionais complexas.

8. O que é o padrão Repository?
Encapsula o acesso ao banco de dados, fornecendo uma interface consistente para persistência, desacoplando o domínio da infraestrutura de dados.

9. O que é o padrão Mediator (ex: MediatR)?
Centraliza a comunicação entre objetos, evitando acoplamentos diretos. No .NET, o MediatR implementa esse padrão com envio de comandos e eventos.

10. Como aplicar Decorator em C#?
Você pode usar composição para adicionar funcionalidades dinamicamente a um objeto:

csharp
Copiar
Editar
interface ICafe { string Servir(); }

class CafeSimples : ICafe {
    public string Servir() => "Café";
}

class CafeComLeite : ICafe {
    private readonly ICafe _baseCafe;
    public CafeComLeite(ICafe baseCafe) => _baseCafe = baseCafe;
    public string Servir() => _baseCafe.Servir() + " com leite";
}

---

**Circuit Breaker**

1. O que é o padrão Circuit Breaker?
É um padrão de resiliência que previne chamadas repetidas para um serviço falho, interrompendo temporariamente as requisições e permitindo a recuperação do sistema.

2. Em quais situações o Circuit Breaker é útil?

Quando um serviço externo está indisponível ou instável

Para evitar sobrecarga e cascata de falhas

Em sistemas distribuídos que dependem de múltiplos microserviços

3. Quais são os estados do Circuit Breaker?

Closed: todas as requisições passam normalmente

Open: chamadas são bloqueadas imediatamente

Half-Open: permite chamadas de teste para verificar se o serviço se recuperou

4. Como funciona a transição de estados?

De Closed para Open: após um número limite de falhas consecutivas

De Open para Half-Open: após um tempo configurado de espera (timeout)

De Half-Open para Closed: se a chamada de teste for bem-sucedida

5. Como implementar Circuit Breaker em .NET?
Utilizando a biblioteca Polly:

csharp
Copiar
Editar
Policy
  .Handle<HttpRequestException>()
  .CircuitBreakerAsync(3, TimeSpan.FromSeconds(30));
6. O que acontece quando o circuito está Open?
O sistema não tenta mais fazer chamadas para o serviço remoto. Retorna uma falha imediata (fallback) para o consumidor.

7. Qual a diferença entre Circuit Breaker e Retry?

Retry tenta repetir uma chamada que falhou.

Circuit Breaker bloqueia novas tentativas após falhas consecutivas, para dar tempo de recuperação ao serviço alvo.

8. É possível combinar Retry com Circuit Breaker?
Sim, é uma prática comum:

csharp
Copiar
Editar
var retryPolicy = Policy.Handle<Exception>().RetryAsync(3);
var circuitBreaker = Policy.Handle<Exception>().CircuitBreakerAsync(2, TimeSpan.FromSeconds(15));

var policyWrap = Policy.WrapAsync(retryPolicy, circuitBreaker);
9. Como monitorar o comportamento do Circuit Breaker?
Usando logs, métricas customizadas, ou ferramentas como Application Insights, Prometheus, Grafana, ou eventos emitidos via Polly telemetry.

10. Qual o impacto de não usar Circuit Breaker em microservices?

Sobrecarga contínua em serviços falhos

Cascata de erros entre serviços

Redução geral de disponibilidade e confiabilidade do sistema

Maior tempo de recuperação de falhas

---

**HTTP Status Codes**

1. O que são status codes HTTP?
São códigos numéricos retornados por um servidor para indicar o resultado de uma requisição. Eles seguem o padrão da especificação HTTP e ajudam o cliente a entender o que ocorreu.

2. Quais são as principais categorias de status codes?

1xx – Informativos

2xx – Sucesso

3xx – Redirecionamento

4xx – Erro do cliente

5xx – Erro do servidor

3. O que significa o status code 200?
OK – A requisição foi bem-sucedida e o servidor retornou os dados normalmente.

4. Quando utilizar o status code 201?
Created – Usado após uma requisição POST que resultou na criação de um recurso, como ao cadastrar um novo item.

5. Qual a diferença entre 204 e 200?

200 OK: resposta com conteúdo.

204 No Content: a requisição foi bem-sucedida, mas não há conteúdo no corpo da resposta.

6. Quando usar o código 400?
Bad Request – A requisição foi malformada ou tem dados inválidos. Exemplo: campos obrigatórios ausentes.

7. Qual a diferença entre 401 e 403?

401 Unauthorized: o usuário não está autenticado.

403 Forbidden: o usuário está autenticado, mas não tem permissão para acessar o recurso.

8. O que indica o status code 404?
Not Found – O recurso solicitado não foi encontrado no servidor.

9. O que significa 500 Internal Server Error?
Erro genérico que indica que o servidor encontrou uma falha inesperada durante o processamento da requisição.

10. Como retornar status codes corretamente em ASP.NET Core?
Exemplo com IActionResult:

csharp
Copiar
Editar
return NotFound(); // 404
return Ok(dados); // 200
return Created("/api/itens/1", item); // 201
return BadRequest(erro); // 400

---

**Arquitetura de Software**

1. O que é arquitetura de software?
É a definição da estrutura e organização de um sistema, incluindo seus componentes, interações, tecnologias, padrões e decisões de alto nível que impactam manutenibilidade, escalabilidade, performance e segurança.

2. Qual a diferença entre arquitetura monolítica e microsserviços?

Monolítica: toda a aplicação é empacotada e executada como um único processo.

Microsserviços: a aplicação é dividida em módulos independentes, com comunicação via APIs ou mensageria.

3. O que é a arquitetura em camadas?
É uma abordagem tradicional onde a aplicação é dividida em camadas com responsabilidades bem definidas:

Apresentação (UI)

Aplicação

Domínio (regra de negócio)

Infraestrutura (dados e serviços externos)

4. O que é arquitetura hexagonal (Ports & Adapters)?
Separa o núcleo da aplicação (domínio) de suas dependências externas por meio de portas (interfaces) e adaptadores. Facilita testes e evita acoplamento com frameworks.

5. O que é o padrão Clean Architecture?
Defende um modelo onde o domínio fica no centro e é completamente isolado das tecnologias externas (banco, web, frameworks). As dependências são sempre direcionadas para o centro.

6. Como se aplicam princípios SOLID à arquitetura?
SOLID ajuda a criar componentes coesos, desacoplados e testáveis, alinhando a estrutura interna da aplicação com os objetivos da arquitetura.

7. O que são cross-cutting concerns e como tratá-los?
São funcionalidades transversais a várias partes do sistema, como log, cache, autenticação. Devem ser tratados com middlewares, interceptadores ou decorators, evitando poluir o domínio.

8. Qual a importância de separar domínio da infraestrutura?
Evita acoplamento e facilita testes, manutenção e troca de tecnologias (ex: mudar banco ou API externa sem impactar regras de negócio).

9. O que é o padrão CQRS e quando aplicá-lo?
Command Query Responsibility Segregation separa as operações de leitura (Query) das de escrita (Command), ideal para sistemas com grande volume de leitura e lógica de escrita complexa.

10. Como decidir entre usar uma arquitetura mais simples ou uma mais robusta (como Clean Architecture)?
Depende do contexto:

Projetos pequenos ou com curto ciclo de vida: arquitetura mais simples e pragmática.

Projetos complexos, com muitas regras e integração externa: Clean Architecture ou Hexagonal trazem melhor manutenção e testabilidade a longo prazo.

---

**Redis**

1. O que é o Redis?
Redis é um banco de dados em memória, de código aberto, usado principalmente como cache, estrutura de dados chave-valor, pub/sub e armazenamento temporário. É extremamente rápido.

2. Quando usar Redis?
Use Redis quando precisar de:

Cache de dados para acelerar consultas frequentes

Sessões temporárias e armazenamentos voláteis

Filas simples ou pub/sub

Contadores ou ranking em tempo real

Gerenciamento de tokens, OTPs ou locks distribuídos

3. Por que usar Redis como cache?
Porque ele é extremamente rápido (opera em memória) e suporta expiração (TTL). Ideal para armazenar dados lidos com frequência e que mudam pouco.

4. Qual a diferença entre Redis e um banco relacional?
Redis armazena dados em memória, de forma não relacional e com estrutura simples (strings, hashes, sets, etc.). Bancos relacionais usam disco e possuem schema fixo.

5. Como configurar Redis em uma aplicação .NET?
Usando o pacote StackExchange.Redis:

csharp
Copiar
Editar
var redis = ConnectionMultiplexer.Connect("localhost");
var db = redis.GetDatabase();
db.StringSet("chave", "valor");
6. O que é TTL (Time To Live) no Redis?
É o tempo de vida de uma chave no cache. Após o TTL, o valor é automaticamente expirado:

csharp
Copiar
Editar
db.StringSet("chave", "valor", TimeSpan.FromMinutes(5));
7. Redis é persistente?
Sim, mas não é seu foco principal. Ele possui modos de persistência opcionais como RDB e AOF, mas o uso ideal é para dados voláteis ou temporários.

8. Como Redis é usado para controle de concorrência?
Redis pode ser usado para locks distribuídos, por exemplo usando SETNX para garantir que apenas uma instância execute uma ação crítica.

9. Redis funciona em aplicações escaláveis?
Sim, Redis é ideal para ambientes distribuídos, onde múltiplas instâncias da aplicação precisam acessar o mesmo cache ou sessão de forma eficiente.

10. Quais desvantagens ou cuidados ao usar Redis?

Dados são perdidos se não houver persistência configurada

Armazenamento limitado à memória RAM

Não é ideal para dados relacionais ou com consistência forte

Pode exigir replicação e alta disponibilidade para ambientes críticos

---

1. Testes Automatizados
Unit Tests, Integration Tests, Testes de Contrato

Ferramentas como xUnit, NUnit, Moq, FluentAssertions

Testes em APIs: TestServer, WebApplicationFactory

✅ Mostra domínio sobre qualidade e confiabilidade do código.

2. Mensageria com MassTransit ou CAP
Facilita integração com RabbitMQ ou Kafka

Suporte a retries, dead-letter, consumer/producer, sagas

Preferido em arquiteturas com eventos

✅ Valioso para projetos com microsserviços e mensageria robusta.

3. Segurança em APIs
JWT, OAuth2, Refresh Token

Autenticação vs Autorização

Rate limiting e validação de entrada

✅ Demonstra preocupação com práticas modernas e segurança.

4. Logging, Monitoramento e Observabilidade
Uso de Serilog, Elastic Stack (ELK), Application Insights, Grafana + Prometheus

Importância de correlação de logs (TraceId/SpanId)

✅ Indispensável para ambientes produtivos e troubleshooting.

5. Tolerância a falhas e Resiliência
Além de Circuit Breaker: Retry, Timeout, Fallback, Bulkhead (via Polly)

✅ Essencial em arquiteturas distribuídas e cloud-native.

6. Versionamento e Evolução de APIs
Versionamento por URL, Header ou Query

API Deprecation e compatibilidade

✅ Mostra maturidade no ciclo de vida de APIs.

7. Infraestrutura como Código (IaC)
Uso de Terraform, AWS CDK, ou CloudFormation

Automatização e versionamento de ambientes

✅ Muito valorizado em times DevOps e Cloud-first.