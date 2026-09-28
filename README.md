# Aluguel de Mesas e Cadeiras Jundiaí

Site estático (HTML/CSS/JS puro) que serve como guia informativo sobre aluguel de mesas, cadeiras e materiais para festas e eventos em Jundiaí e região, conectando visitantes à plataforma Locaaqui.

## Estrutura

- `index.html` — página principal (guia, busca, FAQ, tabela de preços)
- `contato.html` — página de contato
- `privacidade.html` — política de privacidade (LGPD / cookies / AdSense)
- `assets/` — CSS, JS e webfonts
- `images/` — imagens do site
- `_headers` — cabeçalhos HTTP (segurança e cache) para o Cloudflare Pages
- `_redirects` — regras de redirecionamento do Cloudflare Pages

## Deploy — Cloudflare Pages

O deploy é automático via GitHub Actions (`.github/workflows/cloudflare-pages.yml`) a cada push na branch `main`.

### Secrets necessários no repositório

Configure em **Settings → Secrets and variables → Actions**:

| Secret                  | Descrição                                                        |
| ----------------------- | ---------------------------------------------------------------- |
| `CLOUDFLARE_API_TOKEN`  | Token de API com permissão **Cloudflare Pages: Edit**            |
| `CLOUDFLARE_ACCOUNT_ID` | ID da conta Cloudflare (Dashboard → Workers & Pages → à direita) |

### Criando o token de API

1. Acesse **My Profile → API Tokens → Create Token** no dashboard da Cloudflare.
2. Use o template **Edit Cloudflare Workers** ou crie um custom com a permissão `Account → Cloudflare Pages → Edit`.
3. Copie o token e adicione como secret `CLOUDFLARE_API_TOKEN`.

### Projeto no Cloudflare Pages

O workflow publica no projeto chamado `terrenosavendajundiai`. Na primeira execução, o Wrangler cria o projeto automaticamente caso ele ainda não exista. Depois, associe o domínio `terrenosavendajundiai.com.br` em **Workers & Pages → terrenosavendajundiai → Custom domains**.

## Desenvolvimento local

Por ser um site estático, basta abrir `index.html` no navegador ou servir a pasta com qualquer servidor estático:

```bash
npx serve .
```
