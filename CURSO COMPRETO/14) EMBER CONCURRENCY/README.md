# EMBER CONCURRENCY | EMBER.JS | ASYNCHRONOUS, TASK DECORATOR | RESTARTABLE, ENQUEUE, DROP, KEEPLATEST
Ember Concurrency é uma biblioteca para Ember.js que facilita o gerenciamento de tarefas assíncronas, como chamadas de API, requisições ao servidor e interações com elementos da interface do usuário. Ele simplifica o código e oferece um controle preciso sobre a execução dessas tarefas assíncronas. Vamos explorar alguns conceitos-chave relacionados ao Ember Concurrency.

**Tarefas (Tasks):**

Ember Concurrency introduz o conceito de "tarefas" (tasks). As tarefas são funções que podem ser executadas de forma concorrente e que podem ser controladas de maneira mais granular do que Promises comuns. Aqui estão algumas características das tarefas:

- Elas podem ser iniciadas, canceladas, e concluídas.
- Você pode definir estratégias de execução, como reiniciar uma tarefa se uma nova solicitação for feita antes de a anterior ser concluída.
- As tarefas podem ser associadas a componentes ou serviços.

**Decoradores de Tarefa (Task Decorators):**

O Ember Concurrency oferece decoradores de tarefa que simplificam a criação de tarefas. Os decoradores mais comuns são:

- `@task`: É o decorador principal para criar uma tarefa. Ele é usado para transformar uma função em uma tarefa.

- `@restartable`: Usado para criar uma tarefa que pode ser reiniciada se for iniciada novamente antes de ser concluída. É útil para ações que podem ser canceladas e substituídas por uma nova.

- `@enqueue`: Cria uma tarefa que garante que apenas uma instância dela seja executada por vez, enfileirando solicitações subsequentes.

- `@drop`: Cria uma tarefa que ignora todas as solicitações subsequentes se uma tarefa já estiver em execução.

- `@keepLatest`: Semelhante ao `@restartable`, mas garante que apenas a última instância seja executada e as outras sejam canceladas automaticamente.

**Exemplo de Uso:**

Aqui está um exemplo simples de como você pode usar o decorador `@task` para criar e usar uma tarefa:

```javascript
// app/components/meu-componente.js
import Component from '@glimmer/component';
import { task } from 'ember-concurrency';

export default class MeuComponenteComponent extends Component {
  @task
  *minhaTarefa() {
    // Lógica assíncrona aqui
    yield new Promise((resolve) => {
      setTimeout(resolve, 2000);
    });
  }
}
```

Na classe do componente acima, `minhaTarefa` é uma tarefa que executa uma operação assíncrona. Você pode iniciar a tarefa chamando `this.minhaTarefa.perform()` em algum lugar do componente.

O Ember Concurrency oferece uma maneira eficaz de lidar com tarefas assíncronas em aplicativos Ember.js, simplificando o código e fornecendo controle sobre a execução dessas tarefas. Os decoradores de tarefa, como `@restartable`, `@enqueue`, `@drop` e `@keepLatest`, são ferramentas poderosas para ajustar o comportamento das tarefas com base nas necessidades do seu aplicativo.