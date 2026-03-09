# 🧾 Produto Service — Monitoramento com Prometheus e Grafana

Este é um projeto simples, mas bem útil, feito em Spring Boot 3.3.5, que mostra como monitorar uma aplicação usando Prometheus e Grafana.
A ideia é basicamente: levantar um serviço de pedidos, expor as métricas dele com o Actuator, deixar o Prometheus coletar essas métricas e visualizar tudo bonitinho no Grafana.

📚 **Disciplina:** Arquitetura de Aplicacoes Web 👨‍🏫 **Professor:** Leonardo Vieira Guimarãe 🏫 **Instituição:** Centro Universitário Newton Paiva ✍️ **Aluno:** Douglas Coimbra Laass.

---

## 🚀 Tecnologias Usadas

Aqui vai o combo usado no projeto:

* Java 17

* Spring Boot 3.3.5

* Spring Web

* Spring Boot Actuator

* Micrometer + Prometheus

* Swagger UI (Springdoc OpenAPI)

* Lombok

* Maven

---

## ⚙️ O que o projeto faz?

Expõe métricas em /actuator/prometheus

Permite monitorar coisas como CPU, threads, memória e afins

Integra direto com `Prometheus` e `Grafana`

Gera documentação automática da API com `Swagger`

Inclui health check e endpoints de gerenciamento

Nada muito absurdo — mas extremamente útil para quem quer aprender monitoramento na prática.

---

## 🧩 Como funciona o monitoramento?

Ferramentas | Para que servem?

`Actuator`	Expõe métricas e status da aplicação

`Micrometer`	Organiza e padroniza as métricas

`Prometheus`	Faz a coleta e armazena tudo

`Grafana`	Mostra dashboards bonitinhos

É quase uma corrente:

Spring Boot → Micrometer → Prometheus → Grafana.

---

## 🔧 Rodando o projeto

### 1️⃣ Clonar o repositório

```
git clone https://github.com/CoimbraDouglas/AppWeb_Monitoramento
cd AppWeb_Monitoramento
```

---

### 2️⃣ Build + Run

```
mvn clean package
mvn spring-boot:run
```

Depois disso, o serviço fica disponível em:
```
👉 http://localhost:8080
```

---

## 📊 Endpoints Úteis

Endpoint	O que faz

/actuator	Lista tudo que o Actuator expõe

/actuator/health	Diz se a aplicação está saudável

/actuator/prometheus	Endpoint que o Prometheus coleta

/swagger-ui.html	Documentação da API

---

## 🧠 Configurar Prometheus

No seu prometheus.yml, coloque algo assim:

```
scrape_configs:
  - job_name: 'pedido-service'
    metrics_path: '/actuator/prometheus'
    static_configs:
      - targets: ['host.docker.internal:8080']
```

⚠️ Se você estiver rodando fora de Docker, pode alterar o target para localhost:8080.

---

## 📈 Configurar Grafana

Abra o Grafana: http://localhost:3000

Vá em Connections > Data Sources > Add data source

Escolha Prometheus

Coloque a URL (geralmente http://localhost:9090)

Crie seu dashboard e adicione gráficos com métricas como:

* http_server_requests_seconds_count

* jvm_memory_used_bytes

* process_cpu_usage

* system_cpu_usage

---

## 🧰 Dependências principais

* spring-boot-starter-web	`API REST`

* spring-boot-starter-actuator	`Métricas e monitoramento`

* micrometer-registry-prometheus	`Exportar métricas`

* springdoc-openapi-starter-webmvc-ui	`Swagger`

* lombok	`Evita boilerplate e agiliza o código`

* spring-boot-starter-test	`Testes`

---

## 📦 Estrutura do projeto

```
pedido-service/
 ├── src/
 │   ├── main/
 │   │   ├── java/com/example/pedidoservice/
 │   │   └── resources/
 │   └── test/
 ├── pom.xml
 └── README.md
```

---

## 👨‍💻 Autor do Projeto

Douglas Coimbra

Repositório:
👉 https://github.com/CoimbraDouglas/AppWeb_Monitoramento




