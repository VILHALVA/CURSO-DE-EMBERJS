# SERVICES
**Serviços (Services): Visão Geral e Implementação**
Em Ember.js, os serviços são uma parte importante da arquitetura do aplicativo e permitem compartilhar lógica, dados e funcionalidades entre diferentes partes do aplicativo. Vamos dar uma visão geral dos serviços e como implementá-los no Ember.js.

**Visão Geral dos Serviços:**

Os serviços são objetos que podem ser injetados em várias partes do aplicativo para fornecer funcionalidades compartilhadas. Eles são uma maneira eficaz de gerenciar o estado global e a lógica em seu aplicativo Ember. Aqui estão algumas características importantes dos serviços:

1. **Injeção de Dependências**: Os serviços são injetados em controladores, componentes e rotas para fornecer funcionalidades comuns.

2. **Estado Global**: Os serviços podem conter estado global, tornando-os ideais para compartilhar informações e lógica entre diferentes partes do aplicativo.

3. **Acesso a Serviços de Terceiros**: Você pode usar serviços para acessar APIs de terceiros, como serviços de mapa, autenticação ou notificações.

4. **Testabilidade**: Os serviços são testáveis, o que facilita a escrita de testes unitários e de integração.

**Implementação de Serviços:**

Para criar um serviço no Ember.js, você pode usar o comando Ember CLI:

```bash
ember generate service meu-servico
```

Isso criará um arquivo JavaScript para o serviço em `app/services/meu-servico.js`. Aqui está um exemplo simples de um serviço que contém um contador:

```javascript
// app/services/meu-servico.js
import Service from '@ember/service';

export default class MeuServicoService extends Service {
  contador = 0;

  incrementar() {
    this.contador++;
  }

  reset() {
    this.contador = 0;
  }
}
```

Aqui, o serviço `meu-servico` possui uma propriedade `contador` e dois métodos, `incrementar` e `reset`, para interagir com essa propriedade.

Para injetar e usar o serviço em uma rota, controlador ou componente, você pode fazer o seguinte:

```javascript
import Controller from '@ember/controller';
import { inject as service } from '@ember/service';

export default Controller.extend({
  meuServico: service(),

  actions: {
    incrementarContador() {
      this.meuServico.incrementar();
    },
    resetContador() {
      this.meuServico.reset();
    }
  }
});
```

No exemplo acima, o serviço `meu-servico` é injetado no controlador usando `inject as service`, e os métodos do serviço podem ser chamados a partir do controlador.

Os serviços são uma maneira poderosa de compartilhar funcionalidades e estado entre várias partes de um aplicativo Ember. Eles são frequentemente usados para gerenciar coisas como autenticação, comunicação com APIs e armazenamento de estado global. 