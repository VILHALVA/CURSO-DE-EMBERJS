# EMBER TESTING PART 1
**Testes no Ember - Parte 1: Testes Unitários**

Os testes são uma parte fundamental do desenvolvimento de aplicativos Ember.js. Eles ajudam a garantir que o código esteja funcionando corretamente e que as alterações não introduzam erros. Nesta primeira parte, vamos explorar os testes unitários no Ember, incluindo os tipos de testes, a velocidade e o valor dos testes, a estrutura de arquivos de teste e como escrever seu próprio teste unitário.

**Tipos de Testes:**

Existem diferentes tipos de testes que podem ser realizados em um aplicativo Ember.js:

1. **Testes Unitários**: Testam unidades individuais de código, como componentes, serviços, modelos, e outros.

2. **Testes de Integração**: Testam como várias unidades interagem umas com as outras, como a interação entre componentes.

3. **Testes de Aceitação**: São testes end-to-end que simulam a interação do usuário com o aplicativo.

4. **Testes de Unidade de Rotas**: Testam o comportamento das rotas do aplicativo.

Nesta parte, focaremos nos testes unitários.

**Velocidade e Valor dos Testes:**

Os testes unitários são rápidos e devem ser executados com frequência durante o desenvolvimento. Eles são valiosos para:

- Capturar erros precocemente e fornecer feedback rápido.
- Documentar o comportamento esperado de um componente ou unidade.
- Manter a qualidade do código durante o desenvolvimento contínuo.

**Estrutura de Arquivos de Teste:**

Em um aplicativo Ember, os arquivos de teste são normalmente organizados dentro de uma estrutura de diretórios separados. Aqui está uma estrutura de exemplo:

```
my-app/
  tests/
    unit/
      components/
      services/
      models/
      helpers/
```

Os testes unitários para componentes, serviços, modelos e helpers são mantidos em diretórios separados.

**Escrever um Teste Unitário:**

Aqui está um exemplo de como escrever um teste unitário para um componente Ember:

Suponha que você tenha um componente chamado "meu-botao" que exibe um botão simples. Vamos escrever um teste unitário para verificar se o botão é renderizado corretamente:

```javascript
// my-app/tests/unit/components/meu-botao-test.js
import { module, test } from 'qunit';
import { setupRenderingTest } from 'ember-qunit';
import { render, click } from '@ember/test-helpers';
import hbs from 'htmlbars-inline-precompile';

module('Unit | Component | meu-botao', function(hooks) {
  setupRenderingTest(hooks);

  test('it renders a button', async function(assert) {
    await render(hbs`<MeuBotao />`);
    
    assert.dom('button').exists();
  });

  test('it triggers an action on click', async function(assert) {
    this.set('onClick', () => {
      assert.ok(true, 'Action was triggered');
    });

    await render(hbs`<MeuBotao @onClick={{this.onClick}} />`);

    await click('button');
  });
});
```

Neste exemplo, usamos o módulo `qunit` e as funções de teste do QUnit para escrever nossos testes. O `setupRenderingTest` do `ember-qunit` configura o ambiente de teste para renderização de componentes. Usamos o `await render` para renderizar o componente e, em seguida, verificamos se o botão existe.

No segundo teste, configuramos um manipulador de eventos fictício que deve ser acionado quando o botão é clicado. Usamos o `await click` para simular um clique no botão e verificamos se a ação foi acionada.

Esses são exemplos básicos de testes unitários no Ember. Eles são valiosos para garantir que os componentes funcionem conforme o esperado. Você pode escrever testes adicionais para cobrir mais cenários e garantir a robustez do seu aplicativo.