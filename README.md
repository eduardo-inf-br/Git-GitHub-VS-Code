# Git, GitHub e VS Code
Integração Profissional e Didático.

**Documento consolida o conteúdo técnico** — ao incluir Git, GitHub, VS Code, configuração inicial do Git, repositório, `git status`, `git add`, `git commit` e a integração entre editor, terminal e controle de versão.

---

## Sumário

- [1. Visão geral](#1-visão-geral)
- [2. O que é Git](#2-o-que-é-git)
- [3. Git x GitHub](#3-git-x-github)
- [4. Visual Studio Code](#4-visual-studio-code)
- [5. Instalação e configuração inicial](#5-instalação-e-configuração-inicial)
- [6. Configuração da branch principal](#6-configuração-da-branch-principal)
- [7. Criando um projeto](#7-criando-um-projeto)
- [8. Inicializando um repositório](#8-inicializando-um-repositório)
- [9. Entendendo `git status`](#9-entendendo-git-status)
- [10. Área de preparação — staging](#10-área-de-preparação--staging)
- [11. Criando um commit](#11-criando-um-commit)
- [12. Histórico de commits](#12-histórico-de-commits)
- [13. Git integrado ao VS Code](#13-git-integrado-ao-vs-code)
- [14. GitHub](#14-github)
- [15. Fluxo Git + GitHub + VS Code](#15-fluxo-git--github--vs-code)
- [16. Comandos essenciais](#16-comandos-essenciais)
- [17. Glossário](#17-glossário)
- [18. Checklist prático](#18-checklist-prático)

---

# 1. Visão geral

O vídeo apresenta um fluxo introdutório de desenvolvimento utilizando:

- **Git** para controle de versão;
- **GitHub** para hospedagem e colaboração em repositórios;
- **Visual Studio Code (VS Code)** como editor de código;
- **Terminal** para executar comandos Git;
- um projeto web simples como exemplo prático.

A ideia central é manter o histórico das alterações do projeto de maneira organizada e permitir que esse histórico seja sincronizado com um serviço remoto, como o GitHub.

### Fluxo conceitual

```text
Projeto
   │
   ▼
Arquivos modificados
   │
   ▼
git status
   │
   ▼
git add
   │
   ▼
Staging Area
   │
   ▼
git commit
   │
   ▼
Histórico local do Git
   │
   ▼
GitHub / repositório remoto
```

---

# 2. O que é Git

**Git** é um sistema distribuído de controle de versão.

Ele registra alterações realizadas nos arquivos de um projeto e permite consultar, comparar e recuperar diferentes estados do projeto.

## 2.1 Para que serve

Com Git é possível:

- acompanhar alterações;
- criar pontos de restauração;
- visualizar o histórico;
- trabalhar em diferentes branches;
- colaborar com outras pessoas;
- comparar versões;
- desfazer determinadas alterações;
- sincronizar o projeto com repositórios remotos.

## 2.2 Repositório

Um **repositório Git** é o projeto que passou a ser gerenciado pelo Git.

Ao executar:

```bash
git init
```

o Git cria a estrutura necessária para controlar as versões daquele diretório.

---

# 3. Git x GitHub

Embora os nomes sejam frequentemente usados juntos, Git e GitHub são coisas diferentes.

| Tecnologia | Função |
|---|---|
| Git | Controle de versão distribuído |
| GitHub | Plataforma para hospedar e colaborar em repositórios Git |
| VS Code | Editor de código e ambiente de desenvolvimento |
| Terminal | Interface para executar comandos |

### Git

Funciona localmente no computador.

```text
Computador
└── projeto
    └── .git
```

### GitHub

Pode armazenar uma cópia remota do repositório.

```text
Computador
   │
   │ Git
   ▼
GitHub
```

O Git pode funcionar sem GitHub. O GitHub, por sua vez, utiliza Git como parte fundamental do seu fluxo de controle de versão.

---

# 4. Visual Studio Code

O **Visual Studio Code (VS Code)** é utilizado no vídeo como editor do projeto.

Ele possui integração com Git, permitindo visualizar:

- arquivos modificados;
- alterações;
- mudanças preparadas para commit;
- histórico;
- branches;
- operações de controle de versão.

Além da interface gráfica, o VS Code possui um terminal integrado.

Exemplo:

```text
VS Code
├── Explorer
├── Source Control
├── Editor
└── Terminal
```

Isso permite editar os arquivos e executar comandos Git no mesmo ambiente.

---

# 5. Instalação e configuração inicial

Depois de instalar o Git, é recomendável verificar se ele está disponível no terminal:

```bash
git --version
```

Um resultado semelhante a este indica que o Git está instalado:

```text
git version 2.x.x
```

> O número exato depende da versão instalada.

## 5.1 Configurar o nome do usuário

Uma configuração comum é:

```bash
git config --global user.name "Seu Nome"
```

## 5.2 Configurar o e-mail

```bash
git config --global user.email "seu-email@example.com"
```

Essas informações são utilizadas nos commits criados localmente.

## 5.3 Conferir as configurações

```bash
git config --global --list
```

Também é possível consultar uma configuração específica:

```bash
git config --global user.name
git config --global user.email
```

---

# 6. Configuração da branch principal

O material visual do vídeo mostra a configuração da branch inicial como `main`.

Um comando usado para estabelecer esse padrão é:

```bash
git config --global init.defaultBranch main
```

Assim, novos repositórios inicializados com:

```bash
git init
```

podem utilizar `main` como nome da branch inicial.

## Por que `main`?

`main` é atualmente um nome amplamente utilizado para representar a branch principal de um repositório.

O nome da branch é uma convenção e pode ser alterado conforme as necessidades do projeto.

---

# 7. Criando um projeto

O vídeo utiliza um projeto web simples no VS Code.

Uma estrutura típica pode ser:

```text
my-first-project/
├── index.html
└── style.css
```

Exemplo de `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >
    <title>My First Project</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>My First Project</h1>
</body>
</html>
```

O conteúdo exato do projeto pode variar; o ponto importante para o aprendizado do Git é que os arquivos passam a ser acompanhados pelo sistema de controle de versão.

---

# 8. Inicializando um repositório

Dentro da pasta do projeto:

```bash
git init
```

O comando inicializa um novo repositório Git.

Depois disso, o Git passa a acompanhar o estado dos arquivos daquele diretório.

## Estrutura conceitual

```text
my-first-project/
├── .git/
├── index.html
└── style.css
```

A pasta `.git` contém os dados internos utilizados pelo Git para controlar as versões.

> Normalmente, não se edita manualmente o conteúdo de `.git`.

---

# 9. Entendendo `git status`

Um dos comandos mais importantes para iniciantes é:

```bash
git status
```

Ele mostra o estado atual do repositório.

Em um projeto recém-inicializado, arquivos ainda não adicionados ao controle de versão podem aparecer como **untracked files**.

Exemplo conceitual:

```text
Untracked files:
  index.html
  style.css
```

### O que significa `untracked`?

Significa que o arquivo existe no diretório de trabalho, mas ainda não foi colocado sob controle de versão pelo Git.

---

# 10. Área de preparação — staging

Antes de criar um commit, o Git possui uma etapa intermediária chamada **staging area** ou **área de preparação**.

O comando:

```bash
git add index.html
```

adiciona um arquivo específico à staging area.

Para adicionar vários arquivos:

```bash
git add .
```

ou, dependendo do fluxo desejado:

```bash
git add index.html style.css
```

## Fluxo

```text
Working Tree
     │
     │ git add
     ▼
Staging Area
     │
     │ git commit
     ▼
Repository
```

Essa separação é importante porque permite escolher exatamente quais alterações farão parte de um determinado commit.

---

# 11. Criando um commit

Depois de adicionar as alterações à staging area, cria-se um commit:

```bash
git commit -m "Initial commit"
```

Um commit representa um ponto registrado no histórico do repositório.

## Mensagem do commit

A opção:

```bash
-m
```

permite fornecer a mensagem diretamente na linha de comando.

Exemplo:

```bash
git commit -m "Adiciona estrutura inicial do projeto"
```

Uma boa mensagem deve indicar, de forma curta e clara, o que foi alterado.

### Exemplos

```bash
git commit -m "Adiciona página inicial"
git commit -m "Cria estilos básicos"
git commit -m "Corrige layout do cabeçalho"
```

---

# 12. Histórico de commits

Depois de criar commits, o histórico pode ser consultado com:

```bash
git log
```

Uma visualização resumida pode ser obtida com:

```bash
git log --oneline
```

Exemplo:

```text
a1b2c3d Adiciona estrutura inicial
```

Cada commit possui um identificador próprio, normalmente representado por um hash.

## Por que o histórico é importante?

Ele permite saber:

- quais alterações foram registradas;
- quando foram registradas;
- quem criou o commit;
- qual foi a mensagem;
- qual estado do projeto corresponde àquele ponto do histórico.

---

# 13. Git integrado ao VS Code

O VS Code possui uma área chamada **Source Control**.

Ela permite visualizar alterações sem depender exclusivamente do terminal.

O fluxo visual é equivalente ao fluxo Git:

```text
Arquivo alterado
      │
      ▼
Source Control
      │
      ▼
Stage
      │
      ▼
Commit
```

## Indicadores de alterações

Quando um arquivo é modificado, o VS Code pode indicar que há alterações pendentes.

A interface permite comparar:

```text
Versão anterior
       ↕
Versão atual
```

Essa comparação é chamada de **diff**.

---

# 14. GitHub

O **GitHub** é uma plataforma de hospedagem de repositórios Git.

Um repositório remoto pode ser usado para:

- armazenar o código;
- compartilhar projetos;
- colaborar;
- revisar alterações;
- trabalhar com branches;
- registrar issues;
- integrar ferramentas de desenvolvimento.

## Repositório local e remoto

É importante distinguir:

```text
LOCAL
└── Repositório Git no computador

REMOTO
└── Repositório hospedado no GitHub
```

Eles podem ser conectados para sincronizar alterações.

---

# 15. Fluxo Git + GitHub + VS Code

Um fluxo básico pode ser organizado assim:

```text
1. Criar projeto
       ↓
2. Abrir no VS Code
       ↓
3. git init
       ↓
4. Criar/modificar arquivos
       ↓
5. git status
       ↓
6. git add
       ↓
7. git commit
       ↓
8. Conectar ao GitHub
       ↓
9. git push
```

Quando existe um repositório remoto, o Git permite enviar os commits locais para esse repositório.

## Comandos de sincronização

Adicionar um remoto:

```bash
git remote add origin URL_DO_REPOSITORIO
```

Verificar os remotos:

```bash
git remote -v
```

Enviar a branch para o remoto:

```bash
git push -u origin main
```

> O comando exato pode variar conforme o nome da branch e a configuração do repositório remoto.

---

# 16. Comandos essenciais

## Verificar a instalação

```bash
git --version
```

## Configurar identidade

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

## Configurar branch inicial

```bash
git config --global init.defaultBranch main
```

## Inicializar repositório

```bash
git init
```

## Ver estado

```bash
git status
```

## Adicionar arquivo

```bash
git add arquivo.ext
```

## Adicionar alterações

```bash
git add .
```

## Criar commit

```bash
git commit -m "Mensagem do commit"
```

## Consultar histórico

```bash
git log
```

## Histórico resumido

```bash
git log --oneline
```

## Adicionar repositório remoto

```bash
git remote add origin URL_DO_REPOSITORIO
```

## Consultar repositórios remotos

```bash
git remote -v
```

## Enviar alterações

```bash
git push -u origin main
```

---

# 17. Glossário

| Termo | Significado |
|---|---|
| **Git** | Sistema distribuído de controle de versão |
| **GitHub** | Plataforma de hospedagem e colaboração para repositórios Git |
| **Repositório** | Estrutura usada para armazenar o histórico do projeto |
| **Commit** | Registro de um conjunto de alterações |
| **Branch** | Linha independente de desenvolvimento |
| **Main** | Nome convencional da branch principal |
| **Working tree** | Estado dos arquivos no diretório de trabalho |
| **Staging area** | Área onde alterações são preparadas antes do commit |
| **Untracked** | Arquivo ainda não acompanhado pelo Git |
| **Remote** | Repositório remoto associado ao projeto |
| **Origin** | Nome convencional do primeiro remoto |
| **Push** | Envio de commits locais para um repositório remoto |
| **Pull** | Obtenção e integração de alterações do remoto |
| **Diff** | Comparação entre versões/estados de arquivos |

---

# 18. Checklist prático

## Configuração inicial

- [ ] Instalar Git
- [ ] Verificar `git --version`
- [ ] Configurar `user.name`
- [ ] Configurar `user.email`
- [ ] Definir `main` como branch inicial, se desejado

## Novo projeto

- [ ] Criar a pasta do projeto
- [ ] Abrir no VS Code
- [ ] Executar `git init`
- [ ] Executar `git status`

## Primeiro registro

- [ ] Criar ou adicionar os arquivos
- [ ] Executar `git add`
- [ ] Conferir `git status`
- [ ] Executar `git commit -m "..."`

## GitHub

- [ ] Criar o repositório remoto
- [ ] Associar o remoto com `git remote add origin`
- [ ] Conferir com `git remote -v`
- [ ] Enviar com `git push`

---

# Referência rápida

```bash
# Verificar Git
git --version

# Configuração
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"

# Branch inicial
git config --global init.defaultBranch main

# Criar repositório
git init

# Ver alterações
git status

# Preparar arquivos
git add .

# Registrar alterações
git commit -m "Mensagem"

# Ver histórico
git log --oneline

# Configurar remoto
git remote add origin URL_DO_REPOSITORIO

# Ver remoto
git remote -v

# Enviar para GitHub
git push -u origin main
```

---

## Conclusão

O fluxo fundamental apresentado pode ser resumido em:

```text
EDITAR
  ↓
VERIFICAR
  ↓
git status
  ↓
PREPARAR
  ↓
git add
  ↓
REGISTRAR
  ↓
git commit
  ↓
SINCRONIZAR
  ↓
git push
```

A combinação de **Git + GitHub + VS Code** permite que o desenvolvedor edite o projeto, acompanhe suas alterações, registre versões e, quando configurado um repositório remoto, sincronize o histórico com o GitHub.

---

**`Informática para Internet`**

O suporte fornecido por corporações permite-nos o desenvolvimento e implementação de programas, projetos e recursos para Eduardo.Inf.Br. Através dessas parcerias é possível que empreendedores e proprietários de pequenas empresas, recebam ampla variedade de conteúdos e ferramentas por meio de sistemas e suporte. "[Eduardo.Inf.Br](https://informatizar.netlify.app/)".

---

<img 
    align="left" 
    alt="HTML"
    title="HTML" 
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" 
/>
<img 
    align="left" 
    alt="CSS" 
    title="CSS"
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" 
/>
<img 
    align="left" 
    alt="JavaScript" 
    title="JavaScript"
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" 
/>
<img 
    align="left" 
    alt="Bootstrap"
    title="Bootstrap" 
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bootstrap/bootstrap-original.svg" 
/>
<img 
    align="left" 
    alt="Git" 
    title="Git"
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg" 
/>
