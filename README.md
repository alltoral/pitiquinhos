# Pitiquinhos — arquivos para colocar no ar

Este pacote contém o app pronto para publicar, agora como um **PWA (app
instalável)**. Não precisa de build (o React é carregado via CDN) e não
precisa de backend nem de chaves de API.

## Arquivos

- `index.html` — o app inteiro (interface, estilos e lógica)
- `manifest.webmanifest` — metadados que permitem instalar o app
- `sw.js` — service worker (funciona offline e é exigido para instalar)
- `icon-192.png` / `icon-512.png` — ícones do app instalado

**Importante:** publique a pasta inteira, não só o `index.html` — os outros
arquivos são necessários pra instalação funcionar.

## Como os dados são salvos

O app usa o `localStorage` do navegador — os dados ficam salvos no aparelho
de quem estiver usando, sem precisar de banco de dados, e **não são
apagados ao fechar o navegador, reiniciar o aparelho ou "sair da conta"**.
Eles só somem se alguém limpar os dados do site manualmente no navegador.

Como camada extra de segurança, o app agora tem um card **"Backup dos
dados"** no final da tela (em qualquer aba), com dois botões:

- **Baixar backup** — gera um arquivo `.json` com tudo (cão, gato,
  estoques, calendário). Baixe de vez em quando, ou antes de trocar de
  aparelho/navegador.
- **Importar backup** — escolha um arquivo de backup baixado antes pra
  restaurar todos os dados.

## Publicando no GitHub Pages

1. Crie um repositório no GitHub e suba **todos os arquivos desta pasta**
2. No repositório, vá em **Settings → Pages**
3. Em "Source", escolha a branch `main` e a pasta raiz (`/`)
4. Salve — em alguns minutos o link fica disponível em algo como
   `https://seu-usuario.github.io/nome-do-repo`

## Publicando na Vercel (via GitHub)

1. Suba o repositório para o GitHub (veja acima)
2. Em vercel.com → **Add New → Project → Import Git Repository**
3. Selecione o repositório e clique em **Deploy** — não precisa configurar
   nada, é um site estático

## Alternativa rápida (sem GitHub)

Arraste a pasta inteira em https://app.netlify.com/drop e você recebe um
link na hora.

## Instalando o app (depois de publicado)

Isso só funciona depois que o app estiver no ar em um endereço `https://`
(não funciona abrindo o `index.html` direto do computador):

- **Celular (Android/Chrome):** abra o link, toque no menu (⋮) e escolha
  "Instalar app" ou "Adicionar à tela inicial"
- **iPhone (Safari):** abra o link, toque no ícone de compartilhar e
  escolha "Adicionar à Tela de Início"
- **Computador (Chrome/Edge):** abra o link e clique no ícone de instalar
  que aparece do lado direito da barra de endereço

Depois de instalado, o app abre em janela própria, com ícone na tela
inicial/área de trabalho, como um aplicativo normal.

## Testando localmente

Basta abrir o `index.html` clicando duas vezes nele — funciona offline,
mas a instalação como app (PWA) só fica disponível depois de publicado em
um endereço `https://` de verdade.
