# @MediaPost API - Cliente PHP

## C�digo
### Inicializa��o
```php
<?php
// Autoloading
require 'vendor/autoload.php';

// Instanciando o client
$mapi = new Mapi\Client(
    '' /* $ConsumerKey */,
    '' /* $ConsumerSecret */,
    '' /* $Token */,
    '' /* $TokenSecret */
);
```

### Requisi��es
```php
<?php
// ...

// Requisi��es GET
$response = $mapi->get('url/do/recurso');

// Requisi��es DELETE
$response = $mapi->delete('url/do/recurso');

// Requisi��es POST
$response = $mapi->post('url/do/recurso', [
    'campo' => 'valor',
    'campo2' => 'valor2'
]);

// Requisi��es PUT
$response = $mapi->put('url/do/recurso', [
    'campo' => 'valor',
    'campo2' => 'valor2'
]);
```

### Respostas
Todas as requisi��es retornam um objeto do tipo `Mapi\Response`.
```php
<?php
// ...

// Retorna a quantidade de registros que o recurso pode retornar (desconsiderando a pagina��o)
var_dump($response->getTotalCount());

// Essa classe se comporta como um array...

// ... podendo ser iterada...
foreach ($response as $key => $value) {
    var_dump($key, $value);
}

// ... e tamb�m acessada
var_dump(count($response));
var_dump($response['key']);

// Se preferir lidar realmente com um array, basta invocar o m�todo toArray()
$arr = $response->toArray();
```

## Credenciais
Para acessar a API, voc� ir� precisar das quatro credenciais de acesso: _Consumer Key, Consumer Secret, Token_ e _Token Secret_.

Para requisitar esses dados, voc� deve entrar em contato com a equipe de Suporte, criando um chamado atrav�s de sua conta @MediaPost.

## Testes
A pasta _tests_ possui alguns arquivos para exemplificar o consumo dos recursos.

Antes de acessar algum desses testes, voc� precisar� modificar as credenciais encontradas no arquivo _conf.php_ nessa mesma pasta.

Toda a documenta��o est� dispon�vel em https://www.mediapost.com.br/api/.
