# Configuração do Cabeçalho X-Frame-Options

Este conjunto de diretivas é utilizado para configurar o cabeçalho HTTP `X-Frame-Options` no servidor Apache. O objetivo é melhorar a segurança do seu site, evitando ataques conhecidos como clickjacking, nos quais um invasor tenta enganar um usuário para clicar em algo diferente do que o usuário percebe.

### Configuração

1. **Verifique a Existência do Módulo `mod_headers`:**

   Certifique-se de que o módulo `mod_headers` do Apache esteja instalado e ativado. Você pode verificar isso executando o seguinte comando:

   ```bash
   a2enmod headers
   ```

   E, em seguida, reinicie o Apache:

   ```bash
   systemctl restart apache2
   ```

2. **Integração no seu Arquivo de Configuração do Apache ou em um arquivo .htaccess:**

   Adicione as seguintes linhas ao seu arquivo de configuração do Apache ou a um arquivo `.htaccess` no diretório desejado:

   ```apache
   <IfModule mod_headers.c>
       Header set X-Frame-Options "DENY"
   </IfModule>
   ```

3. **Entendendo as Diretivas:**

   - `<IfModule mod_headers.c>`: Garante que as configurações contidas dentro só serão aplicadas se o módulo `mod_headers` estiver carregado.

   - `Header set X-Frame-Options "DENY"`: Define o cabeçalho `X-Frame-Options` como "DENY", indicando que o conteúdo da página não deve ser exibido em nenhum frame.

### Notas

- **Compatibilidade:**
  - O cabeçalho `X-Frame-Options` pode impactar a maneira como seu site é incorporado em iframes. Certifique-se de que isso não afeta funcionalidades legítimas no seu site.

### Contribuições

Se você tiver sugestões ou melhorias, sinta-se à vontade para abrir um problema ou enviar um pedido de recebimento.

Mantenha seu site seguro contra ataques de clickjacking!
