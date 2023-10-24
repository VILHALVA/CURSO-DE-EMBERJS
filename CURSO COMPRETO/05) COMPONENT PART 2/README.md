# COMPONENT PART 2
**Componente (Component) - Parte 2: Propriedades Monitoradas, Getter e Ações**

Nesta parte, vamos explorar as propriedades monitoradas (tracked properties), getters e ações em componentes do Ember.js.

**Propriedades Monitoradas (Tracked Properties):**

No Ember.js, as propriedades monitoradas são variáveis que podem ser rastreadas automaticamente quanto às mudanças e atualizações na interface do usuário quando elas mudam. Você pode definir propriedades monitoradas em componentes usando o decorador `@tracked`. Aqui está um exemplo:

```javascript
// app/components/my-component.js
import Component from '@glimmer/component';
import { tracked } from '@glimmer/tracking';

export default class MyComponentComponent extends Component {
  @tracked count = 0; // A propriedade 'count' é monitorada
}
```

Agora, a propriedade `count` será monitorada automaticamente quanto a mudanças, e qualquer alteração nela será refletida na interface do usuário.

**Getter (Método Get):**

Você pode usar métodos getter em componentes para calcular e retornar valores com base em outras propriedades monitoradas. Os getters são definidos com o prefixo `get` na frente de um método. Veja um exemplo:

```javascript
// app/components/my-component.js
import Component from '@glimmer/component';
import { tracked } from '@glimmer/tracking';

export default class MyComponentComponent extends Component {
  @tracked firstName = 'João';
  @tracked lastName = 'Silva';

  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

Neste exemplo, `fullName` é um getter que combina as propriedades `firstName` e `lastName` para retornar o nome completo.

**Ações (Actions):**

As ações permitem que os componentes respondam a eventos ou interações do usuário. Você pode definir ações em um componente usando o método `actions` e, em seguida, chamá-las em resposta a eventos. Aqui está um exemplo:

```javascript
// app/components/my-button.js
import Component from '@glimmer/component';
import { action } from '@ember/object';

export default class MyButtonComponent extends Component {
  @tracked clicks = 0;

  @action
  incrementClicks() {
    this.clicks++;
  }
}
```

No exemplo acima, definimos uma ação chamada `incrementClicks`, que é chamada quando o botão é clicado. Isso aumenta o valor de `clicks`, que é uma propriedade monitorada, e qualquer mudança em `clicks` será refletida na interface do usuário.

No template Handlebars, você pode chamar a ação assim:

```handlebars
{{! app/templates/components/my-button.hbs }}
<button {{on 'click' this.incrementClicks}}>
  Clique Aqui ({{clicks}})
</button>
```

A ação `incrementClicks` é vinculada ao evento de clique do botão.

Esses conceitos de propriedades monitoradas, getters e ações são componentes fundamentais do desenvolvimento no Ember.js e ajudam a criar interações dinâmicas e responsivas em seus aplicativos.