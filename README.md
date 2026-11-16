# Facilita OAB

<p align="center">
  <strong>Estude com estratégia. Evolua com inteligência. Conquiste sua aprovação.</strong>
</p>

<p align="center">
  Plataforma de estudos desenvolvida para auxiliar estudantes de Direito na preparação para a primeira fase do Exame da Ordem dos Advogados do Brasil (OAB).
</p>

---

## 🔒 Sobre este repositório

Este é o repositório público de apresentação e documentação do **Facilita OAB**.

O código-fonte completo da plataforma está armazenado em um **repositório privado**, que concentra o desenvolvimento e os componentes internos do sistema, incluindo frontend, backend, banco de dados, integrações, configurações e demais arquivos necessários ao funcionamento da aplicação.

A separação entre os repositórios existe para preservar a segurança, a integridade e a propriedade intelectual do projeto.

**O que você encontra aqui:**
- Visão geral do Facilita OAB e de suas funcionalidades.
- Documentação técnica e arquitetural em nível de apresentação.
- Decisões e tecnologias utilizadas no desenvolvimento.
- Registro de melhorias e evolução do projeto.
- Imagens e demonstrações da plataforma.
- Planejamento de funcionalidades futuras.

**O que não está disponível publicamente:**
- Código-fonte completo da aplicação.
- Credenciais, chaves de API e variáveis de ambiente.
- Configurações internas de produção.
- Dados de usuários e informações privadas.
- Arquivos e instruções internas de desenvolvimento.

Este repositório não contém uma versão executável ou completa da plataforma. Seu objetivo é apresentar o projeto, documentar sua evolução e compartilhar informações sobre as soluções desenvolvidas.


---


## 📚 Sobre o projeto

O **Facilita OAB** é uma plataforma digital de estudos criada para auxiliar estudantes de Direito na preparação para a primeira fase do Exame da Ordem dos Advogados do Brasil.

A proposta é reunir, em um único ambiente, ferramentas que acompanham diferentes etapas da preparação: planejamento, estudo, resolução de questões, revisão de erros e análise de desempenho.

O projeto vai além de um banco de questões tradicional. Seu objetivo é funcionar como um *companion* de estudos, combinando organização automatizada, recursos de inteligência artificial e acompanhamento contínuo da evolução do estudante.

A plataforma utiliza a distribuição de conteúdos por relevância e peso das matérias na prova da FGV, buscando tornar a preparação mais direcionada e eficiente.

## ✨ Funcionalidades

### 🧑‍⚖️ Mentor Jurídico

Assistente de inteligência artificial integrado ao Google Gemini, desenvolvido para auxiliar o estudante durante sua preparação.

- Interação em tempo real por streaming SSE.
- Histórico de conversas.
- Continuidade das interações.
- Cancelamento e nova tentativa de respostas.
- Integração com o Caderno de Erros.
- Orientação voltada à compreensão de conteúdos jurídicos.

### 📝 Simulados

Sistema de avaliação com questões inéditas geradas por inteligência artificial.

- Geração de questões com saída estruturada do Gemini.
- Simulados rápidos com matérias variadas.
- Simulados direcionados por matéria.
- Resolução e acompanhamento das respostas.
- Recuperação de sessões após atualização da página.
- Registro dos resultados para acompanhamento posterior.

### 📖 Caderno de Erros

Ambiente centralizado para organizar questões e dificuldades identificadas durante os estudos.

- Integração com o Mentor Jurídico e os Simulados.
- Organização dos itens por status: aberto, revisando e dominado.
- Anotações individuais.
- Salvamento automático.
- Feedback sobre falhas de sincronização.

### 📅 Plano de Estudos e Cronograma

Planejamento adaptável para organizar a preparação até a data da prova.

- Definição da data do exame.
- Distribuição de conteúdos conforme os pesos da FGV.
- Organização das atividades de estudo.
- Acompanhamento do progresso.
- Persistência das alterações e feedback de sincronização.

### 📊 Estatísticas

Painel de acompanhamento da evolução do estudante.

- Evolução das notas nos simulados.
- Desempenho por matéria.
- Sequência de dias estudando (*streak*).
- Indicadores de evolução.
- Acompanhamento do Caderno de Erros.

### 🏠 Página inicial

Visão geral da rotina de estudos, reunindo informações relevantes para o acompanhamento diário.

- Sequência de estudos.
- Último simulado realizado.
- Atividades recentes.
- Acesso às principais funcionalidades.

---

## 🛠️ Tecnologias e ferramentas

O projeto utiliza uma arquitetura web separada entre frontend, backend e banco de dados.

| Camada | Tecnologias |
|---|---|
| Interface | React 18 |
| Build e desenvolvimento | Vite 6 |
| Estilização | Tailwind CSS 3 |
| Componentes visuais | Heroicons |
| Renderização de conteúdo | react-markdown e GFM |
| Backend | Python 3.12 e FastAPI |
| ORM | SQLAlchemy 2 |
| Migrações | Alembic |
| Validação de dados | Pydantic |
| Banco de dados | PostgreSQL |
| Inteligência artificial | Google Gemini |
| Comunicação em tempo real | Server-Sent Events (SSE) |
| Autenticação | JWT (HS256) |
| Limitação de requisições | SlowAPI |
| Containerização | Docker e Docker Compose |
| Integração contínua | GitHub Actions |

