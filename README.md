Pitiquinhos — arquivos para colocar no ar
Este pacote contém o app pronto para publicar, como um PWA (app
instalável) com sincronização entre aparelhos via Firebase. Não
precisa de build (React e Firebase são carregados via CDN).
Arquivos
`index.html` — o app inteiro (interface, estilos e lógica)
`manifest.webmanifest` — metadados que permitem instalar o app
`sw.js` — service worker (funciona offline e é exigido para instalar)
`icon-192.png` / `icon-512.png` — ícones do app instalado
Importante: publique a pasta inteira, não só o `index.html` — os outros
arquivos são necessários pra instalação e a sincronização funcionarem.
Como a sincronização entre aparelhos funciona
Na primeira vez que o app abre em um aparelho, ele pede pra você:
Criar código novo — gera um código único (ex: `M5YXGRS5`) e cria uma
"casa" nova no banco de dados. Anote esse código.
Entrar com um código — se você já criou uma casa em outro aparelho,
digite o mesmo código aqui pra ver os mesmos dados.
Depois da primeira vez, o aparelho lembra o código sozinho — não precisa
digitar de novo. O código aparece no rodapé do app ("Sincronizado ·
CÓDIGO"), com uma opção de trocar/desconectar se precisar.
Os dados ficam salvos no Firestore (banco de dados do Firebase) e também
em cache local no aparelho, então o app continua funcionando offline —
qualquer alteração feita sem internet é enviada assim que a conexão
voltar.
Sobre segurança: não há login/senha — o código de sincronização
funciona como uma chave de acesso. Qualquer pessoa que souber o código
consegue ver e editar os dados daquela casa. Para um app de uso
doméstico/familiar isso é razoável, mas evite compartilhar o código
publicamente.
Como camada extra de segurança, o app também tem um card "Backup dos
dados" no rodapé (baixar/importar um arquivo `.json` com tudo).
Publicando no GitHub Pages
Crie um repositório no GitHub e suba todos os arquivos desta pasta
No repositório, vá em Settings → Pages
Em "Source", escolha a branch `main` e a pasta raiz (`/`)
Salve — em alguns minutos o link fica disponível em algo como
`https://seu-usuario.github.io/nome-do-repo`
Publicando na Vercel (via GitHub)
Suba o repositório para o GitHub (veja acima)
Em vercel.com → Add New → Project → Import Git Repository
Selecione o repositório e clique em Deploy — não precisa configurar
nada, é um site estático
Alternativa rápida (sem GitHub)
Arraste a pasta inteira em https://app.netlify.com/drop e você recebe um
link na hora.
Instalando o app (depois de publicado)
Isso só funciona depois que o app estiver no ar em um endereço `https://`
(não funciona abrindo o `index.html` direto do computador):
Celular (Android/Chrome): abra o link, toque no menu (⋮) e escolha
"Instalar app" ou "Adicionar à tela inicial"
iPhone (Safari): abra o link, toque no ícone de compartilhar e
escolha "Adicionar à Tela de Início"
Computador (Chrome/Edge): abra o link e clique no ícone de instalar
que aparece do lado direito da barra de endereço
Depois de instalado, o app abre em janela própria, com ícone na tela
inicial/área de trabalho, como um aplicativo normal. Ao instalar em um
novo aparelho, use o código de sincronização pra ver os mesmos dados.
Testando localmente
Abrir o `index.html` direto do computador (duplo clique) não funciona
para a sincronização, porque o Firebase exige um endereço `http://` ou
`https://` de verdade (não `file://`). Pra testar localmente, rode um
servidor simples na pasta, por exemplo `python3 -m http.server` e acesse
`http://localhost:8000`.
