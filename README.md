Biblioteca de integração PagSeguro para Java
===========================================

Descrição
---------

A biblioteca PagSeguro em Java é um conjunto de classes de domínio que facilitam, para o desenvolvedor Java, a utilização das funcionalidades que o PagSeguro oferece na forma de APIs. Com a biblioteca instalada e configurada, você pode facilmente integrar funcionalidades como:

 - Criar [requisições de pagamentos]
 - Criar [requisições de assinaturas]
 - Cancelar [assinaturas]
 - Cancelar [transações por código]
 - Estornar [transações por código]
 - Consultar [assinaturas]
 - Consultar [transações por código]
 - Consultar [transações por intervalo de datas]
 - Consultar [transações abandonadas]
 - Receber [notificações]


Requisitos Mínimos
------------------

 - [Java] 1.6+
 - [Gradle]

Instalação
----------

 - Baixe o repositório como arquivo zip ou faça um clone;
 - Descompacte os arquivos em seu computador;
 - Navega até a pasta *source*
 - Execute o comando ```gradle build```
 - Navegue até a pasta *build/libs*
 - Importe o arquivo ```pagseguro-api-*.*.*.jar``` para seu projeto
 - O diretório *public* contém exemplos de chamadas utilizando a API e o diretório *source* contém a biblioteca propriamente dita.


Configuração
------------

Para fazer uso real da biblioteca, é preciso fazer as configurações de credenciais e de ambiente.
As duas configurações seguem a ordem de precedência:

 - Manual
 - Propriedades do sistema
 - Arquivo (*pagseguro.properties*)
 - Variáveis do sistema


### Credenciais

É necessário configurar as credenciais do vendedor ou da aplicação. Segue abaixo como configurar de acordo com cada método.

#### Manual
```PagSeguro pagSeguro = PagSeguro.instance(Credential.applicationCredential("appId", "appKey"), PagSeguroEnv.SANDBOX);```
#### Propriedades do sistema
É necessário passar as opções para a JVM:
- Vendedor: ```-Dpagseguro.email="email" -Dpagseguro.token="token"```
- Aplicação: ```-Dpagseguro.appId="appId" -Dpagseguro.appKey="appKey"```

```PagSeguro pagSeguro = PagSeguro.instance();```
#### Arquivo
É necessário criar o arquivo *pagseguro.properties* dentro da pasta *resources* da sua aplicação e criar as propriedades:
- Vendedor:
```
    email=email
    token=token
```
- Aplicação:
```
    appId=appId
    appKey=appKey
```

```PagSeguro pagSeguro = PagSeguro.instance();```
#### Variáveis do sistema
É necessário criar as seguintes variáveis de ambiente:
- Vendedor: ```PSL_EMAIL``` e ```PSL_TOKEN```
- Aplicação: ```PSL_APP_ID``` e ```PSL_APP_KEY```

```PagSeguro pagSeguro = PagSeguro.instance();```




### Ambiente

É necessário configurar o ambiente do pagseguro que deseja utilizar. Segue abaixo como configurar de acordo com cada método.

#### Manual
- Sandbox:
```
Credential credential = Credential.sellerCredential("email", "token");
PagSeguroEnv environment = PagSeguroEnv.SANDBOX;
PagSeguro pagSeguro = PagSeguro.instance(credential, environment);
```
- Produção:
```
Credential credential = Credential.sellerCredential("email", "token");
PagSeguroEnv environment = PagSeguroEnv.PRODUCTION;
PagSeguro pagSeguro = PagSeguro.instance(credential, environment);
```


```  
PagSeguro pagSeguro = PagSeguro.instance(credential, environment);
```
#### Propriedades do sistema
É necessário passar as opções para a JVM:
- Sandbox: ```-Dpagseguro.environment="sandbox"```
- Produção: ```-Dpagseguro.environment="production"```

```PagSeguro pagSeguro = PagSeguro.instance();```
#### Arquivo
É necessário criar o arquivo *pagseguro.properties* dentro da pasta *resources* da sua aplicação e criar as propriedades:
- Sandbox: ```environment=sandbox```
- Produção: ```environment=production```

```PagSeguro pagSeguro = PagSeguro.instance();```
#### Variáveis do sistema
É necessário criar as seguintes variáveis de ambiente:
- Sandbox: ```PSL_PSL_ENVIRONMENT``` com valor: ```sandbox```
- Produção: ```PSL_PSL_ENVIRONMENT```  com valor: ```production```

```PagSeguro pagSeguro = PagSeguro.instance();```


Dúvidas?
----------
Caso tenha dúvidas ou precise de suporte, acesse nosso [fórum].


Changelog
---------
4.2.0
- Adicionado serviço de Recorrência Transparente:
  - Dev changelog:
      - 4.2.0.0-SNAPSHOT: Criação de sessão para recorrência transparente
      - 4.2.0.1-SNAPSHOT: criação de plano manual e automático
      - 4.2.0.2-SNAPSHOT: Adesão ao plano
      - 4.2.0.3-SNAPSHOT: Adicionado retorno da data (getDate()) nos métodos de criação de plano
      - 4.2.0.4-SNAPSHOT: Edição de valores do plano
      - 4.2.0.5-SNAPSHOT: Adicionado tratamento de retorno de erro para response sem body
      - 4.2.0.6-SNAPSHOT: Desconto para a próxima parcela da adesão

