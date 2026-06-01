# API de Catálogo de Livros — Demo Docker

API REST simples em FastAPI usada como exemplo na aula de Containers (Engenharia de Software II).

## Estrutura do projeto

```
api-livros-docker-demo/
├── main.py            # Aplicação FastAPI e rotas
├── models.py          # Modelos Pydantic (Livro)
├── repository.py      # Repositório em memória
├── requirements.txt   # Dependências Python
├── Dockerfile         # Receita do container
└── .dockerignore      # Arquivos que ficam fora da imagem
```

## Rodando localmente (sem Docker)

```bash
pip install -r requirements.txt
uvicorn main:app --reload
```

Acesse a documentação interativa em `http://localhost:8000/docs`.

## Rodando com Docker

### 1. Clone o repositório

```bash
git clone <url-deste-repositorio>
cd api-livros-docker-demo
```

### 2. Construa a imagem

```bash
docker build -t catalogo-livros .
```

### 3. Suba o container

```bash
docker run -p 8000:8000 catalogo-livros
```

A API estará disponível em `http://localhost:8000/docs`.

## Rodando no Killercoda

1. Acesse `https://killercoda.com/playgrounds/scenario/docker` (ou outro cenário Ubuntu com Docker)
2. No terminal, execute os mesmos comandos da seção anterior
3. Para acessar a API rodando no navegador, use o botão de "expor porta" do Killercoda informando a porta `8000`

## Endpoints

| Método | Caminho           | Descrição                |
|--------|-------------------|--------------------------|
| GET    | /livros           | Lista todos os livros    |
| GET    | /livros/{id}      | Busca um livro por id    |
| POST   | /livros           | Cria um livro            |
| PUT    | /livros/{id}      | Atualiza um livro        |
| DELETE | /livros/{id}      | Remove um livro          |

## Notas

- A persistência é **em memória**. Os dados somem a cada restart do container — comportamento esperado para o escopo desta aula.
- A documentação interativa Swagger fica em `/docs` e permite testar todos os endpoints pelo navegador.
