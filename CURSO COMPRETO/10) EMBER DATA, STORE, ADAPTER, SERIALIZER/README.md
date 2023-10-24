# EMBER DATA, STORE, ADAPTER, SERIALIZER
No Ember.js, Ember Data é uma biblioteca que fornece uma maneira eficaz de interagir com APIs RESTful ou outras fontes de dados. O Ember Data é projetado para facilitar o armazenamento e a recuperação de dados em um aplicativo Ember. Vamos explorar os conceitos-chave relacionados ao Ember Data: Store, Adapter e Serializer.

**Store:**

O Store é uma parte fundamental do Ember Data e é responsável por gerenciar o estado da aplicação, o acesso aos dados e a manutenção de registros. Ele atua como uma camada intermediária entre seu aplicativo e sua fonte de dados, tornando mais fácil recuperar, criar, atualizar e excluir registros. O Store mantém um cache dos registros carregados e, assim, minimiza as requisições de rede, melhorando o desempenho.

Aqui está um exemplo de como você pode usar o Store para recuperar registros:

```javascript
import Route from '@ember/routing/route';

export default class MyRoute extends Route {
  model() {
    return this.store.findAll('post'); // Recupera todos os registros do tipo 'post'
  }
}
```

**Adapter:**

O Adapter é responsável por lidar com as chamadas de rede e determinar como os dados devem ser enviados e recebidos entre o Ember Data e a sua API. Existem diferentes tipos de Adapters, como RESTAdapter, JSONAPIAdapter, e o seu aplicativo pode usar o Adapter mais adequado ao formato da API que está sendo consumida.

Por exemplo, para usar o RESTAdapter, você pode configurá-lo assim:

```javascript
// app/adapters/application.js
import RESTAdapter from '@ember-data/adapter/rest';

export default class ApplicationAdapter extends RESTAdapter {
  host = 'https://api.example.com';
  namespace = 'api/v1';
}
```

**Serializer:**

O Serializer é responsável por converter os dados entre o formato em que estão na API e o formato em que são armazenados no Store. Cada Adapter está associado a um Serializer correspondente. O Serializer determina como os dados são serializados (convertidos para JSON) antes de serem enviados para a API e deserializados (convertidos de JSON) após serem recebidos da API.

Por exemplo, para usar o JSONAPISerializer:

```javascript
// app/serializers/application.js
import JSONAPISerializer from '@ember-data/serializer/json-api';

export default class ApplicationSerializer extends JSONAPISerializer {
  // Personalize o Serializer conforme necessário
}
```

Esses conceitos - Store, Adapter e Serializer - trabalham juntos para facilitar a comunicação com uma API e o gerenciamento de dados em um aplicativo Ember. Eles permitem que você realize operações de leitura e escrita em um Store local, que posteriormente são sincronizadas com a fonte de dados, proporcionando uma experiência de desenvolvimento eficaz e consistente.