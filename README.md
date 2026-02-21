# Labchain - Website

Site institucional do Laboratório de Pesquisa em Blockchain e suas Aplicações da Universidade Estadual do Ceará (UECE).

## 🚀 Tecnologias

- React + Vite
- React Router (HashRouter para GitHub Pages)
- CSS puro com variáveis CSS
- Sistema de i18n customizado (PT/EN)

## 📦 Instalação e Execução

```bash
cd site
npm install
npm run dev      # Desenvolvimento em http://localhost:5173
npm run build    # Build para produção
```

## 🌐 Deploy

O site está configurado para deploy automático no GitHub Pages via GitHub Actions. Ao fazer push para `main`, o workflow `.github/workflows/deploy.yml` faz build e deploy automaticamente.

**URL de produção:** https://labchain-uece.github.io

## 📝 Como Adicionar Conteúdo

### 1. Adicionar Membro

Edite `site/src/data/members.js`:

```js
{
  id: 5,
  name: 'Nome do Membro',
  role: 'researcher', // 'coordinator', 'researcher', ou 'collaborator'
  photo: '/images/members/nome.jpg', // Adicione a foto em site/public/images/members/
  lattes: 'http://lattes.cnpq.br/ID',
  interests: {
    pt: ['Interesse 1', 'Interesse 2'],
    en: ['Interest 1', 'Interest 2']
  }
}
```

### 2. Adicionar Publicação

Edite `site/src/data/publications.js`:

```js
{
  year: 2026,
  papers: [
    {
      title: 'Título do Paper',
      authors: 'Autor1, A.; Autor2, B.; Autor3, C.',
      venue: 'Nome da Conferência/Journal, v. X, p. Y-Z, 2026.',
      preprint: '/images/papers/2026/nome-preprint.pdf', // ou null se não tiver
      publisherUrl: 'https://doi.org/...', // ou '#' se não tiver
      slides: '/images/papers/2026/nome-slides.pdf', // ou null se não tiver
      video: 'https://youtube.com/...', // ou null se não tiver (link externo)
      award: null, // ou 'Nome do Prêmio' se tiver
    }
  ]
}
```

**Importante:**
- PDFs de preprints devem estar em `site/public/images/papers/ANO/arquivo.pdf`
- Se `preprint` ou `publisherUrl` for `null` ou `'#'`, o botão não aparecerá

### 3. Adicionar Atividade/Notícia

Edite `site/src/data/news.js`:

```js
{
  id: 5,
  date: '2026-03-15', // Formato ISO: YYYY-MM-DD
  tag: 'evento', // 'evento', 'premiacao', ou 'publicacao'
  title: {
    pt: 'Título em Português',
    en: 'Title in English'
  },
  description: {
    pt: 'Descrição em português...',
    en: 'Description in English...'
  },
  photos: [
    '/images/news/evento-0.jpg',
    '/images/news/evento-1.jpg',
  ] // Adicione as fotos em site/public/images/news/
}
```

**Tags disponíveis:**
- `evento`: Participação em eventos (mostra botão "Ver Momentos")
- `premiacao`: Prêmios recebidos (mostra botão "Ver Momentos")
- `publicacao`: Novas publicações (não mostra botão)

### 4. Adicionar Projeto

Edite `site/src/data/projects.js`:

```js
{
  id: 5,
  name: 'Nome do Projeto', // ou { pt: 'Nome PT', en: 'Name EN' }
  description: {
    pt: 'Descrição em português...',
    en: 'Description in English...'
  },
  image: '/images/projects/projeto.png', // Adicione em site/public/images/projects/
  url: 'https://url-do-projeto.com' // ou '#' se não tiver (botão não aparecerá)
}
```

### 5. Editar Textos da Interface

Edite `site/src/i18n/translations.js`:

```js
export const translations = {
  pt: {
    about_text: 'Novo texto em português...',
    // ...
  },
  en: {
    about_text: 'New text in English...',
    // ...
  }
}
```

**Principais seções:**
- `hero_*`: Hero da home
- `about_*`: Seção "Quem Somos"
- `rl_*`: Linhas de pesquisa (rl_1 a rl_8)
- `contact_*`: Página de contato
- `members_*`, `research_*`, `activities_*`, `projects_*`: Seções específicas

## 📁 Estrutura de Arquivos

```
site/
├── public/
│   ├── images/
│   │   ├── members/         # Fotos dos membros
│   │   ├── news/           # Fotos das atividades
│   │   ├── papers/         # PDFs dos preprints (por ano)
│   │   ├── projects/       # Imagens dos projetos
│   │   ├── uece-logo.png
│   │   └── ppgcc-logo.jpg
│   └── logo.png
├── src/
│   ├── components/         # Navbar, Footer, PhotoModal
│   ├── data/              # Dados (members, publications, news, projects)
│   ├── i18n/              # Sistema de tradução
│   ├── pages/             # Páginas (Home, Research, Members, etc.)
│   ├── utils.js           # assetUrl() para GitHub Pages
│   └── main.jsx           # Entry point
└── vite.config.js         # Config com base: '/labchain-website/'
```

## 🎨 Paleta de Cores

```css
--blue-primary: #319dd8
--blue-dark: #2563a6
--purple-primary: #7663cf
--purple-dark: #5a4aa0
--gray-dark: #2d2d2d
```

## ⚠️ Observações Importantes

1. **Imagens:** Sempre adicione imagens em `site/public/images/` (não em `src/assets/`)
2. **GitHub Pages:** O site usa HashRouter (`#/`) para funcionar corretamente no GitHub Pages
3. **Base Path:** Todos os assets locais usam `assetUrl()` para funcionar com o base path `/labchain-website/`
4. **Datas:** Use formato ISO `YYYY-MM-DD` em news.js - serão formatadas automaticamente
5. **Links vazios:** Use `null` ou `'#'` para links inexistentes - os botões não aparecerão

## 📞 Contato

- **Email:** jerffeson.souza@uece.br
- **Localização:** Sala 16, NC2A Térreo — UECE, Fortaleza - CE, Brasil
