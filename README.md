<div align="center">

# Isabella Anton

**Portfólio pessoal da desenvolvedora Isabella Anton**

<br />

[![Next.js](https://img.shields.io/badge/Next.js_15-111111?style=for-the-badge&logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://vercel.com/)

[**Ver o site ao vivo →**](https://isabellaantondev.vercel.app) 

</div>

<br />

## Sobre

Site de portfólio de **Isabella Anton**, estudante de Ciência da Computação na UNIFOR (Fortaleza, CE).
O design parte de um hero com um **wordmark gigante**, letras coloridas e **pílulas de navegação ligadas às letras por linhas ortogonais**, sobre um fundo escuro com grid de papel milimetrado.

O nome "IA" (Isabella Anton) vira o fio condutor do projeto, de forma discreta: no logo, no favicon, no rodapé e em um pequeno detalhe interativo no hero.

## Destaques

| | |
|---|---|
| **Quatro idiomas** | Português, inglês, francês e alemão, com rotas `/pt`, `/en`, `/fr` e `/de` e detecção automática pelo idioma do navegador. |
| **Hero interativo** | As letras caem na entrada, as linhas das pílulas se traçam e reagem ao passar o mouse (a letra pula e brilha). |
| **Dock de personalização** | Paleta, fonte, espaçamento, raio das bordas e intensidade do brilho, em tempo real. As escolhas ficam salvas no navegador. |
| **Modo debug** | Tecla `D` (ou botão no dock) mostra as caixas de layout e as linhas conectoras, como no DevTools. |
| **Grid que reage ao mouse** | O fundo ganha brilho ao redor do cursor. |
| **Currículo em PDF** | Botão de download na navbar, no hero, em Sobre e em Contato. |
| **Acessível** | HTML semântico, foco visível, navegação por teclado, link "pular para o conteúdo" e `prefers-reduced-motion` respeitado. |
| **Leve e rápido** | Páginas estáticas, fontes hospedadas no próprio site e animações em CSS puro. |
| **SEO pronto** | Metadados por idioma, `hreflang`, Open Graph, sitemap, robots, favicon e JSON-LD. |

## O jogo com o "IA"

Ao passar o mouse (ou tocar) no **"i"** ou no **"a"** grandes do wordmark, ou no botão abaixo da frase, o significado muda:

`Isabella Anton` → `Interfaces Acessíveis` → `Inovação Aplicada` → `Imaginação Aplicada` → `Impacto Social` → `Inteligência Aplicada`

Para editar a lista, mude `hero.ia` em `content/content.ts`.

## Stack

- **[Next.js 15](https://nextjs.org/)** (App Router) e **React 19**
- **TypeScript**
- **Tailwind CSS 3**
- **[Fontsource](https://fontsource.org/)**: Outfit, Space Grotesk e JetBrains Mono, hospedadas no próprio projeto
- **Vercel** para hospedagem

## Rodando localmente

Requisitos: **Node.js 20 ou superior**.

```bash
# 1. Instale as dependências
npm install

# 2. Rode em modo de desenvolvimento
npm run dev
```

Abra [http://localhost:3000](http://localhost:3000). A raiz redireciona para `/pt`, `/en`, `/fr` ou `/de`.

Outros comandos:

```bash
npm run typecheck   # checa os tipos
npm run build       # build de produção
npm start           # serve o build de produção
```

## Editando o conteúdo

Todo o conteúdo do site (textos, projetos, habilidades, links, artigos) fica em **um único arquivo**:

```
content/content.ts
```

Os textos são escritos nos quatro idiomas de uma vez com a função `t()`:

```ts
desc: t(
  'Texto em português',
  'Text in English',
  'Texte en français',
  'Text auf Deutsch',
),
```

Itens que ainda precisam de dados estão marcados com `[TODO]`.

### Adicionar um projeto

Acrescente um objeto em `projectItems`, em `content/content.ts`:

```ts
{
  name: 'Meu Projeto',
  meta: t('Categoria', 'Category', 'Catégorie', 'Kategorie'),
  desc: t('...', '...', '...', '...'),
  tags: ['React', 'TypeScript'],
  demo: 'https://meu-projeto.vercel.app/', // '' se não houver
  repo: 'https://github.com/usuario/repo',  // '' se não houver
  press: '',                               // link de matéria, se houver
  awards: [],                              // prêmios (opcional)
  color: 1,                                // 1 a 5, cor da paleta
},
```

### Currículo

1. Coloque o PDF na pasta `public/`, por exemplo `public/Curriculo_Isabella_Anton.pdf`.
2. Em `content/content.ts`, ajuste `resume.href` para `/Curriculo_Isabella_Anton.pdf`.

### Domínio do site

Troque `site.url` em `content/content.ts` pelo endereço final. Ele é usado no sitemap, no `robots.txt` e nos metadados de compartilhamento.

## Estrutura

```
.
├── app/
│   ├── [lang]/page.tsx        # página única, gerada para cada idioma
│   ├── layout.tsx             # html, metadados base e fundo
│   ├── globals.css            # tokens, grid, animações e modo debug
│   ├── not-found.tsx          # página 404
│   ├── opengraph-image.tsx    # imagem de compartilhamento
│   ├── icon.svg               # favicon
│   ├── robots.ts
│   └── sitemap.ts
├── components/
│   ├── Hero.tsx               # wordmark, pílulas e linhas conectoras
│   ├── Navbar.tsx
│   ├── Sections.tsx           # projetos, habilidades, sobre e contato
│   ├── Dock.tsx               # personalização em tempo real
│   ├── LocalTime.tsx          # cidade e hora local
│   ├── ResumeButton.tsx
│   └── ...
├── content/
│   ├── content.ts             # todo o conteúdo do site
│   └── i18n.ts                # idiomas e utilitários de tradução
├── lib/util.ts
├── middleware.ts              # "/" → idioma do navegador
├── public/                    # arquivos estáticos (currículo em PDF)
└── next.config.mjs
```

## Deploy na Vercel

1. Suba o projeto para um repositório no GitHub.
2. Na [Vercel](https://vercel.com), clique em **Add New → Project** e importe o repositório.
3. Confirme que o **Framework Preset** é **Next.js** (a detecção é automática) e clique em **Deploy**.

A cada `git push` para a branch `main`, o site é atualizado sozinho.

## Personalização visual

O dock flutuante na parte de baixo da tela altera o site em tempo real:

| Ícone | O que muda | Opções |
|---|---|---|
| Paleta | Cores das letras e dos projetos | default, neon, pastel, mono |
| Fonte | Tipografia do site | Outfit, Space Grotesk, JetBrains Mono |
| Espaçamento | Respiros entre seções | compact, normal, airy |
| Raio | Cantos dos cards | sharp, normal, round |
| Brilho | Intensidade dos glows | off, soft, strong |
| Terminal | Modo debug | ligado ou desligado (tecla `D`) |

As escolhas ficam salvas no `localStorage` do navegador.

---

<div align="center">

Projetado e desenvolvido por **Isabella Anton**
Fortaleza, CE · [GitHub](https://github.com/isabellaanton) · [LinkedIn](https://linkedin.com/in/isabella-anton) · [E-mail](mailto:isabellaanton3@gmail.com)

</div>
