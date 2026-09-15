# Nutri Deividi S.F. — Landing Page VSL

Página de captura com vídeo de apresentação e CTA direto para WhatsApp.

---

## Estrutura de arquivos

```
/
├── index.html          ← página principal (edite aqui)
├── robots.txt          ← permissões para crawlers e LLMs
├── sitemap.xml         ← mapa do site para indexação
├── CNAME               ← domínio personalizado (GitHub Pages)
├── _config.yml         ← configuração GitHub Pages
├── README.md           ← este arquivo
└── assets/
    ├── logo.png        ← sua logomarca (PNG transparente, ~200px altura)
    └── video/          ← pasta reservada (vídeo hospedado no YouTube)
```

---

## Como publicar no GitHub Pages

1. Crie um repositório no GitHub (pode ser privado ou público)
2. Faça upload de todos os arquivos para a branch `main`
3. Vá em **Settings → Pages**
4. Em *Source*, selecione **Deploy from a branch → main → / (root)**
5. Clique em **Save**

O site estará disponível em `https://seu-usuario.github.io/nome-do-repo/` em alguns minutos.

---

## Configurar domínio personalizado

### No GitHub
1. Em **Settings → Pages → Custom domain**, digite seu domínio (ex: `samplafit.com.br`)
2. Marque **Enforce HTTPS**
3. O arquivo `CNAME` já está configurado — atualize o conteúdo com seu domínio real

### No seu registrador de domínio (GoDaddy, Registro.br, Hostinger etc.)
Crie os seguintes registros DNS:

**Registros A** (aponte o domínio raiz para o GitHub):
```
A  @  185.199.108.153
A  @  185.199.109.153
A  @  185.199.110.153
A  @  185.199.111.153
```

**Registro CNAME** (para o subdomínio www):
```
CNAME  www  seu-usuario.github.io
```

A propagação leva entre 10 minutos e 48 horas.

---

## Após publicar — ajustes obrigatórios

### 1. Atualizar o domínio nos arquivos
Substitua `seu-dominio.com.br` pelo seu domínio real em:
- `index.html` → tag `<link rel="canonical">` e bloco Schema.org
- `sitemap.xml` → tag `<loc>`
- `robots.txt` → linha `Sitemap:`
- `CNAME` → o próprio conteúdo do arquivo

### 2. Adicionar a logomarca
Coloque o arquivo `logo.png` na pasta `assets/`.
- Formato: PNG com fundo transparente
- Versão recomendada: branca ou dourada
- Altura mínima: 96px (será exibida em 48px)

### 3. Configurar o vídeo
No `index.html`, localize o bloco de configuração no `<script>`:

```js
const VIDEO_ID         = 'iqmBkYXhDzE'; // ← ID do seu YouTube Short
const VIDEO_DURATION_S = 102;            // ← duração em segundos
const TRIGGER_AT       = 0.30;           // ← CTA aparece aos 30% do vídeo
```

O ID do Shorts fica no final da URL:
`youtube.com/shorts/`**`iqmBkYXhDzE`**

---

## SEO e LLMs

O `robots.txt` já libera os principais crawlers de IA (GPTBot, ClaudeBot, PerplexityBot etc.).
O Schema.org no `<head>` do `index.html` descreve você, seu serviço e um FAQ — isso alimenta
tanto o Google quanto respostas de LLMs sobre seu nome e especialidade.

Após publicar, submeta o sitemap no **Google Search Console**:
`https://seu-dominio.com.br/sitemap.xml`
