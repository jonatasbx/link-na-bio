🔗 Link na Bio

Página de perfil pessoal no estilo "link na bio": reúne em um só lugar meus principais links (GitHub, LinkedIn, portfólio...) e permite alternar entre tema escuro e claro.

Projeto de estudo feito com HTML, CSS e JavaScript puro, sem frameworks, seguindo um fluxo de trabalho profissional: escopo, modelo de dados, design, branches, Pull Requests e deploy.

Status: 🚧 em desenvolvimento (Etapa 2 de 6: modelo de dados e design)

🎯 Problema e usuário
Problema: redes sociais permitem só um link no perfil, e quem quer me conhecer precisa procurar meus perfis em vários lugares.
Usuário: recrutadores, colegas de curso e pessoas que encontram meu perfil nas redes.
📖 Histórias de usuário
Como visitante, quero ver meu nome, foto e uma bio curta para saber quem eu sou.
Como visitante, quero clicar em botões grandes para abrir meus links com facilidade no celular.
Como visitante, quero alternar entre tema escuro e claro para ler com conforto.
📦 Escopo do MVP
Dentro ✅	Fora ❌ (versões futuras)
Foto, nome e bio	Painel para editar os links
Lista de links vinda de um arquivo de dados	Contador de cliques
Alternância de tema escuro/claro	Back-end ou banco de dados
Layout responsivo (mobile first)	Múltiplos idiomas
Deploy no GitHub Pages
🗂️ Modelo de dados

Os dados ficam separados da interface, em js/dados.js. Para adicionar ou trocar um link, basta editar esse arquivo.

perfil (objeto)
├─ nome      : texto
├─ bio       : texto
├─ foto      : texto (caminho da imagem)
├─ fotoAlt   : texto (descrição da foto para leitores de tela)
└─ links     : array de objetos
     └─ { titulo, url, icone }

Exemplo em JSON:

json
{
  "nome": "Jonatas Xavier",
  "bio": "Estudante de ADS aprendendo JavaScript",
  "foto": "img/avatar.jpg",
  "fotoAlt": "Foto de Jonatas Xavier",
  "links": [
    { "titulo": "GitHub", "url": "https://github.com/...", "icone": "github" },
    { "titulo": "LinkedIn", "url": "https://linkedin.com/in/...", "icone": "linkedin" }
  ]
}
🎨 Design

As decisões visuais estão em variáveis CSS (design tokens) no arquivo css/tokens.css. O tema escuro é o padrão (:root). O tema claro é ativado com o atributo data-theme="light" no <html>, que troca só os valores das cores.

Paleta criada com o Realtime Colors. Contraste verificado no WebAIM Contrast Checker.

Cores
Token	Uso	Escuro (padrão)	Claro
--text	Texto principal
#eae9fc
#040316
--background	Fundo da página
#010104
#fbfbfe
--primary	Botões dos links
#27912f
#1e6f24
--text-on-primary	Texto dentro dos botões
#010104
#fbfbfe
--secondary	Bordas, ícones, foco
#5a53df
#2720ac
--accent	Detalhes decorativos
#565298
#6b67ad
Contraste (WCAG 2)

Mínimos: 4.5:1 para texto normal e 3:1 para texto grande, ícones e bordas.

Combinação	Escuro	Claro	Resultado
--text sobre --background	17.4:1	19.7:1	✅ AA/AAA
--text-on-primary sobre --primary	5.1:1	6.1:1	✅ AA
--primary sobre --background	5.1:1	6.1:1	✅ AA
--secondary sobre --background	3.7:1	10.8:1	⚠️ no escuro, usar só em bordas/ícones
--accent sobre --background	3.0:1	4.9:1	⚠️ no escuro, usar só em detalhes decorativos

Decisão: no tema escuro, texto claro sobre o verde --primary ficava em 3.4:1 e reprovava. Por isso foi criado o token --text-on-primary com texto escuro.

Tipografia
Fonte: pilha de fontes do sistema (system-ui, -apple-system, "Segoe UI", Roboto, sans-serif). Carrega na hora e não depende de serviço externo.
Tamanhos: --text-sm 14px · --text-base 16px · --text-lg 20px · --text-xl 28px
Espaçamentos

--space-1 8px · --space-2 16px · --space-3 24px · --space-4 32px · --radius 12px

🛠️ Tecnologias
HTML5 semântico
CSS3 (variáveis CSS, Flexbox/Grid)
JavaScript puro (vanilla)
Git + GitHub Desktop
GitHub Pages (deploy)
📁 Estrutura atual
link-na-bio/
├── index.html          ← única página; a "porta de entrada"
├── README.md
├── .gitignore
├── css/
│   ├── tokens.css      ← (Etapa 2) cores, fontes, espaçamentos
│   └── estilos.css     ← (Etapa 4) layout e componentes
├── js/
│   ├── dados.js        ← (Etapa 2) perfil + links
│   ├── interface.js    ← (Etapa 5) funções que montam o HTML
│   └── app.js          ← (Etapa 5) ponto de partida + tema claro/escuro
└── img/
    └── avatar.jpg      ← sua foto (ou uma imagem qualquer por enquanto)
▶️ Como executar
Clone o repositório pelo GitHub Desktop (File → Clone repository).
Abra o arquivo index.html no navegador.

Não há instalação nem dependências.

🗺️ Etapas do projeto
 1. Ideia, escopo e repositório
 2. Modelo de dados e design
 3. Arquitetura e estrutura (Pull Request e merge)
 4. CSS e layout responsivo
 5. JavaScript: renderizar os links e alternar o tema
 6. Revisão, deploy no GitHub Pages e release v1.0.0
👤 Autor

Jonatas Xavier, estudante de Análise e Desenvolvimento de Sistemas.
