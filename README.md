# Ambientes virtuais com Python

Quando queremos trabalhar em diferentes projetos, ou com diferentes profissionais é importante que possamos controlar de forma fácil como as pessoas podem ter um ambiente igual o nosso, ou ainda como podemos ter diferentes ambientes na mesma máquina. Para isso o ideal é usarmos estratégias de ambientes virtuais, dessa forma isolando nossos projetos.

Importante notar que nesse README não veremos como instalar cada uma das bibliotecas, apenas seus modos de uso.
O recomendado é que apenas o **Pyenv seja instalado de forma global**, que o **Pipx seja instalado dentro da versão Global do Pyenv** e o **Poetry e Ipython sejam instalados dentro do Pipx**.

Em caso de dúvidas, [esse vídeo foi usado como base para esses ambientes](https://www.youtube.com/watch?v=9LYqtLuD7z4).

## Pyenv

O Pyenv é usado para termos uma versão de Python global (quase como uma versão padrão de Python) e outras versões locais, podendo mudar a versão dependendo do projeto que estamos.

- Para baixar uma versão usamos: `pyenv install <version>`
- Para definir a versão global usamos: `pyenv global <version>`
- Para definir uma versão local usamos: `pyenv local <version>`

Quando definimos uma versão local será criado um arquivo _.python-version_, que depois será o arquivo lido pelo Pyenv para alternar entre as versões dependendo do projeto que o terminar está atualmente.

## Venv

O Venv é usado para isolarmos um projeto do ambiente root que temos na nossa máquina. Fazendo isso ele cria um ambiente local que pode ser ativado e usado para instalar dependências em versões expecíficas sem que essa instalação possa impactar outros projetos. Dessa forma podemos por exemplo ter 2 versões diferentes do Pandas em projetos distintos com a mesma versão de Python.

- Para criarmos um ambiente virtual usamos: `python -m venv .venv` (usa o comando python executando o módulo venv e usando o nome .venv como nome do diretório)
- Para ativar o ambiente (no Linux e Mac): `source .venv/bin/activate`
- Para desativar o ambiente `deactivate`

Importante notar que se dermos um `pip list` ou `pip freeze` poderemos ver os pacotes que temos que foram instalados com Pip do pypi (repositório de pacotes do Python).

## Pipx

Usado para criar ambientes isolados, sem que os pacotes instalados por um usuário interfiram nos outros. Além de ter um melhor controle das versões instaladas, simplificando a atualização.

Recomendado para baixar pacotes globais como o `poetry` (gerenciador de projetos) e `ipython` (interface mais amigavel para desenvolvimento interativo)

- Para listar os pacotes: `pipx list`
- Para instalar pacotes: `pipx install <package>`

## Poetry

Usado para gerenciamento de projetos, cria uma estutura base do projeto já com alguns diretórios base, um arquivo de gerenciamento de dependências mais robusto e uma estrutura mais completa.

**Para que ele possa controlar os ambientes virtuais primeiro usar esse comando**: `poetry config virtualenvs.in-project true `

- Criação de um novo projeto: `poetry new <project_name>`
- Definição de versão local do Python para o Poetry e criação do Venv: `poetry env use <version>` **(importante notar que mesmo assim precisa antes usar o `pyenv local <version>`)**
- Instala um pacote: `poetry add <package>`
- Remove um pacote: `poetry remove <package>`
