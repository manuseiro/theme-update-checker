# Theme Update Checker

**Theme Update Checker** é uma biblioteca de verificação de atualização personalizada para temas do WordPress. Esta ferramenta permite adicionar notificações de atualização automática e atualizações com um clique para seus temas privados. Basta fornecer os detalhes do seu tema no arquivo `style.css`, e a biblioteca se encarregará de verificar periodicamente a URL para novas versões, exibindo uma notificação ao usuário quando necessário.

A interface de atualização utilizada é a padrão do WordPress, proporcionando uma experiência familiar para os usuários.

## Funcionalidades

- **Notificações Automáticas**: Alerta os usuários sobre novas versões disponíveis.
- **Atualizações com um Clique**: Facilita a atualização dos temas diretamente do painel do WordPress.
- **Fácil Integração**: Simples de configurar e usar com qualquer tema do WordPress.

## Instalação

### Passo 1: Definir o Token do GitHub

Adicione o seguinte código ao seu `wp-config.php`:

```php
define('GITHUB_AUTH_TOKEN', 'seu-novo-token-aqui');
```

### Passo 2: Incluir a Biblioteca no Tema

No arquivo functions.php do seu tema, inclua a biblioteca:

```php
require get_template_directory() . '/theme-update-checker/theme-update-checker.php';
```

### Passo 3: Configurar o Usuário e Repositório do GitHub

Adicione as seguintes linhas ao seu `functions.php`:

```php
$github_username = 'seu-usuario'; // Nome do usuário do github.com
$repository_name = 'seu-repositorio'; // Repositório usado para hospedar os arquivos do tema

add_theme_update_hooks($github_username, $repository_name, GITHUB_AUTH_TOKEN);

// Caso não queira definir GITHUB_AUTH_TOKEN no wp-config.php, você pode adicionar seu token diretamente no código:
// add_theme_update_hooks($github_username, $repository_name, 'seu-novo-token-aqui');
```

### Passo 4: Criar Releases e Tags no GitHub

Para que a biblioteca funcione corretamente, é necessário criar releases e associar tags no seu repositório do 

GitHub. Siga os passos abaixo:
1. Vá para a página do seu repositório no GitHub.
2. Clique na aba `Releases` na parte superior.
3. Clique no botão `Draft a new release`.
4. Preencha os campos:
- Tag version: A tag correspondente à versão do seu tema, por exemplo, v1.0.0.
- Release title: Um título descritivo para a release.
- Description: Descrição detalhada das mudanças nesta versão.
5. Faça upload do arquivo `zip` do seu tema no campo "Attach binaries by dropping them here or selecting them".
6. Clique em `Publish release`.

### Passo 5: Atualizar o style.css

No arquivo `style.css` do seu tema, certifique-se de que a versão do tema está corretamente definida. Por exemplo:

```css
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

### (Opcional) Depuração

Utilize a função `debug_theme_update_process` para verificar se o processo de atualização está funcionando corretamente:

```php
debug_theme_update_process(update_theme_from_github($github_username, $repository_name, GITHUB_AUTH_TOKEN));
```

## Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![GitHub issues](https://img.shields.io/github/issues/manuseiro/theme-update-checker)](https://github.com/manuseiro/theme-update-checker/issues) [![GitHub forks](https://img.shields.io/github/forks/manuseiro/theme-update-checker)](https://github.com/manuseiro/theme-update-checker/network) [![GitHub stars](https://img.shields.io/github/stars/manuseiro/theme-update-checker)](https://github.com/manuseiro/theme-update-checker/stargazers) [![GitHub contributors](https://img.shields.io/github/contributors/manuseiro/theme-update-checker)](https://github.com/manuseiro/theme-update-checker/graphs/contributors)

## Contribuição

Contribuições são bem-vindas! Por favor, leia o [guia de contribuição](CONTRIBUTING.md) para obter mais detalhes sobre como enviar solicitações pull, relatar problemas, etc.




