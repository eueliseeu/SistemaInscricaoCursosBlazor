# SistemaDeInscrição

Aplicação web desenvolvida com **ASP.NET Core Blazor Web App** como atividade prática da disciplina de Desenvolvimento Web. O sistema permite a inscrição de usuários em cursos por meio de um formulário interativo, com validação em tempo real, feedback visual assíncrono e layout responsivo.

---

## Sumário

- [SistemaDeInscrição](#sistemadeinscrição)
  - [Sumário](#sumário)
  - [Funcionalidades](#funcionalidades)
  - [Tecnologias](#tecnologias)
  - [Pré-requisitos](#pré-requisitos)
  - [Instalação e Execução](#instalação-e-execução)
  - [Estrutura do Projeto](#estrutura-do-projeto)
  - [Validações](#validações)
    - [Fluxo de envio](#fluxo-de-envio)
  - [Autor](#autor)

---

## Funcionalidades

- Formulário de inscrição com vinculação de dados via `[SupplyParameterFromForm]`
- Validação de campos com `DataAnnotations` (nome, e-mail, idade e curso)
- Seleção de curso via componente `<InputSelect>`
- Feedback visual assíncrono com `Task.Delay` durante o envio
- Notificação de confirmação após inscrição bem-sucedida
- Layout responsivo com Bootstrap 5
- Botão de envio desabilitado com texto dinâmico durante o processamento

## Tecnologias

| Tecnologia | Versão | Finalidade |
| --- | --- | --- |
| .NET | 10 | Runtime e SDK |
| ASP.NET Core Blazor | Web App | Framework principal |
| Bootstrap | 5 | Estilização responsiva |

## Pré-requisitos

- [.NET SDK 10](https://dotnet.microsoft.com/download) ou superior instalado
- Git instalado

Verifique sua versão do .NET:

```bash
dotnet --version
```

## Instalação e Execução

```bash
# Clone o repositório
git clone https://github.com/eueliseeu/sistema-inscricao-cursos-blazor.git

# Acesse a pasta do projeto
cd sistema-inscricao-cursos-blazor

# Execute com hot reload
dotnet watch run
```

Acesse no navegador:

```
http://localhost:5240/inscricao
```

## Estrutura do Projeto

```
SistemaInscricaoCursosBlazor/
├── Components/
│   ├── Models/
│   │   └── InscricaoModel.cs
│   ├── Pages/
│   │   ├── Inscricao.razor
│   │   └── Inscricao.razor.css
│   └── Layout/
│       ├── MainLayout.razor
│       └── MainLayout.razor.css
├── wwwroot/
│   └── app.css
├── Program.cs
└── SistemaInscricaoCursosBlazor.csproj
```

## Validações

| Campo | Restrição |
| --- | --- |
| **Nome** | Obrigatório |
| **E-mail** | Obrigatório; formato válido via `[EmailAddress]` |
| **Idade** | Obrigatória; entre 16 e 100 anos via `[Range(16, 100)]` |
| **Curso** | Obrigatório; selecionado via `<InputSelect>` |

### Fluxo de envio

1. Usuário preenche e submete o formulário
2. `OnValidSubmit` é acionado — `enviando = true`
3. Botão é desabilitado e exibe *"Processando..."*
4. `await Task.Delay(2000)` simula uma requisição assíncrona
5. `sucesso = true` — notificação de confirmação é exibida

## Autor

Desenvolvido como atividade da disciplina **Desenvolvimento Web** — Professor Daniel Henrique Matos de Paiva.
