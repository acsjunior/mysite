# CLAUDE.md

Site pessoal/currículo de António Júnior (https://antoniojunior.me), feito com **Hugo** + **Hugo Blox Builder** (starter `academic-cv`, módulo `blox-tailwind` v0.3.2). Não há código de aplicação: o site é todo configuração YAML, Markdown com front matter e alguns overrides de templates Hugo.

## Comandos

```bash
hugo server            # dev local em http://localhost:1313 (PT em /, EN em /en/)
hugo --gc --minify     # build de produção em public/
npx pagefind --site public   # índice de busca (a busca da navbar depende dele)
```

- Versão de Hugo fixada em **0.136.5 extended** (`hugoblox.yaml`, `netlify.toml`, `.github/workflows/publish.yaml`). A máquina local pode ter versão mais nova (ex.: 0.148); se o build quebrar, suspeite primeiro da diferença de versão.
- Os módulos Hugo estão **vendorizados** em `_vendor/` (Hugo usa essa pasta em vez de baixar pelo `go.mod`). Para atualizar módulos: `hugo mod get -u` e depois `hugo mod vendor`. Não edite arquivos dentro de `_vendor/` — para customizar, copie o template para `layouts/` (veja abaixo).
- Não há testes nem lint; "verificar" = rodar `hugo server` e olhar as páginas PT e EN.

## Deploy

- Push em `main` dispara `.github/workflows/publish.yaml` (build Hugo + Pagefind → GitHub Pages).
- Também existe `netlify.toml` (build equivalente para Netlify). O domínio de produção está em `baseURL` de `config/_default/hugo.yaml`.
- `public/`, `resources/_gen/` e `hugo_stats.json` estão versionados (não há `.gitignore`), então um build local altera muitos arquivos nessas pastas. Ao commitar mudanças de conteúdo/config, mantenha-as separadas de ruído de build quando possível, e não commite `.DS_Store`.
- `.github/workflows/import-publications.yml` (importa `publications.bib`) e `updater-wip.yml` são resquícios do template e na prática não rodam.

## Estrutura

```
config/_default/
  hugo.yaml       # título, baseURL, idioma padrão (pt), taxonomias, permalinks
  languages.yaml  # pt (padrão, content/) e en (content/en/, menu próprio)
  menus.yaml      # menu principal em português
  params.yaml     # aparência, navbar (logo1.png), footer, SEO, custom_css
  module.yaml     # imports dos módulos HugoBlox e mounts
content/          # conteúdo em PORTUGUÊS (idioma padrão, sem subpasta)
  _index.md       # home: blocos resume-biography-3 + markdown "Resumo Profissional" (id: bio)
  experience.md   # página Experiência & Formação: blocos resume-experience + resume-languages
  authors/admin/_index.md   # PERFIL: nome, cargo, organizações, redes, interesses, education, work, languages
content/en/       # espelho em INGLÊS: _index.md, experience.md, authors/admin/_index.md
static/uploads/cv_acsjunior.pdf        # CV PT (botão "Baixar CV")
static/en/uploads/cv_acsjunior_en.pdf  # CV EN (botão "Download CV")
assets/css/custom.css              # fonte Nunito Sans, cor de fundo da hero (.dark = #115176), avatar 150x150
assets/css/blox/biography.css      # override de CSS do bloco de biografia
assets/media/                      # logo1.png (navbar), icon.png (favicon), ícones SVG extras em icons/
layouts/partials/                  # overrides de templates do HugoBlox (ver abaixo)
```

### Onde mexer para cada tipo de mudança

- **Bio, cargo, experiências, formação, idiomas, redes sociais**: `content/authors/admin/_index.md` (PT) **e** `content/en/authors/admin/_index.md` (EN). Os dados de currículo vêm do perfil do autor, não das páginas.
- **Texto do Resumo Profissional / botão de CV**: `content/_index.md` e `content/en/_index.md`.
- **Itens de menu**: `config/_default/menus.yaml` (PT) e o bloco `menu:` dentro de `en:` em `config/_default/languages.yaml` (EN).
- **Visual**: `assets/css/custom.css` (prefira CSS a mexer em templates). `appearance` em `params.yaml` controla modo claro/escuro e cor do tema.
- **Novo CV em PDF**: substitua os arquivos em `static/uploads/` e `static/en/uploads/` mantendo os nomes.

## Convenções importantes

- **Bilíngue sempre**: toda mudança de conteúdo deve ser feita nas duas versões (PT em `content/`, EN em `content/en/`). Os arquivos EN são cópias traduzidas com a mesma estrutura de front matter — mantenha as duas em sincronia (mesmas chaves, mesma ordem de itens em `work`/`education`).
- O `username` dos blocos (`admin`) aponta para a pasta em `content/authors/`; cada idioma resolve o autor dentro do seu próprio `contentDir`.
- Datas em `work`/`education` no formato `AAAA-MM-DD`; `date_end` vazio/ausente = "atual".
- Ícones de redes usam a sintaxe HugoBlox (`brands/linkedin`, `brands/github`, `academicons/...`); ícones personalizados vão em `assets/media/icons/`.
- Blocos comentados (`papers`, `talks`, `projects`, `teaching` etc.) são do template e estão desativados de propósito. As pastas `content/post`, `project`, `publication`, `event`, `teaching` e `content/projects.md` ainda contêm conteúdo de exemplo do template; elas não aparecem no menu, mas são geradas no build. Não as trate como conteúdo real do autor.
- Mensagens de commit seguem Conventional Commits em português, com escopo: `feat(i18n): ...`, `fix(config): ...`, `chore(cleanup): ...`, `style: ...`.

## Overrides de templates (`layouts/partials/`)

Sobrescrevem arquivos de mesmo caminho em `_vendor/.../blox-tailwind/layouts/partials/`. Ao atualizar o módulo, compare com a versão nova do vendor.

- `blox/resume-biography-3.html`: hero da home (avatar, nome, cargo, organização, redes, botão de CV).
- `blox/resume-experience.html`: página de experiência; usa o título da página como fallback do título da seção.
- `components/headers/navbar.html`: navbar com logo personalizado.
- `site_head.html`, `site_footer.html`, `page_metadata_authors.html`: ajustes no head, rodapé e lista de autores.
- `hooks/head-end/github-button.html`: carrega o script de botões do GitHub.
- `views/article-grid.html`: arquivo vazio (desativa essa view).

## SEO

- Título e descrição em PT: `title` em `hugo.yaml` e `marketing.seo.description` em `params.yaml`.
- Título e descrição em EN: `en.title` e `en.params.marketing.seo.description` em `languages.yaml`. O tema lê `marketing.seo.description`; uma chave `description` solta é ignorada. Ao mudar um idioma, atualize o outro.
- `hugo` também escreve em `hugo_stats.json` e `resources/_gen/` (e `--gc` apaga imagens geradas). Para só validar, gere a saída em outra pasta (`hugo -d /tmp/...`) e desfaça as mudanças nesses arquivos se não forem intencionais.
