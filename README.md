# Theme Update Checker

Esta é uma biblioteca de verificação de atualização personalizada para temas do WordPress. Ele permite adicionar notificações de atualização automática e atualizações com um clique aos seus temas privados. Tudo o que você precisa fazer é colocar os detalhes do seu tema no arquivo 'style.css'. A biblioteca verifica periodicamente a URL para ver se há uma nova versão disponível e exibe uma notificação de atualização ao usuário, se necessário.

O verificador de atualização usa a interface de atualização padrão que é familiar para a maioria dos usuários do WordPress.

## Instalação

Defina o token do GitHub no `wp-config.php`:

```php
define('GITHUB_AUTH_TOKEN', 'seu-novo-token-aqui');
```

Inclua o arquivo `theme-update-checker.php` no `functions.php` do seu tema:

```php
require get_template_directory() . '/theme-update-checker/theme-update-checker.php';
```

No arquivo `functions.php`, configure o usuário e repositório do GitHub:
```php
$github_username = 'seu-usuario';// Nome do usuário do github.com
$repository_name = 'seu-repositorio';Repositorio usado para hospedar os arquivos do Tema

add_theme_update_hooks($github_username, $repository_name, GITHUB_AUTH_TOKEN);
 ```
Criar Releases e Tags no GitHub
Para que o script funcione corretamente, você precisa criar releases e associar tags no repositório GitHub do seu tema:

Criar uma Release no GitHub:
1. Vá para a página do seu repositório no GitHub.
2. Clique na aba "Releases" na parte superior.
3. Clique no botão "Draft a new release".
4. Preencha os campos:
- Tag version: A tag correspondente à versão do seu tema, por exemplo, v1.0.0.
- Release title: Um título descritivo para a release.
- Description: Uma descrição detalhada das mudanças nesta versão.
5. Faça upload do arquivo zip do seu tema no campo "Attach binaries by dropping them here or selecting them".
6. Clique em "Publish release".

No arquivo `style.css` do seu tema, certifique-se de que a versão do tema está corretamente definida. Por exemplo:

```CSS
/*
Theme Name: Nome do Tema
Theme URI: http://seudominio.com
Author: Seu Nome
Author URI: http://seudominio.com
Description: Descrição do tema.
Version: 1.0.0
License: GNU General Public License v2 or later
License URI: LICENSE.txt
Text Domain: seutema
*/
```

Use a função `debug_theme_update_process` para verificar se o processo de atualização está funcionando corretamente:

4. (Opcional) Use a função `debug_theme_update_process` para depuração:
    ```php
    debug_theme_update_process(update_theme_from_github($github_username, $repository_name, GITHUB_AUTH_TOKEN));
    ```

## Licença

Este projeto está licenciado sob a licença MIT.

    