### 🎨 Design System

A interface utiliza uma identidade visual editorial, desenvolvida para oferecer uma experiência de estudo organizada, consistente e confortável.

- **Fraunces:** tipografia utilizada nos títulos.
- **Manrope:** tipografia utilizada na interface.
- Paleta visual baseada em tons de vinho e creme.
- Componentes e padrões visuais consistentes entre as funcionalidades.
- Interface pensada para diferentes tamanhos de tela.

---

## 🏗️ Arquitetura

A aplicação é organizada em camadas com responsabilidades distintas.

```text
                 FACILITA OAB
                       |
          +------------+------------+
          |                         |
       FRONTEND                  BACKEND
          |                         |
    React + Vite                 FastAPI
          |                         |
          |              +----------+----------+
          |              |          |          |
          |           Routers    Services     IA
          |              |          |          |
          |              +----------+----------+
          |                         |
          |                    SQLAlchemy
          |                         |
          |                    PostgreSQL
          |                         |
          +------ HTTP / SSE -------+
```

### Backend

O backend utiliza FastAPI e organiza as funcionalidades por domínios, mantendo separadas as responsabilidades de autenticação, perfil, cronograma, simulados, conversas, estatísticas e Caderno de Erros.

As principais responsabilidades incluem:

- Disponibilização de APIs REST.
- Autenticação e autorização.
- Validação de dados.
- Regras de negócio.
- Persistência das informações.
- Integração com serviços de inteligência artificial.
- Comunicação em tempo real por SSE.

### Frontend

O frontend utiliza React e Vite, com componentes organizados por funcionalidade e utilitários responsáveis pela comunicação com a API, gerenciamento de dados e experiência de interação.

### Banco de dados

O PostgreSQL é utilizado para persistência dos dados. O SQLAlchemy realiza o mapeamento objeto-relacional, enquanto o Alembic mantém o histórico de alterações estruturais do banco por meio de migrações versionadas.

### Inteligência artificial

A integração com o Google Gemini oferece recursos de assistência jurídica e geração de simulados.

O projeto utiliza *structured output* com validação por schemas Pydantic para estruturar as questões geradas e facilitar seu processamento pela aplicação.

---

## 🔐 Segurança e confiabilidade

A arquitetura considera aspectos importantes para a manutenção de uma aplicação web:

- Autenticação baseada em tokens JWT.
- Validação de entradas e contratos de dados.
- Proteção de rotas privadas.
- Limitação de requisições.
- Cabeçalhos de segurança HTTP.
- Controle de alterações no banco por migrações versionadas.
- Tratamento de erros de comunicação e sincronização.
- Feedback de falhas para evitar que problemas de persistência passem despercebidos.

---

## ☁️ Infraestrutura e publicação

A infraestrutura de produção utiliza serviços especializados para cada camada da aplicação:

| Serviço | Responsabilidade |
|---|---|
| Vercel | Hospedagem do frontend |
| Render | Hospedagem do backend |
| Neon | Banco de dados PostgreSQL |
| GitHub Actions | Integração contínua |

O fluxo de integração contínua contempla verificações automatizadas, testes e build da aplicação.

---

## 🚀 Evolução do projeto

O Facilita OAB está em desenvolvimento contínuo. A evolução considera tanto o aprimoramento das funcionalidades existentes quanto a preparação da arquitetura para novos cenários de utilização.

### Próxima etapa: plataforma multiusuário

Uma das principais direções de evolução é transformar a aplicação em uma plataforma multiusuário.

Essa evolução prevê:

- Cadastro e autenticação individual.
- Dados independentes para cada estudante.
- Planos de estudos e cronogramas individualizados.
- Histórico próprio de simulados e desempenho.
- Caderno de Erros e conversas independentes.
- Isolamento e proteção dos dados entre contas.

A migração deverá preservar integralmente os dados e a continuidade de utilização do usuário atual, sem exigir que ele recomece sua preparação.

---

## 📂 Documentação

Este repositório público funciona como espaço de apresentação, documentação e acompanhamento da evolução do Facilita OAB.

A documentação será organizada para registrar:

- Arquitetura e organização técnica.
- Decisões arquiteturais.
- Funcionalidades e seus objetivos.
- Planejamento de evolução.
- Histórico de desenvolvimento.
- Capturas de tela e registros visuais.

O código-fonte principal, as configurações privadas e os dados de produção permanecem em ambiente separado.

---

## 📌 Status do projeto

**Em desenvolvimento contínuo.**

O Facilita OAB é um projeto pessoal de desenvolvimento de software, construído a partir de uma necessidade real de preparação para o Exame da OAB.

Seu desenvolvimento busca conciliar engenharia de software, inteligência artificial e educação, com foco em uma experiência de aprendizagem útil, organizada e confiável.

---

<p align="center">
  <strong>Facilita OAB</strong><br/>
  Tecnologia a serviço da sua aprovação. ⚖️
</p>
