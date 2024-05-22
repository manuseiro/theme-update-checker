# Theme Update Checker (TUC)

Este script permite verificar e atualizar temas WordPress a partir de um repositório GitHub.

## Instalação

1. Clone ou baixe este repositório.
2. Adicione o arquivo `theme-update-checker.php` ao seu tema WordPress.

## Uso

1. Defina o token do GitHub no seu `wp-config.php`:

```php
define('GITHUB_AUTH_TOKEN', 'seu-token-aqui');
```

Inclua e configure o script no functions.php do seu tema:

```php
require get_template_directory() . '/theme-update-checker.php';

Definir usuário e repositório do GitHub
```php
$github_username = 'seu-usuario';
$repository_name = 'seu-repositorio';
```

Adicionar hooks para verificar atualizações e adicionar informações adicionais sobre o tema
```php
add_theme_update_hooks($github_username, $repository_name, GITHUB_AUTH_TOKEN);
```
Opcional: Exemplo de uso para depuração
```php
debug_theme_update_process(update_theme_from_github($github_username, $repository_name, GITHUB_AUTH_TOKEN));
```
