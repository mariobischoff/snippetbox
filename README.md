# Snippetbox

Snippetbox é uma aplicação web para criar, compartilhar e visualizar snippets de texto, inspirada no Pastebin. Desenvolvida em Go, ela utiliza uma arquitetura modular e segue os princípios ensinados no livro *Let's Go* de Alex Edwards, sendo um projeto prático para aprender desenvolvimento web com Go.

## Funcionalidades
- Criar e visualizar snippets de texto.
- Interface web renderizada com templates HTML.
- Servir arquivos estáticos (CSS, JS, imagens).
- Logging de informações e erros.

## Tecnologias
- **Go**: Linguagem principal para o backend.
- **net/http**: Servidor HTTP e roteamento.
- **flag**: Configuração de argumentos de linha de comando.
- **html/template**: Renderização de templates HTML.
- **SQLC** (planejado): Geração de código a partir de consultas SQL.

## Pré-requisitos
- Go 1.21 ou superior ([instruções de instalação](https://golang.org/doc/install)).
- Git para clonar o repositório.
- (Opcional) SQLC, se for usar o banco de dados (`go install github.com/sqlc-dev/sqlc/cmd/sqlc@latest`).

## Instalação
1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/snippetbox.git
   cd snippetbox
   ```

2. Instale dependências (se houver):
   ```bash
   go mod tidy
   ```

3. Compile o programa:
   ```bash
   go build -o snippetbox ./cmd/web
   ```

## Uso
1. Execute o servidor:
   ```bash
   ./snippetbox -addr=":4000"
   ```
   - A flag `-addr` define o endereço de rede (padrão: `:4000`).

2. Acesse no navegador:
   ```
   http://localhost:4000
   ```

3. Rotas disponíveis:
   - `/`: Página inicial (renderizada com `home.tmpl`).
   - `/snippet/view`: Visualizar um snippet (a ser implementado).
   - `/snippet/create`: Criar um novo snippet (a ser implementado).
   - `/static/`: Arquivos estáticos servidos do diretório `ui/static`.

4. Logs são exibidos no terminal com prefixos `INFO` e `ERROR`.

## Estrutura do Projeto
```
snippetbox/
├── README.md           # Documentação do projeto
├── cmd/               # Ponto de entrada da aplicação
│   └── web/          # Aplicação web principal
│       ├── handlers.go  # Funções de manipulação de rotas
│       └── main.go      # Configuração do servidor HTTP
├── go.mod             # Definição de módulos e dependências
├── internal/          # Código interno (a ser implementado, ex.: modelos, DB)
├── sqlc.yaml          # Configuração do SQLC para geração de código SQL
└── ui/               # Arquivos da interface do usuário
    ├── html/         # Templates HTML
    │   ├── base.tmpl    # Template base (layout comum)
    │   ├── pages/       # Páginas específicas
    │   │   └── home.tmpl  # Template da página inicial
    │   └── partials/    # Partes reutilizáveis
    │       └── nav.tmpl   # Navegação (ex.: menu)
    └── static/       # Arquivos estáticos
        ├── css/         # Estilos
        │   └── main.css
        ├── img/         # Imagens
        │   ├── favicon.ico
        │   └── logo.png
        └── js/          # Scripts
            └── main.js
```

## Contribuindo
1. Faça um fork do repositório.
2. Crie uma branch para sua feature (`git checkout -b feat/sua-feature`).
3. Commit suas mudanças (`git commit -m "feat: descrição da mudança"`).
4. Envie um pull request.

## TODO
- Implementar lógica de armazenamento de snippets (ex.: SQLite/PostgreSQL com SQLC).
- Adicionar handlers completos em `handlers.go` para `/snippet/view` e `/snippet/create`.
- Estilizar a interface com `main.css` e adicionar interatividade com `main.js`.
- Configurar o `sqlc.yaml` para gerar modelos e queries.

## Licença
Este projeto é licenciado sob a [MIT License](LICENSE) (a definir).

## Créditos
Desenvolvido com base no livro [*Let's Go*](https://lets-go.alexedwards.net/) de Alex Edwards.

---

### Observações
- **Estrutura**: A seção "Estrutura do Projeto" reflete exatamente a árvore de diretórios que você forneceu, com descrições curtas para cada item.
- **SQLC**: Incluí uma menção ao `sqlc.yaml`, assumindo que você planeja usar SQLC para interagir com um banco de dados (como no *Let's Go*). Se isso não for o caso, posso remover.
- **TODO**: Adicionei itens que parecem lógicos para o estágio inicial do projeto, alinhados com o livro (ex.: banco de dados, handlers).
- **Comando de build**: Ajustei para `go build -o snippetbox ./cmd/web`, já que o `main.go` está em `cmd/web`.