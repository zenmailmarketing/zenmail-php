# PHP Zenmail API Client

Zenmail é a ferramenta de envio de email marketing criada pela [Templateria](https://templateria.com/). Esta biblioteca PHP é um cliente de sua API que permite a automação de qualquer recurso disponível no [painel web](https://app.zenmail.marketing).

O próprio painel do Zenmail consome sua API - essa é a nossa maneira de garantir uma API completa e fácil de usar.

## Instalação

Usando [Composer](https://getcomposer.org):

```bash
composer require templateria/zenmail-php
```

## Autenticação

Solicite um token de acesso ao suporte enviando um email para [alo@zenmail.marketing](mailto:alo@zenmail.marketing).

## Introdução

Todas as requisições à API passam por uma instância de `Zenmail\Client`:

```php
$zenmail = new Zenmail\Client([
    'token'      => 'seu token aqui'
    'account_id' => 9999
])
```

Através de interfaces fluentes, você acessa todos os recursos disponíveis na API:

```php
$contact = $zenmail->contacts->get('pedro@templateria.com'); // obtém um contato pelo email
$contact = $zenmail->contacts->get(58978456);                // ou então diretamente pelo ID
```

## Roadmap

Esta biblioteca encontra-se em estágio inicial de desenvolvimento. Estão disponíveis as seguintes operações:

Contatos
[x] criar contatos
[x] listar contatos
[x] buscar contatos
[x] remover contatos
[x] atualizar contatos

## Gerenciamento de Contatos

### Criar um Contato

```php
$zenmail->contacts->create([
    'email'   => 'pedro@templateria.com',
    'details' => ['nome' => 'Pedro']
]);
```

### Obter um Contato

```php
$contact = $zenmail->contacts->get('pedro@templateria.com'); // obtém um contato pelo email
$contact = $zenmail->contacts->get(58978456);                // ou então diretamente pelo ID
```

### Listar Contatos (com busca por email)

```php
// retorna todos os contatos do domínio templateria.com
$zenmail->contacts->find(['email' => '@templateria.com']);
```

### Atualizar um Contato

```php
$zenmail->contacts->update($contact->id, [
    'details' => [
        'nome'      => 'Pedro',
        'sobrenome' => 'Padron',
        'empresa'   => 'Templateria'
    ]
]);
```

### Remover um Contato

```php
$zenmail->contacts->delete($contact->id);
```

## Suporte

Acesse nossa [documentação](https://help.zenmail.marketing) para saber mais sobre o *Zenmail* e envie um email para [alo@zenmail.marketing](mailto:alo@zenmail.marketing) caso tenha alguma dúvida.

## Segurança

Para questões de segurança como vulnerabilidades encontradas ou outros assuntos, envie um email para [alo@zenmail.marketing](mailto:alo@zenmail.marketing).

## Changelog

Detalhes sobre cada versão desta biblioteca estão disponíveis no arquivo [CHANGELOG.md](CHANGELOG.md).

## Licença

MIT License. Copyright 2019 Templateria Ltda. Por favor, veja o [Arquivo de Licença](LICENSE.md) para mais informações.