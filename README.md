# Especificação de Requisitos do Sistema (ERS/SRS)

## Descrição Geral do Sistema
O sistema tem como objetivo gerenciar tarefas pessoais, permitindo que os usuários cadastrem, organizem e acompanhem suas atividades do dia a dia.
Ele é voltado para usuários comuns, como estudantes, trabalhadores e qualquer pessoa que deseje organizar melhor sua rotina.

As principais funcionalidades incluem:

- Cadastro, edição e exclusão de tarefas
- Definição de prioridades e prazos
- Marcação de tarefas como concluídas
- Visualização da lista de tarefas organizadas por data ou prioridade

O sistema opera em ambiente web e pode ser acessado através de navegadores em computadores ou celulares, oferecendo uma interface simples e intuitiva para facilitar o uso mesmo por pessoas sem experiência técnica.

---

## Requisitos Gerais

### Requisitos Funcionais (RF)

| ID   | Descrição                                                 | Prioridade |
| ---- | --------------------------------------------------------- | ---------- |
| RF01 | O usuário deve poder realizar login no sistema.           | Essencial  |
| RF02 | O sistema deve permitir o cadastro de tarefas.            | Essencial  |
| RF03 | O usuário deve poder excluir uma tarefa cadastrada.       | Essencial  |
| RF04 | O usuário deve poder editar uma tarefa já existente.      | Importante |
| RF05 | O sistema deve permitir marcar uma tarefa como concluída. | Importante |


### Requisitos Não Funcionais (RNF)

| ID    | Descrição                                                             | Prioridade |
| ----- | --------------------------------------------------------------------- | ---------- |
| RNF01 | O sistema deve responder em até 2 segundos por requisição.            | Essencial  |
| RNF02 | O acesso deve ser protegido por autenticação segura.                  | Essencial  |
| RNF03 | A interface deve ser intuitiva e responsiva.                          | Essencial  |
| RNF04 | O sistema deve estar disponível 99,5% do tempo mensal.                | Importante |
| RNF05 | O sistema deve ser compatível com os principais navegadores modernos. | Importante |


### Regras de Negócio (RN)

| ID   | Descrição                                                | Prioridade |
| ---- | -------------------------------------------------------- | ---------- |
| RN01 | Cada usuário deve possuir um e-mail único para cadastro. | Essencial  |
| RN02 | Uma tarefa concluída não pode ser editada.               | Essencial  |
| RN03 | O usuário só pode excluir tarefas que ele mesmo criou.   | Importante |

---

## Diagramas UML

### Diagrama de Caso de Uso
<p align="center">
<img src="https://github.com/user-attachments/assets/7add72f8-1885-49bf-bcc8-cb5fd463d6e0" alt="Diagrama de Caso de Uso" width="600">
</p>

*Este diagrama ilustra o escopo funcional do sistema, identificando o ator 'Usuário' e as ações que ele pode realizar, como Login, Cadastrar, Manter e Concluir tarefas. Ele também destaca regras de negócio importantes (notas em vermelho), como a unicidade do e-mail e restrições de edição para tarefas concluídas.*

### Diagrama de Sequência

<p align="center">
<img src="https://github.com/user-attachments/assets/49a74cd8-99d8-44dd-91c3-76cd04f3aa69" alt="Diagrama de Sequência" width="600">
</p>

*Este diagrama demonstra a interação técnica passo a passo para o caso de uso 'Cadastrar Tarefa'. Ele exibe a troca de mensagens cronológica entre as camadas do sistema (Usuário, Interface, Controlador e Banco de Dados), desde a solicitação inicial até a confirmação de que os dados foram salvos com sucesso.*

### Diagrama de Atividades

<p align="center">
<img src="https://github.com/user-attachments/assets/7d7b3369-2c3a-40c6-a6ba-8a5c8e27524f" alt="Diagrama de Atividades" width="600">
</p>

