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