4.1.1
- Publicação da biblioteca no Repositório Global do Maven: ajustes no javadoc e melhorias gerais

4.1.0
- Melhorias e adicionado exemplos das transações de cancelamento e estorno (total e parcial)

4.0.0
- Remoção de funcionalidade depreciada (checkout com cartão de crédito internacional)

3.2.0
- Remoção de funcionalidades depreciadas

3.1.1
- Corrigido bug ao criar sessões (/sessions)

3.1.0
 - Adicionar parametros no header da requisição
 - Adicionar novas bandeiras de cartão de crédito

3.0.0
 - Criar requisições de pagamentos
 - Criar requisições de pagamentos com assinaturas
 - Criar requisições de cancelamento de transações
 - Criar requisições de estorno de transações
 - Consultar transações por código
 - Consultar transações por intervalo de datas
 - Consultar transações abandonadas
 - Consultar transações por código de referência
 - Criar requisições de autorizações
 - Consultar autorizações por código
 - Consultar autorizações por intervalo de datas
 - Consultar autorizações por código de notificação
 - Consultar autorizações por código de referência 
 - Criar requisições de assinaturas
 - Criar requisições de cancelamento de assinaturas
 - Criar requisições de cobrança de assinaturas
 - Consultar assinaturas por código
 - Consultar assinaturas por intervalo de datas
 - Consultar assinaturas por intervalo de dias
 - Consultar assinaturas por código de notificação
 - Receber notificações de autorizações
 - Receber notificações de assinaturas
 - Receber notificações de transações
 - Criar requisições de checkout transparente utilizando boleto
 - Criar requisições de checkout transparente utilizando debito online
 - Criar requisições de checkout transparente utilizando cartão de crédito

Licença
-------

Copyright 2016 PagSeguro Internet LTDA.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.


Notas
-----

 - O PagSeguro somente aceita pagamento utilizando a moeda Real brasileiro (BRL).
 - Certifique-se que o email e o token informados estejam relacionados a uma conta que possua o perfil de vendedor ou empresarial.
 - Certifique-se que tenha definido corretamente o charset de acordo com a codificação (ISO-8859-1 ou UTF-8) do seu sistema. Isso irá prevenir que as transações gerem possíveis erros ou quebras ou ainda que caracteres especiais possam ser apresentados de maneira diferente do habitual.
 - Para que ocorra normalmente a geração de logs, certifique-se que o diretório e o arquivo de log tenham permissões de leitura e escrita.
 - Para a utilizar o checkout transparente, é necessária a solicitação de ativação junto com a equipe do PagSeguro, maiores informações podem ser encontradas em [Como receber pagamentos pelo PagSeguro].


Contribuições
-------------

Achou e corrigiu um bug ou tem alguma feature em mente e deseja contribuir?

* Faça um fork
* Adicione sua feature ou correção de bug (git checkout -b my-new-feature)
* Commit suas mudanças (git commit -am 'Added some feature')
* Rode um push para o branch (git push origin my-new-feature)
* Envie um Pull Request
* Obs.: Adicione exemplos para sua nova feature. Se seu Pull Request for relacionado a uma versão específica, o Pull Request não deve ser enviado para o branch master e sim para o branch correspondente a versão.
* Obs2: Não serão aceitos PR's na branch master. Utilizar a branch de desenvolvimento.

  [gradle]: https://gradle.org/
  [java]: https://www.java.com
  [requisições de assinaturas]: http://download.uol.com.br/pagseguro/docs/pagseguro-assinatura-automatica.pdf
  [assinaturas]: http://download.uol.com.br/pagseguro/docs/pagseguro-assinatura-automatica.pdf
  [requisições de pagamentos]: https://dev.pagseguro.uol.com.br/documentacao/pagamentos
  [notificações]: https://pagseguro.uol.com.br/v3/guia-de-integracao/api-de-notificacoes.html
  [Checkout Transparente]: https://pagseguro.uol.com.br/receba-pagamentos.jhtml#checkout-transparent
  [transações por código]: https://pagseguro.uol.com.br/v3/guia-de-integracao/consulta-de-transacoes-por-codigo.html
  [transações por intervalo de datas]: https://pagseguro.uol.com.br/v2/guia-de-integracao/consulta-de-transacoes-por-intervalo-de-datas.html
  [transações abandonadas]: https://pagseguro.uol.com.br/v2/guia-de-integracao/consulta-de-transacoes-abandonadas.html
  [fórum]: https://comunidade.pagseguro.uol.com.br/hc/pt-br/community/topics
  [GitHub]: https://github.com/pagseguro/pagseguro-java-sdk
  [documentação oficial]: https://dev.pagseguro.uol.com.br/bibliotecas/java
  [Como receber pagamentos pelo PagSeguro]: https://pagseguro.uol.com.br/receba-pagamentos.jhtml#checkout-transparent

