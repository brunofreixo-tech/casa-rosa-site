# Casa Rosa — site institucional

Site institucional da Casa Rosa, publicado em [casarosasp.com.br](https://casarosasp.com.br).

## Origem

Export do ChatGPT Sites em 22/10/2026 (`Casa_Rosa_site_export_portatil.zip`). O inventário original do export está em `docs/INVENTARIO-export-chatgpt.md`.

## Estrutura

- `site/` — é o que vai publicado. Site estático, sem build: `index.html` + `assets/`.
  - `site/assets/_nao-usados/` — arquivos do export que o `index.html` não referencia.
- `docs/` — documentação interna. Não é publicada.

## Testar localmente

```sh
python3 -m http.server --directory site
```

Abra http://localhost:8000.

## Publicação

Cloudflare Pages, com diretório de saída `site` e sem comando de build. **Ainda não configurado.**