*Este diagrama mapeia o fluxo de navegação e a lógica do sistema. Ele detalha o caminho do usuário desde a tentativa de Login (com verificação de sucesso ou erro) até o acesso à lista de tarefas, onde pode-se iniciar um ciclo de cadastro e manutenção ou encerrar a sessão.*

## Arquitetura do Sistema

<p align="center">
<img src="https://github.com/user-attachments/assets/f91ed850-9e6a-49cc-a858-543947494cb8" alt="Arquitetura do Sistena" width="600">
</p>

# Arquitetura MVC - Sistema de Gerenciamento de Tarefas

Este documento explica a arquitetura MVC (Model-View-Controller) do sistema de gerenciamento de tarefas.

## 📋 Estrutura do Projeto

A arquitetura MVC divide a aplicação em três camadas principais, cada uma com responsabilidades específicas:

---

## 🔴 Model (Modelo)

Responsável pela lógica de negócios e manipulação de dados.

### Arquivos:
- **`Usuario.php`**
  - Gerencia os dados e operações relacionadas aos usuários
  - Funções: cadastro, autenticação, validações

- **`Tarefa.php`**
  - Gerencia os dados e operações relacionadas às tarefas
  - Funções: criar, editar, excluir, listar

---

## 🔵 Controller (Controlador)

Atua como intermediário entre Model e View, processando requisições do usuário.

### Arquivos:
- **`UsuarioController.php`**
  - Recebe requisições relacionadas a usuários (login, cadastro)
  - Coordena as ações entre o modelo `Usuario` e as views correspondentes

- **`TarefaController.php`**
  - Recebe requisições relacionadas a tarefas (criar, listar, atualizar)
  - Coordena as ações entre o modelo `Tarefa` e as views

---

## 🟢 View (Visualização)

Responsável pela interface visual com a qual o usuário interage.

### Arquivos:
- **`Login.html`** - Tela de autenticação
- **`Cadastro.html`** - Formulário de registro de novos usuários
- **`lista_tarefas.html`** - Página que exibe todas as tarefas
- **`form_tarefa.html`** - Formulário para criar/editar tarefas

---

## 🟡 Database (Banco de Dados)

Camada de persistência de dados.

### Arquivos:
- **`conexão.php`**
  - Estabelece a conexão com o banco de dados
  - Utilizado pelos Models para persistir e recuperar informações

---

## 🔄 Fluxo de Funcionamento
```
┌─────────┐         ┌──────────────┐         ┌─────────┐         ┌──────────┐
│  View   │ ──(1)──>│  Controller  │ ──(3)──>│  Model  │ ──(4)──>│ Database │
│         │ <─(7)── │              │ <─(5)── │         │ <─(4)── │          │
└─────────┘         └──────────────┘         └─────────┘         └──────────┘
    ↑                                              │
    └──────────────────────────────────────────────┘
```

### Passo a passo:

1. **Usuário interage com a View**
   - Exemplo: preenche o formulário de login

2. **View envia requisição para o Controller**
   - A requisição é direcionada ao controller apropriado

3. **Controller processa e chama o Model**
   - Controller apropriado (ex: `UsuarioController`) processa a requisição

4. **Model se comunica com o Database**
   - Model busca/salva dados no banco de dados via `conexão.php`

5. **Model retorna dados para o Controller**
   - Dados processados são enviados de volta

6. **Controller prepara os dados**
   - Organiza informações para apresentação

7. **Controller envia dados para a View**
   - View exibe as informações formatadas para o usuário

---

## ✅ Vantagens da Arquitetura MVC

- **Separação de responsabilidades**: Cada camada tem uma função específica
- **Manutenibilidade**: Facilita localização e correção de bugs
- **Reusabilidade**: Componentes podem ser reutilizados em diferentes partes
- **Trabalho em equipe**: Diferentes desenvolvedores podem trabalhar em camadas distintas
- **Testabilidade**: Cada camada pode ser testada independentemente

---
