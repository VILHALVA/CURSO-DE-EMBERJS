# RENDERING - INTEGRATION TEST
**Testes de Renderização/Integração no Ember**

Vamos dar uma visão geral dos testes de renderização/integração no Ember.js, recapitular a estrutura dos testes, discutir como depurar testes de renderização/integração, e explicar como escrever testes para elementos DOM, seletores e chamadas de funções.

**Recapitulação:**

Os testes de renderização/integração no Ember.js são usados para verificar se os componentes interagem corretamente e se a interface do usuário é renderizada conforme o esperado. Eles testam a integração entre componentes, rotas e modelos. A biblioteca mais comum para escrever testes de integração no Ember.js é o "ember-qunit" ou o "ember-mocha."

**Estrutura de Arquivos:**

Os testes de renderização/integração geralmente são organizados na seguinte estrutura de diretórios:

```
my-app/
  tests/
    integration/
      components/
      acceptance/
```

Os testes de componentes de integração são mantidos no diretório "integration/components," enquanto os testes de aceitação (testes end-to-end) estão no diretório "acceptance."

**Como Depurar:**

Para depurar testes de renderização/integração no Ember.js, você pode usar as ferramentas de desenvolvedor do navegador. A inserção de `debugger;` no código do teste permitirá que você pause a execução e inspecione o estado atual. Além disso, você pode usar o "Ember Inspector" para visualizar a hierarquia de componentes e estados de aplicativos durante a execução do teste.

**Escrever Teste para Elementos DOM:**

Aqui está um exemplo de como escrever um teste para verificar se um elemento DOM específico é renderizado:

```javascript
// my-app/tests/integration/components/meu-componente-test.js
import { module, test } from 'qunit';
import { setupRenderingTest } from 'ember-qunit';
import { render } from '@ember/test-helpers';
import hbs from 'htmlbars-inline-precompile';

module('Integration | Component | meu-componente', function(hooks) {
  setupRenderingTest(hooks);

  test('it renders a specific DOM element', async function(assert) {
    await render(hbs`<MeuComponente />`);
    
    assert.dom('.element-class').exists();
  });
});
```

No teste acima, usamos `assert.dom('.element-class').exists();` para verificar se um elemento com a classe "element-class" está presente no componente renderizado.

**Testar Seletores:**

Você também pode testar elementos com seletores específicos:

```javascript
assert.dom('button[data-test="submit-button"]').exists();
```

Isso é útil para criar atributos `data-test` nos elementos para facilitar a seleção durante os testes.

**Escrever Teste para Chamada de Função:**

Você pode testar se uma função é chamada durante a interação do usuário. Por exemplo:

```javascript
// Verifique se a função "onButtonClick" é chamada quando o botão é clicado
await click('button');
assert.verifySteps(['onButtonClick']);
```

O método `assert.verifySteps` é usado para verificar se a função foi chamada.

Essas são algumas das práticas comuns para escrever testes de renderização/integração no Ember.js. Eles são úteis para garantir que a interface do usuário esteja funcionando corretamente e que os componentes interajam da maneira esperada. Certifique-se de personalizar os testes de acordo com as necessidades do seu aplicativo.