# Casa Rosa — site institucional

Site institucional da Casa Rosa, publicado em [casarosasp.com.br](https://casarosasp.com.br).

## Origem

Export do ChatGPT Sites em 22/10/2026 (`Casa_Rosa_site_export_portatil.zip`). O inventário original do export está em `docs/INVENTARIO-export-chatgpt.md`.

## Estrutura

- `site/` — é o que vai publicado. Site estático, sem build: `index.html` + `assets/`.
  - `site/assets/_nao-usados/` — arquivos do export que o `index.html` não referencia.
- `docs/` — documentação interna. Não é publicada.
  - `docs/originais/` — imagens e fontes em resolução original (PNG/JPEG/TTF). O site publica versões otimizadas (WebP/WOFF2) geradas a partir delas; para trocar uma imagem, edite o original e gere o WebP de novo.

## Convenções

- Imagens: WebP, largura máxima ~2× o tamanho exibido, sempre com `width`/`height` no `<img>` e `loading="lazy"` abaixo da primeira dobra.
- Fontes: WOFF2 locais (licença OFL em `site/assets/fonts/`).
- `site/.htaccess`: redireciona www → sem www, compressão e cache (HTML revalida sempre; imagens 30 dias; fontes 1 ano).
- SEO/compartilhamento: `og-image.jpg` (1200×630), favicons, `robots.txt`, `sitemap.xml` e dados estruturados (LocalBusiness) no `<head>`.

- Analytics: Umami Cloud (sem cookies, sem banner LGPD), só conta visitas em `casarosasp.com.br` (`data-domains`). Cliques são contados por `data-umami-event` nos links: `whatsapp-grade`, `whatsapp-oficina`, `whatsapp-mindfulness`, `whatsapp-contato`, `whatsapp-rodape`, `instagram-contato`, `instagram-rodape`. Link novo de WhatsApp ou Instagram deve levar o atributo.

## Testar localmente

```sh
python3 -m http.server --directory site
```

Abra http://localhost:8000.

## Publicação

Publicação: Hostinger. Todo push na main que altera site/ dispara a Action deploy-hostinger, que envia o conteúdo de site/ por FTP para o public_html. Secrets necessários: FTP_SERVER, FTP_USERNAME, FTP_PASSWORD; variável: FTP_DIR. Deploy manual: aba Actions → Deploy Hostinger → Run workflow.
