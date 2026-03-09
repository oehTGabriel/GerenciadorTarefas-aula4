# Gerenciador de Tarefas (ToDo List)

Aplicação Spring Boot com Thymeleaf para gerenciamento de tarefas.

## Tecnologias

- Java 21
- Spring Boot 4.0.3
- Thymeleaf
- Maven
- Bean Validation (Jakarta Validation)

## Como Executar

### Pré-requisitos

- Java 21 instalado
- Maven instalado (ou use o wrapper `./mvnw`)

### Executando

```bash
# Usando Maven Wrapper
./mvnw spring-boot:run

# Ou usando Maven instalado
mvn spring-boot:run
```

A aplicação será iniciada na porta **8080**.

## URLs Disponíveis

| URL                          | Método | Descrição                      |
|------------------------------|--------|--------------------------------|
| `/tarefas`                   | GET    | Listar todas as tarefas        |
| `/tarefas/novo`              | GET    | Formulário para nova tarefa    |
| `/tarefas/editar/{id}`       | GET    | Formulário para editar tarefa  |
| `/tarefas/salvar`            | POST   | Salvar tarefa (criar/atualizar)|
| `/tarefas/excluir/{id}`      | POST   | Excluir tarefa                 |
| `/tarefas/status/{id}`       | GET    | Alternar status da tarefa      |

## Estrutura do Projeto

```
com.biopark.tarefas/
├── TarefasAppApplication.java    # Classe principal
├── controller/
│   └── TarefaController.java     # Controlador MVC
├── service/
│   └── TarefaService.java        # Regras de negócio
├── repository/
│   └── TarefaRepository.java     # Armazenamento em memória
└── model/
    └── Tarefa.java                # Entidade Tarefa
```

## Funcionalidades

- Criar, editar e excluir tarefas
- Alternar status entre "Pendente" e "Concluída"
- Validação de formulários com mensagens de erro
- Mensagens flash de sucesso/erro
- 3 tarefas de exemplo pré-cadastradas
- Interface responsiva com CSS customizado

## Filtro de Tarefas e Contagem de Status

### Descrição

Foi adicionada uma funcionalidade que permite filtrar as tarefas exibidas na lista e visualizar um resumo com a quantidade total de tarefas, bem como quantas estão pendentes ou concluídas.

Essa funcionalidade melhora a visualização e organização das tarefas dentro do sistema.

---

## Filtros Disponíveis

A listagem de tarefas agora pode ser filtrada através de um parâmetro enviado na URL.

### Todas as tarefas

Exibe todas as tarefas cadastradas.

```
/tarefas
```

### Tarefas pendentes

Exibe apenas tarefas que ainda não foram concluídas.

```
/tarefas?filtro=pendentes
```

### Tarefas concluídas

Exibe apenas tarefas que já foram finalizadas.

```
/tarefas?filtro=concluidas
```

---

## Implementação no Controller

O método `listar` foi atualizado para:

* Buscar todas as tarefas
* Separar tarefas pendentes e concluídas
* Calcular a quantidade de cada tipo
* Aplicar o filtro recebido pela URL

Esse elemento utiliza **Thymeleaf** para renderizar dinamicamente os valores enviados pelo Controller.

---

## Benefícios da Funcionalidade

* Melhor visualização do estado das tarefas
* Possibilidade de focar apenas em tarefas pendentes ou concluídas
* Informações rápidas sobre o progresso das atividades

