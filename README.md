# Theme Update Checker (TUC)

Este script permite verificar e atualizar temas WordPress a partir de um repositório GitHub.

## Instalação

1. Baixe a biblioteca TUC deste repositório.
2. Adicione a biblioteca `theme-update-checker` ao diretorio do seu tema seu tema WordPress.

## Uso

3. Defina o token do GitHub no seu `wp-config.php`:

```php
define('GITHUB_AUTH_TOKEN', 'seu-token-aqui');
```

4. Inclua e configure o a biblioteca no arquivo `functions.php` do seu tema:

```php
require get_template_directory() . '/theme-update-checker/theme-update-checker.php';

```php
$github_username = 'seu-usuario';
$repository_name = 'seu-repositorio';
```

6. Adicionar hooks para verificar atualizações e adicionar informações adicionais sobre o tema
```php
add_theme_update_hooks($github_username, $repository_name, GITHUB_AUTH_TOKEN);
```
7. Opcional: Exemplo de uso para depuração
```php
debug_theme_update_process(update_theme_from_github($github_username, $repository_name, GITHUB_AUTH_TOKEN));
```
