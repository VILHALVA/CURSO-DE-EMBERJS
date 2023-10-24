# EMBER WITH TYPESCRIPT | EMBER.JS TUTORIAL | COMPONENT, ROUTER, CONTROLLER, SERVICE, HELPER
O uso de TypeScript com Ember.js é uma escolha excelente para desenvolver aplicativos Ember com tipagem estática e recursos avançados de verificação de tipo. Vou fornecer uma visão geral de como usar TypeScript com os principais conceitos em Ember.js, incluindo componentes, roteadores, controladores, serviços e helpers.

**Configurando um Projeto Ember.js com TypeScript:**

1. Crie um novo aplicativo Ember.js com TypeScript usando o Ember CLI:

   ```bash
   ember new my-app --lang=ts
   ```

2. Instale os tipos de TypeScript para Ember:

   ```bash
   npm install --save-dev @types/ember
   ```

**Componentes:**

Os componentes são a base da interface do usuário em Ember.js. Eles são usados para criar elementos reutilizáveis da interface do usuário. Com TypeScript, você pode definir os tipos de propriedades e argumentos que um componente aceita. Aqui está um exemplo:

```typescript
// app/components/my-component.ts
import Component from '@glimmer/component';

interface MyComponentArgs {
  name: string;
}

export default class MyComponent extends Component<MyComponentArgs> {
  get formattedName() {
    return `Hello, ${this.args.name}!`;
  }
}
```

**Router (Roteador):**

O roteador no Ember.js é usado para definir as rotas e a navegação entre elas. Com TypeScript, você pode definir tipos para as rotas e seus modelos. Aqui está um exemplo:

```typescript
// app/routes/index.ts
import Route from '@ember/routing/route';

export default class IndexRoute extends Route {
  model() {
    return ['item1', 'item2', 'item3'];
  }
}
```

**Controladores:**

Os controladores são usados para lidar com a lógica da exibição e para processar os dados do modelo. Com TypeScript, você pode definir os tipos de dados usados no controlador. Aqui está um exemplo:

```typescript
// app/controllers/index.ts
import Controller from '@ember/controller';

interface IndexControllerModel {
  items: string[];
}

export default class IndexController extends Controller<IndexControllerModel> {
  get itemCount() {
    return this.model.items.length;
  }
}
```

**Serviços:**

Os serviços são usados para compartilhar lógica e dados entre partes do aplicativo. Com TypeScript, você pode definir tipos de dados que um serviço contém. Aqui está um exemplo:

```typescript
// app/services/my-service.ts
import Service from '@ember/service';

interface MyServiceData {
  message: string;
}

export default class MyService extends Service {
  data: MyServiceData = { message: 'Hello from service!' };
}
```

**Helpers:**

Os helpers são usados para criar funções que podem ser usadas em seus modelos e templates. Com TypeScript, você pode definir os tipos de entrada e saída de um helper. Aqui está um exemplo:

```typescript
// app/helpers/format-message.ts
import { helper } from '@ember/component/helper';

export function formatMessage([message]: [string]): string {
  return `Formatted: ${message}`;
}

export default helper(formatMessage);
```

Esses são alguns dos principais conceitos em Ember.js e como você pode usá-los com TypeScript. O uso de TypeScript proporciona a verificação de tipo estática e a melhoria da manutenção do código em aplicativos Ember.js, tornando-os mais robustos e fáceis de desenvolver. Certifique-se de seguir as práticas recomendadas e consultar a documentação do TypeScript e do Ember.js para obter informações mais detalhadas.