# Theme Update Checker

Este script verifica e atualiza temas WordPress a partir de um repositório GitHub.

## Instruções

1. Defina o token do GitHub no `wp-config.php`:
    ```php
    define('GITHUB_AUTH_TOKEN', 'seu-novo-token-aqui');
    ```

2. Inclua o arquivo `theme-update-checker.php` no `functions.php` do seu tema:
    ```php
    require get_template_directory() . '/theme-update-checker/theme-update-checker.php';
    ```

3. No arquivo `functions.php`, configure o usuário e repositório do GitHub:
    ```php
    $github_username = 'seu-usuario';
	$repository_name = 'seu-repositorio';

	add_theme_update_hooks($github_username, $repository_name, GITHUB_AUTH_TOKEN);
    ```
4. Criar Releases e Tags no GitHub
Para que o script funcione corretamente, você precisa criar releases e associar tags no repositório GitHub do seu tema:

	Criar uma Release no GitHub:
        - Vá para a página do seu repositório no GitHub.
        - Clique na aba "Releases" na parte superior.
        - Clique no botão "Draft a new release".
        - Preencha os campos:
            -- Tag version: A tag correspondente à versão do seu tema, por exemplo, v1.0.0.
            -- Release title: Um título descritivo para a release.
            -- Description: Uma descrição detalhada das mudanças nesta versão.
        - Faça upload do arquivo zip do seu tema no campo "Attach binaries by dropping them here or selecting them".
        - Clique em "Publish release".

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
