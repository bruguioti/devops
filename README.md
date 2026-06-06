


##  Enterprise Cloud Architecture: C# WebAPI + Kubernetes CI/CD Pipeline

Este projeto foi desenvolvido com o objetivo de desenhar e implementar um ecossistema completo de desenvolvimento e operações (DevOps). Ele simula um ambiente de produção moderno, utilizando uma API em **C# (.NET 8)** containerizada com **Docker**, orquestrada via **Kubernetes** e totalmente automatizada com **GitHub Actions**.


###  Tecnologias e Ferramentas Utilizadas

* **Backend:** C# (.NET 8) WebAPI
* **Containerização:** Docker & Dockerfile multi-stage (otimização de imagem)
* **Orquestração:** Kubernetes (Manifestos de Deployment e Service)
* **Ambiente de Testes K8s:** Kind (Kubernetes in Docker)
* **CI/CD (DevOps):** GitHub Actions
* **Versionamento:** Git (Adotando o padrão **Conventional Commits**)


##  Arquitetura do Fluxo DevOps (CI/CD)

O pipeline foi desenhado para garantir qualidade e consistência a cada alteração de código. O fluxo funciona de forma 100% automatizada:

```text
[Desenvolvedor] ──(git push)──> [GitHub Repository]
                                         │
                               (Dispara o Git Actions)
                                         │
                                         ▼
                     ┌──────────────────────────────────────┐
                     │ 1. Checkout & Setup .NET 8 SDK       │
                     │ 2. Compilação & Restauração (.csproj) │
                     │ 3. Build da Imagem Docker            │
                     │ 4. Inicialização do Cluster K8s      │
                     │ 5. Inject da Imagem no Cluster       │
                     │ 6. Deploy & Validação dos Pods       │
                     └──────────────────────────────────────┘

```


##  Boas Práticas Demonstradas

### 1. Mensagens de Commit Padronizadas (Conventional Commits)

O histórico do repositório é mantido limpo e legível por meio de prefixos semânticos. Exemplos utilizados no ciclo de desenvolvimento:

* `feat:` Adição de novas funcionalidades, documentações ou componentes.
* `chore:` Configurações de infraestrutura, arquivos YAML e esteiras de CI/CD.
* `fix:` Correções de bugs em caminhos de arquivos, nomenclaturas ou falhas de build.

### 2. Pipelines Resilientes e Dinâmicos (Infra as Code)

A esteira do GitHub Actions foi configurada utilizando varreduras dinâmicas (`wildcards`). Isso mitiga erros humanos de digitação e garante resiliência ao pipeline, localizando automaticamente arquivos `.csproj`, `Dockerfiles` e manifestos de Kubernetes (`deployment.yaml`) independentemente de divergências de maiúsculas e minúsculas geradas pelo Git local.



##  Como Executar este Projeto Localmente

### Pré-requisitos

* **Docker Desktop** instalado e em execução.
* **.NET 8 SDK** instalado.

### 1. Clonar o repositório

```bash
git clone [https://github.com/bruguioti/devops.git](https://github.com/bruguioti/devops.git)
cd devops

```

### 2. Rodar o Container Docker Localmente

```bash
# Entrar na pasta do projeto backend
cd MinhaApiCloud

# Construir a imagem Docker
docker build -t minha-api-cloud:v1 .

# Executar o container localmente na porta 8080
docker run -d -p 8080:8080 minha-api-cloud:v1

```

### 3. Testar os Manifestos do Kubernetes Localmente

Se você possuir o `kubectl` e um cluster local (como Kind ou Minikube) configurados na sua máquina, aplique os manifestos da pasta de infraestrutura:

```bash
kubectl apply -f K8s/

```

---

 Desenvolvido por [Bruna Patricia Coutinho]!

```

