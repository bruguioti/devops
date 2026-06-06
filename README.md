#  Enterprise Cloud Architecture: C# WebAPI + Kubernetes CI/CD Pipeline

Este projeto foi desenvolvido com o objetivo de desenhar e implementar um ecossistema completo de desenvolvimento e operações (DevOps). Ele simula um ambiente de produção moderno, utilizando uma API em **C# (.NET 8)** containerizada com **Docker**, orquestrada via **Kubernetes** e totalmente automatizada com **GitHub Actions**.

---

##  Tecnologias e Ferramentas Utilizadas

* **Backend:** C# (.NET 8) WebAPI
* **Containerização:** Docker & Dockerfile multi-stage (otimização de imagem)
* **Orquestração:** Kubernetes (Manifestos de Deployment e Service)
* **Ambiente de Testes K8s:** Kind (Kubernetes in Docker)
* **CI/CD (DevOps):** GitHub Actions
* **Versionamento:** Git (Adotando o padrão **Conventional Commits**)

---

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