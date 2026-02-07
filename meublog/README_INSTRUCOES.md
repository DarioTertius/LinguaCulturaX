# 🚀 GUIA RÁPIDO - Configuração Simplificada (Sem Autenticação)

**Para quem vai gerenciar o blog**

---

## ✅ Passo 1: Criar a Planilha no Google Sheets

### 1.1. Criar Nova Planilha

1. Acesse [Google Sheets](https://sheets.google.com)
2. Clique em **"Em branco"** para criar nova planilha
3. Nomeie como: **"LinguaCulturaX Posts"**

### 1.2. Criar as Colunas

Na **primeira linha** (linha 1), digite exatamente estes nomes:

| A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|
| **ID** | **Título** | **Data** | **Autor** | **Resumo** | **Conteúdo** | **Slug** |

**IMPORTANTE:** Os nomes precisam estar EXATAMENTE assim (com acento e maiúsculas)!

### 1.3. Adicionar Posts de Exemplo

Copie e cole estas linhas como exemplo (linha 2 e 3):

**Linha 2:**
- **ID:** 1
- **Título:** Exemplo de Post
- **Data:** 02/02/2026
- **Autor:** linguacultura
- **Resumo:** Este é um post de exemplo para testar o sistema.
- **Conteúdo:** `<h2>Bem-vindo!</h2><p>Este é um post de exemplo.</p>`
- **Slug:** exemplo-de-post

**Linha 3:**
- **ID:** 2
- **Título:** Vocabulário Alemão - Cores
- **Data:** 02/02/2026
- **Autor:** linguacultura
- **Resumo:** Aprenda as cores em alemão de forma fácil e rápida.
- **Conteúdo:** `<h2>Cores em Alemão</h2><p>Vamos aprender!</p><ul><li><strong>rot</strong> - vermelho</li><li><strong>blau</strong> - azul</li><li><strong>grün</strong> - verde</li></ul>`
- **Slug:** vocabulario-alemao-cores

---

## ✅ Passo 2: Tornar a Planilha Pública

### 2.1. Compartilhar a Planilha

1. Na planilha, clique no botão **"Compartilhar"** (canto superior direito)
   
2. Na janela que abrir, clique em **"Alterar"** (ao lado de "Restrito")

3. Selecione: **"Qualquer pessoa com o link"**

4. No menu suspenso de permissões, selecione: **"Visualizador"**

5. Clique em **"Concluído"**

### 2.2. Copiar o ID da Planilha

1. Olhe para a URL (barra de endereço) da planilha:
   ```
   https://docs.google.com/spreadsheets/d/1LKqPJw1K5jA1e2HK1te-gUAbXlRQX5fwWcKqC4g-MEg/edit
   ```

2. Copie APENAS a parte entre `/d/` e `/edit`:
   ```
   1LKqPJw1K5jA1e2HK1te-gUAbXlRQX5fwWcKqC4g-MEg  ← Este é o ID!
   ```

3. **Guarde este ID!** Você vai precisar dele no próximo passo.

---

## ✅ Passo 3: Configurar o Script Python

### 3.1. Instalar Python (se ainda não tiver)

**Windows:**
1. Baixe em: https://www.python.org/downloads/
2. **IMPORTANTE:** Marque a opção "Add Python to PATH" durante a instalação!
3. Instale normalmente

**Mac/Linux:**
- Geralmente já vem instalado
- Para verificar, abra o Terminal e digite: `python3 --version`

### 3.2. Instalar a Biblioteca gspread

Abra o **Terminal** (Mac/Linux) ou **Prompt de Comando** (Windows) e digite:

```bash
pip install gspread
```

Ou se der erro, tente:

```bash
pip3 install gspread
```

### 3.3. Editar o Script

1. Abra o arquivo **`atualizar_blog_simples.py`** em um editor de texto
   - Pode usar Bloco de Notas, VS Code, Sublime, etc.

2. Encontre esta linha (deve estar perto do início):
   ```python
   PLANILHA_ID = "COLE_O_ID_DA_SUA_PLANILHA_AQUI"
   ```

3. Substitua por:
   ```python
   PLANILHA_ID = "1LKqPJw1K5jA1e2HK1te-gUAbXlRQX5fwWcKqC4g-MEg"  # Cole seu ID aqui!
   ```

4. **Salve o arquivo**

---

## ✅ Passo 4: Testar o Script

### 4.1. Rodar o Script

No Terminal/Prompt, navegue até a pasta onde está o script:

```bash
cd caminho/para/a/pasta
```

Execute o script:

```bash
python atualizar_blog_simples.py
```

Ou:

```bash
python3 atualizar_blog_simples.py
```

### 4.2. O Que Deve Acontecer

Você verá algo assim:

```
======================================================================
🌐 LinguaCulturaX - Atualizador de Blog (Versão Simplificada)
======================================================================

🔗 Conectando à planilha pública...
✅ Conexão estabelecida!
📥 Buscando posts da aba 'Posts'...
✅ 2 posts encontrados na planilha

🔄 Convertendo posts para o formato do blog...
✅ 2 posts convertidos com sucesso

💾 Gerando arquivo blog.js...
✅ Arquivo 'blog.js' gerado com sucesso!
📊 Total de 2 posts incluídos

======================================================================
✨ SUCESSO! Blog atualizado com sucesso!
======================================================================

📝 Próximos passos:
   1. Copie o arquivo 'blog.js' para a pasta do seu site
   2. Faça o upload para o servidor ou commit no Git
   3. Pronto! O blog está atualizado 🎉
```

---

## ✅ Passo 5: Atualizar o Site

### 5.1. Copiar o Arquivo Gerado

O script criou um arquivo chamado `blog.js` na mesma pasta.

### 5.2. Substituir no Site

Copie este arquivo `blog.js` para a pasta do seu site, substituindo o antigo.

### 5.3. Fazer Upload

**Se usa FTP/Hospedagem:**
- Faça upload do `blog.js` para o servidor

**Se usa Git/GitHub:**
```bash
git add blog.js
git commit -m "Atualização do blog"
git push
```

---

## 🔄 Quando Adicionar Novos Posts (SEMPRE)

### Para a Cliente:

1. **Abrir a planilha**
2. **Ir para a última linha vazia**
3. **Preencher:** ID, Título, Data, Autor, Resumo, Conteúdo, Slug
4. **Salvar** (automático)
5. **Avisar você**

### Para Você:

1. **Rodar o script:** `python atualizar_blog_simples.py`
2. **Copiar** o `blog.js` gerado
3. **Fazer upload** para o site
4. **Pronto!** ✅

---

## ❓ Problemas Comuns

### Erro: "planilha não encontrada"

**Solução:**
- Verifique se o ID está correto no script
- Confirme que a planilha está PÚBLICA (compartilhada com "Qualquer pessoa com o link")

### Erro: "aba Posts não encontrada"

**Solução:**
- A aba precisa se chamar exatamente **"Posts"** (com P maiúsculo)
- Ou edite a linha `ABA_NOME = "Posts"` no script

### Erro: "pip não é reconhecido"

**Solução:**
- Reinstale o Python e marque "Add to PATH"
- Ou use: `python -m pip install gspread`

### Posts não aparecem no site

**Solução:**
- Limpe o cache do navegador (Ctrl+Shift+R)
- Verifique se copiou o `blog.js` para a pasta certa
- Abra o console do navegador (F12) e veja se há erros

---

## 📞 Precisa de Ajuda?

Se algo não funcionar, verifique:

1. ✅ ID da planilha está correto?
2. ✅ Planilha está pública?
3. ✅ Biblioteca gspread instalada? (`pip install gspread`)
4. ✅ Colunas nomeadas corretamente?
5. ✅ Aba se chama "Posts"?

---

## 🎉 Tudo Pronto!

Agora você tem um sistema simples e funcional para atualizar o blog! 🚀

**Resumo do Workflow:**
1. Cliente adiciona post na planilha → avisa você
2. Você roda `python atualizar_blog_simples.py`
3. Faz upload do `blog.js`
4. Blog atualizado! ✨

---

**Última atualização:** 02/02/2026