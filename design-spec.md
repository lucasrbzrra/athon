# Athon — Design Specification (SDD)
> Ecossistema vivo de benchmark de RH — dados de mercado confiáveis para decisões de pessoas

---

## 0. INSTRUÇÃO DE GERAÇÃO (leia primeiro)

Você é um gerador de design de produto. A partir desta especificação, **gere o protótipo completo e navegável da plataforma Athon**, com todas as telas funcionais, fluxos conectados e dados de exemplo realistas.

**O que entregar:**
- **Todas as 8 telas** descritas na Seção 4, cada uma como uma view completa e visualmente acabada (não wireframe cinza — design final com cores, tipografia e espaçamento desta spec).
- **Navegação real entre telas**: clicar nos CTAs leva à tela correspondente conforme os fluxos da Seção 6. O protótipo deve ser clicável de ponta a ponta.
- **Dados de exemplo (mock)**: use os valores concretos da Seção 8 para popular cards, formulários e dashboards. Nada de "Lorem ipsum" ou placeholders vazios.
- **A tela principal (`/app/temas`) deve exibir os 22 temas reais** listados na Seção 8.1, cada um como um card, com seus ícones, categorias e dado-chave.
- **Estados visíveis**: demonstre os estados de cada componente (Seção 7) — ex.: alguns cards "Respondidos" e outros "Não respondidos" no catálogo; um dashboard com a seção "Sua Posição" preenchida.
- **Responsivo**: layouts adaptam para desktop, tablet e mobile conforme indicado.

**Tom visual:** profissional, confiável e moderno — um SaaS de inteligência de dados para RH corporativo. Limpo, com bastante respiro, dados numéricos em destaque, sensação de "ferramenta séria que entrega insight rápido".

**Ícones:** use **sempre ícones de uma biblioteca vetorial** (Lucide, Heroicons ou equivalente), com traço consistente. **Nunca use emojis** em nenhum lugar da interface — nem em cards, botões, badges, mensagens, estados vazios ou ilustrações. Onde esta spec sugere um ícone (ex.: na tabela dos 22 temas), trate o nome como referência a um ícone vetorial, não a um emoji.

**Idioma de toda a interface:** Português do Brasil.

---

## 1. Identidade do Produto

**Nome:** Athon
**Etimologia:** Átomo + H de Humano. Representa a menor unidade de inteligência de mercado para o RH: questionários micro, precisos e atômicos que, em conjunto, formam um ecossistema vivo de dados.
**Posicionamento:** Plataforma SaaS colaborativa de benchmark de RH. Empresas contribuem com dados de suas próprias políticas e acessam, em troca, o panorama real do mercado — por setor, porte e região.
**Público-alvo:** Profissionais e líderes de RH de empresas de médio e grande porte com área de pessoas estruturada.
**Tagline:** Ecossistema vivo de benchmark de RH — dados de mercado confiáveis para decisões de pessoas.

**Princípio do produto:** *Você dá um dado, recebe o mercado inteiro.* Quanto mais empresas participam, mais rico o ecossistema — efeito de rede no centro da experiência.

---

## 2. Design System

### 2.1 Paleta de Cores

| Token | Hex | Uso |
|---|---|---|
| `--color-brand-primary` | `#1B4DFF` | CTAs, links ativos, progresso |
| `--color-brand-secondary` | `#0A1F6E` | Fundo de headers, sidebar, cabeçalho de cards |
| `--color-accent` | `#4DFFD2` | Destaques, badges de crédito, hover states |
| `--color-surface-0` | `#F4F6FB` | Fundo geral da aplicação |
| `--color-surface-1` | `#FFFFFF` | Cards, modais, painéis |
| `--color-surface-2` | `#E8ECF4` | Divisores, fundos de input desabilitado |
| `--color-text-primary` | `#0D1117` | Títulos, labels |
| `--color-text-secondary` | `#4B5563` | Subtítulos, descrições, placeholders |
| `--color-text-disabled` | `#9CA3AF` | Estados desabilitados |
| `--color-success` | `#10B981` | Confirmações, créditos ganhos |
| `--color-warning` | `#F59E0B` | Alertas de crédito baixo |
| `--color-error` | `#EF4444` | Erros de validação |
| `--color-p25` | `#93C5FD` | Percentil 25 nos gráficos |
| `--color-p50` | `#1B4DFF` | Percentil 50 (mediana) nos gráficos |
| `--color-p75` | `#0A1F6E` | Percentil 75 nos gráficos |

### 2.2 Tipografia

| Token | Fonte | Tamanho | Peso | Uso |
|---|---|---|---|---|
| `--text-display` | Inter | 36px | 700 | Título de página principal |
| `--text-heading-1` | Inter | 28px | 700 | Títulos de seção |
| `--text-heading-2` | Inter | 22px | 600 | Títulos de card |
| `--text-heading-3` | Inter | 18px | 600 | Subtítulos, labels de grupo |
| `--text-body` | Inter | 16px | 400 | Corpo de texto |
| `--text-body-sm` | Inter | 14px | 400 | Textos secundários, helpers |
| `--text-label` | Inter | 13px | 500 | Labels de campo, badges |
| `--text-caption` | Inter | 12px | 400 | Notas, tooltips |
| `--text-mono` | JetBrains Mono | 14px | 400 | Dados numéricos, percentis |

### 2.3 Espaçamento

| Token | Valor | Uso |
|---|---|---|
| `--space-1` | 4px | Espaço mínimo entre ícone e label |
| `--space-2` | 8px | Padding interno de badges e chips |
| `--space-3` | 12px | Gap entre elementos em linha |
| `--space-4` | 16px | Padding de inputs e botões |
| `--space-5` | 20px | Gap interno de cards pequenos |
| `--space-6` | 24px | Padding de cards padrão |
| `--space-8` | 32px | Espaçamento entre seções internas |
| `--space-10` | 40px | Margem entre seções de página |
| `--space-12` | 48px | Padding de containers de formulário |
| `--space-16` | 64px | Espaçamento de seções de landing |

### 2.4 Border Radius

| Token | Valor | Uso |
|---|---|---|
| `--radius-sm` | 6px | Badges, chips, tags |
| `--radius-md` | 10px | Inputs, botões |
| `--radius-lg` | 16px | Cards padrão |
| `--radius-xl` | 24px | Modais, painéis de dashboard |
| `--radius-full` | 9999px | Avatares, indicadores de status |

### 2.5 Sombras

| Token | Valor | Uso |
|---|---|---|
| `--shadow-sm` | `0 1px 3px rgba(0,0,0,0.08)` | Cards em repouso |
| `--shadow-md` | `0 4px 12px rgba(0,0,0,0.10)` | Cards em hover, dropdowns |
| `--shadow-lg` | `0 8px 24px rgba(0,0,0,0.12)` | Modais, toasts |
| `--shadow-brand` | `0 4px 16px rgba(27,77,255,0.24)` | Botões primários em hover |

### 2.6 Componentes Base

**Botão Primário:** `background: --color-brand-primary`, `color: white`, `border-radius: --radius-md`, `padding: --space-4 --space-6`, `font: --text-label / 500`, hover eleva `--shadow-brand`.

**Botão Secundário:** `border: 1.5px solid --color-brand-primary`, `color: --color-brand-primary`, `background: transparent`, mesmo border-radius.

**Botão Ghost:** sem borda e sem fundo, `color: --color-text-secondary`, apenas underline no hover.

**Input:** `background: --color-surface-1`, `border: 1.5px solid --color-surface-2`, `border-radius: --radius-md`, `padding: --space-4`, foco muda borda para `--color-brand-primary` com `box-shadow: 0 0 0 3px rgba(27,77,255,0.12)`.

**Badge de Crédito:** `background: rgba(77,255,210,0.15)`, `color: --color-brand-secondary`, `border-radius: --radius-sm`, ícone de moeda à esquerda.

**Card de Tema:** `background: --color-surface-1`, `border-radius: --radius-lg`, `box-shadow: --shadow-sm`, borda superior de 3px em `--color-brand-primary`. Hover: `box-shadow: --shadow-md`, leve `translateY(-2px)`.

**Chip de Filtro:** `border-radius: --radius-full`, `border: 1.5px solid --color-surface-2`, ativo recebe `background: --color-brand-primary`, `color: white`, sem borda.

**Logomarca:** wordmark "Athon" em Inter 700, com o "h" estilizado (ponto de átomo / órbita sobre o "h"). Em fundos escuros, texto branco com o "h" em `--color-accent`.

---

## 3. Arquitetura de Telas

```
/ (landing)
├── /cadastro                          ← criar conta (toggle Empresa | Consultor)
├── /login                             ← entrar
│
├── /app  ........................... PERSONA EMPRESA
│   ├── /app/temas                     ← TELA PRINCIPAL: catálogo dos 22 temas (cards)
│   ├── /app/temas/:slug/formulario    ← formulário de coleta do tema
│   ├── /app/temas/:slug/sucesso       ← confirmação de resposta
│   ├── /app/temas/:slug/dashboard     ← dashboard de benchmark do tema
│   ├── /app/planos                    ← planos e créditos
│   └── /app/consultores               ← consultores vinculados (desvincular)
│
├── /consultor  ..................... PERSONA CONSULTOR (fluxo extra — Seção 9)
│   ├── /consultor/clientes            ← painel: lista de empresas-cliente (cards)
│   ├── /consultor/clientes/novo       ← cadastrar cliente por CNPJ + e-mail
│   └── /consultor/clientes/:cnpj/envio← selecionar formulários e enviar ao cliente
│
└── /responder  ..................... FLUXO PÚBLICO SEM LOGIN (cliente convidado)
    ├── /responder/:chave              ← acesso por link + chave: lista de formulários
    └── /responder/:chave/:slug        ← formulário público vinculado ao CNPJ
```

**Total: telas a gerar** — 7 telas da persona Empresa (cadastro, login, catálogo, formulário, sucesso, dashboard, planos) + `/app/consultores` + 3 telas da persona Consultor + 2 telas do fluxo público de resposta. Priorize o catálogo de temas como tela principal da Empresa e `/consultor/clientes` como tela principal do Consultor. A `/` landing é opcional.

---

## 4. Telas — Especificação por Prompt

---

### 4.1 Tela de Cadastro (`/cadastro`)

**Prompt de tela:**
> Crie uma tela de cadastro institucional para a plataforma Athon. A tela deve transmitir credibilidade e modernidade para profissionais de RH. O layout é dividido em dois painéis horizontais: à esquerda, um painel escuro (`--color-brand-secondary`) com a logomarca Athon, a tagline "Ecossistema vivo de benchmark de RH", e três benefícios listados com ícone e texto curto (Dados de mercado em tempo real / Formulários rápidos de 5 a 10 minutos / 10 créditos gratuitos ao cadastrar). À direita, fundo `--color-surface-0`, formulário centralizado com título "Crie sua conta" e subtítulo "Acesse dados de mercado reais para o seu RH.". **No topo do formulário, um seletor de tipo de conta (segmented control de duas opções): "Empresa" e "Consultor externo"** — a opção selecionada muda os campos exibidos abaixo e o destino após o cadastro.

**Seletor de tipo de conta (no topo do formulário):**
- **Empresa** (padrão) — quem contribui com dados e paga pelos créditos. Mostra os campos abaixo e leva a `/app/temas`.
- **Consultor externo** — quem gerencia várias empresas-cliente. Ver campos e regras na Seção 9.1; leva a `/consultor/clientes`.

**Campos do formulário (tipo "Empresa"):**
- Nome completo (texto, obrigatório) — ex.: `Marina Costa`
- E-mail corporativo (e-mail, obrigatório) — ex.: `marina.costa@empresa.com.br`
- Empresa (texto, obrigatório) — ex.: `Nimbus Tecnologia`
- CNPJ (texto com máscara `00.000.000/0000-00`, obrigatório) — ex.: `12.345.678/0001-90`
- Segmento da empresa (select: Tecnologia / Indústria / Varejo / Serviços / Saúde / Financeiro / Outro)
- Porte da empresa (select: Até 100 colaboradores / 101–500 / 501–2.000 / Acima de 2.000)
- Região (select: Sul / Sudeste / Centro-Oeste / Nordeste / Norte)
- Senha (password, mínimo 8 caracteres)
- Confirmação de senha (password)

**CTA:** Botão primário "Criar conta e ganhar 10 créditos" ocupando largura total do formulário.

**Rodapé do formulário:** Link "Já tenho uma conta → Entrar" em `--text-body-sm`.

**Regras de negócio:**
- E-mail deve ter domínio corporativo (não aceitar gmail, hotmail, yahoo, outlook pessoal).
- CNPJ é obrigatório, validado (formato + dígitos verificadores) e único na plataforma: se já houver conta para o CNPJ, exibir aviso "Já existe uma conta para este CNPJ" com link "Entrar". O CNPJ é a chave que identifica a empresa no ecossistema e ancora a regra de um administrador principal por CNPJ (ver Seção 5.5).
- Após o cadastro bem-sucedido, 10 créditos são creditados automaticamente na conta.
- Toast de sucesso: "Conta criada! Você ganhou 10 créditos de boas-vindas." com ícone em `--color-success`.
- Ao concluir, **navega para `/app/temas`**.

---

### 4.2 Tela de Login (`/login`)

**Prompt de tela:**
> Crie uma tela de login clean e objetiva para a Athon. Layout centralizado na tela com fundo `--color-surface-0`. No centro, um card branco com `--radius-xl` e `--shadow-lg` contendo: logomarca Athon no topo, título "Bem-vindo de volta" e subtítulo "Continue tomando decisões baseadas em dados.". Abaixo do formulário, um bloco destacado em `rgba(27,77,255,0.06)` com borda esquerda de 3px em `--color-brand-primary` mostrando a mensagem "Preencha formulários e ganhe créditos para acessar o benchmark do mercado."

**Campos do formulário:**
- E-mail corporativo (e-mail, obrigatório)
- Senha (password, obrigatório)
- Checkbox "Manter conectado"

**CTA:** Botão primário "Entrar" largura total.

**Links auxiliares:** "Esqueci minha senha" (ghost button, alinhado à direita acima do CTA) e "Criar conta" (link abaixo do CTA, **navega para `/cadastro`**).

**Regras de negócio:**
- Máximo de 5 tentativas com senha incorreta antes de bloquear o acesso por 15 minutos.
- Sessão persistente de 30 dias se "Manter conectado" estiver ativo.
- Ao concluir, **navega para `/app/temas`**.

---

### 4.3 Catálogo de Temas — TELA PRINCIPAL (`/app/temas`)

**Prompt de tela:**
> Crie a tela principal da plataforma Athon — o catálogo com os **22 temas de benchmark**. No topo, uma topbar fixa com a logomarca à esquerda e à direita o indicador de créditos do usuário (ícone de moeda + número + label "créditos") e o avatar do usuário com nome da empresa. Abaixo da topbar, um header de página com título "Temas de Benchmark" e subtítulo "Escolha um tema, contribua com seus dados e acesse o panorama do mercado.". Logo abaixo, uma faixa de resumo com 3 mini-indicadores: "22 temas disponíveis", "X temas respondidos por você", "Y empresas no ecossistema". Em seguida, uma barra de filtros horizontal com chips selecionáveis por categoria (ver Seção 8.2). Abaixo, um **grid responsivo com os 22 cards de tema** — 3 colunas em desktop, 2 em tablet, 1 em mobile.

> **Importante:** gere os 22 cards reais listados na Seção 8.1, cada um com seu ícone, título, categoria e dado-chave. Misture os estados: marque alguns como "Respondido" (ex.: temas 1, 9, 12, 13) e o restante como "Não respondido", para demonstrar os estados de card da Seção 7.1.

**Anatomia do Card de Tema:**
- Barra superior colorida de 3px em `--color-brand-primary`
- Ícone do tema (24px, em `--color-brand-primary`)
- Tag de categoria (chip pequeno em `--text-caption`)
- Título do tema (`--text-heading-2`)
- Descrição de uma linha com o dado-chave do tema (`--text-body-sm`, `--color-text-secondary`)
- Rodapé do card: status badge à esquerda (verde "Respondido" ou cinza "Não respondido") + contagem "N empresas participaram" em `--text-caption`
- CTA do card varia por estado:
  - não respondido → botão secundário "Responder · +5 créditos"
  - respondido, benchmark não acessado → botão primário "Ver benchmark · 3 créditos"
  - respondido, benchmark acessado → botão ghost "Ver benchmark"

**Regras de negócio:**
- Temas com status "Respondido" exibem um ícone de check no canto superior direito do card.
- "Responder" **navega para** `/app/temas/:slug/formulario`. "Ver benchmark" **navega para** `/app/temas/:slug/dashboard` e consome 3 créditos.
- Se o usuário não tiver créditos suficientes para o benchmark, o clique abre o **modal "Créditos insuficientes"** (Seção 6.3).
- Os filtros de categoria são exclusivos (single select). "Todos" desmarca qualquer filtro ativo e mostra os 22 temas.

---

### 4.4 Formulário por Tema (`/app/temas/:slug/formulario`)

**Prompt de tela:**
> Crie a tela de formulário de coleta de dados da Athon. Layout de coluna única, centralizado, largura máxima de 680px. No topo, uma breadcrumb "Temas → [Nome do Tema]". Abaixo, o cabeçalho do formulário: título do tema em `--text-heading-1`, e um bloco de contexto em `--color-surface-2` com `--radius-md` explicando em 2–3 linhas o que será coletado e por que importa. Uma barra de progresso linear abaixo do cabeçalho mostra o avanço por grupos de perguntas (ex.: "Grupo 2 de 3"). As perguntas são agrupadas em seções com título de grupo. Ao final, um rodapé fixo na base da tela com o botão primário "Enviar e ganhar 5 créditos" e o texto auxiliar "Seus dados são anonimizados antes de qualquer uso".

> **Gere o formulário concreto do tema "Reembolso de Km" usando as perguntas de exemplo da Seção 8.3.** Os tipos de campo abaixo cobrem todos os formulários da plataforma.

**Tipos de campo utilizados nos formulários:**
- Numérico com unidade (ex.: "R$/km", "%", "horas/ano", "R$")
- Select simples (opção única)
- Select múltiplo (múltiplas opções)
- Escala (slider de 0 a 100%)
- Radio group (opção exclusiva com labels descritivos)
- Toggle (sim/não)

**Regras de negócio:**
- Nenhum campo obrigatório pode ser enviado em branco. Campos não obrigatórios são marcados como "(opcional)".
- Validação em tempo real: campos numéricos alertam se o valor estiver fora de faixas de consistência (ex.: reajuste salarial acima de 100% gera um aviso amarelo, não bloqueio).
- O formulário salva progresso automaticamente a cada 60 segundos (mostrar microcopy "Rascunho salvo" discreto).
- Após envio bem-sucedido, **navega para** `/app/temas/:slug/sucesso`.
- Ao clicar em "Voltar para Temas" sem enviar, exibir modal de confirmação: "Seu progresso foi salvo. Deseja sair?"

---

### 4.5 Tela de Sucesso de Resposta (`/app/temas/:slug/sucesso`)

**Prompt de tela:**
> Crie uma tela de confirmação de envio de formulário para a Athon. Layout centralizado na tela, coluna única, fundo `--color-surface-0`. No centro, um card branco com `--radius-xl` e `--shadow-lg` contendo: um ícone animado de check em círculo verde (`--color-success`) no topo, título "Contribuição registrada!" em `--text-heading-1`, subtítulo "Seus dados foram anonimizados e já estão enriquecendo o ecossistema Athon.". Abaixo, um bloco de destaque com borda e fundo em `rgba(77,255,210,0.12)` mostrando "+5 créditos adicionados" com o ícone de moeda e o saldo total atualizado (ex.: "Saldo atual: 20 créditos"). Dois botões abaixo: primário "Ver benchmark deste tema · 3 créditos" e ghost "Voltar ao catálogo de temas".

**Regras de negócio:**
- Os 5 créditos são exibidos imediatamente, com animação de contador no saldo do header.
- O botão "Ver benchmark" **navega para** `/app/temas/:slug/dashboard` e consome 3 créditos.
- O botão ghost **navega para** `/app/temas`.
- Se o saldo após o ganho ainda for < 3, o botão primário é substituído por "Comprar créditos" (**navega para** `/app/planos`).

---

### 4.6 Dashboard de Tema (`/app/temas/:slug/dashboard`)

**Prompt de tela:**
> Crie o dashboard de benchmark por tema da Athon. No topo, breadcrumb "Temas → [Nome do Tema] → Benchmark". Título da página com o nome do tema e badge "Dados ao vivo" com um indicador pulsante verde. À direita do título, uma linha com "N empresas participaram" e a última data de atualização. Abaixo do título, uma barra de filtros contextuais com 3 dropdowns: Segmento, Porte e Região (mesmas opções do cadastro, com a opção "Todos" como padrão). Todos os dados do dashboard respondem visualmente aos filtros selecionados. O conteúdo principal é organizado em seções com cartões de métrica e visualizações gráficas.

> **Gere o dashboard concreto do tema "Reembolso de Km" usando os dados de exemplo da Seção 8.4.**

**Estrutura de conteúdo do dashboard:**

**Seção 1 — Visão Geral (topo).** Três cartões lado a lado com os percentis principais:
- Card P25: label "Quartil inferior", valor grande em `--text-mono`, cor `--color-p25`
- Card P50: label "Mediana do mercado" (destaque visual maior), valor grande em `--text-mono`, cor `--color-p50`
- Card P75: label "Quartil superior", valor grande em `--text-mono`, cor `--color-p75`

**Seção 2 — Distribuição do Mercado.** Gráfico de barras (histograma) mostrando a distribuição dos valores respondidos pelas empresas, agrupados em faixas. Eixo X: faixas de valor; Eixo Y: % de empresas. Linha vertical tracejada marcando a posição da empresa logada.

**Seção 3 — Sua Posição no Mercado.** Bloco visível apenas se a empresa já respondeu o tema. Exibe: o valor informado pela empresa, em qual percentil ela está (ex.: "Você está no P62 do mercado") e um gauge linear horizontal com marcação da posição entre P25 e P75.

**Seção 4 — Recorte por Segmento.** Gráfico de barras agrupadas (ou tabela) mostrando a mediana (P50) do dado-chave por setor, para identificar variações entre segmentos.

**Seção 5 — Tendência.** Gráfico de linha simples mostrando a evolução da mediana ao longo dos últimos ciclos de coleta.

**Regras de negócio:**
- O acesso consome 3 créditos na primeira consulta; consultas subsequentes ao mesmo tema são gratuitas.
- Dados anonimizados: nenhum dado individual de empresa é exibível. A menor granularidade visível é a mediana de um grupo com mínimo de 5 empresas.
- Se o filtro retornar menos de 5 empresas, substituir gráficos por: "Dados insuficientes para este recorte. Amplie os filtros para ver resultados."
- A Seção 3 só aparece se a empresa respondeu o tema; caso contrário, mostrar CTA "Responda para ver sua posição".
- O badge "Dados ao vivo" reflete a última atualização; se >30 dias sem novos dados, muda para "Atualizado há N dias" em `--color-warning`.

---

### 4.7 Tela de Planos (`/app/planos`)

**Prompt de tela:**
> Crie a tela de planos e créditos da Athon. Cabeçalho de página com título "Créditos e Planos" e subtítulo "Contribua com dados e ganhe créditos. Ou escolha um plano para acesso contínuo.". Logo abaixo, um bloco de saldo atual do usuário: ícone de moeda, saldo em `--text-display`, label "créditos disponíveis" e abaixo o histórico das últimas 3 movimentações (data, descrição, variação de crédito — ver exemplos na Seção 8.5). Em seguida, dois blocos lado a lado: à esquerda "Como ganhar créditos grátis" e à direita "Comprar créditos ou plano".

**Bloco esquerdo — Ganhar créditos:** lista com ícone de check:
- Cadastrar sua empresa → +10 créditos (uma única vez)
- Responder um tema → +5 créditos por tema
- Cada tema pode ser atualizado a cada 6 meses, gerando novos créditos

**Bloco direito — Planos e pacotes** (cards verticais com `--radius-lg`):

| Plano | Descrição | Preço | CTA |
|---|---|---|---|
| Pacote 50 créditos | Acesso avulso a temas específicos | R$ 500 | Comprar pacote |
| Assinatura Anual | Acesso ilimitado a todos os temas e dashboards | R$ 3.000/ano | Assinar agora |
| White-label | Para consultorias com múltiplos clientes | R$ 12.000/ano | Falar com comercial |

O plano **Assinatura Anual** tem badge "Mais popular" e borda em `--color-brand-primary`.

**Tabela de uso de créditos:** abaixo dos cards, tabela com colunas Ação / Créditos / Observação (espelha a Seção 5.1).

**Regras de negócio:**
- O saldo é atualizado em tempo real após qualquer transação.
- A compra de pacotes/assinatura abre um fluxo de pagamento externo (representar como modal de checkout mock).
- Assinantes anuais não consomem créditos para acessar dashboards.
- Créditos não expiram e não são transferíveis entre empresas.
- O histórico exibe no máximo os últimos 30 registros; link "Ver histórico completo" para lista paginada.
- White-label abre formulário de contato comercial, não checkout.
- Contratar Assinatura/White-label substitui o saldo do header por badge "Plano ativo".

---

## 5. Regras de Negócio Globais

### 5.1 Sistema de Créditos

| Evento | Variação | Observação |
|---|---|---|
| Cadastro da empresa | +10 | Único, no momento do cadastro |
| Preencher formulário de tema | +5 | Por tema, renovável a cada 6 meses |
| Consultar dashboard de um tema | −3 | Apenas na primeira consulta por tema |
| Consulta subsequente ao mesmo tema | 0 | Acesso gratuito após primeira consulta |
| Compra — Pacote 50 créditos | +50 | R$ 500 (compra avulsa) |
| Assinatura Anual | ilimitado | R$ 3.000/ano |

### 5.2 Privacidade e Anonimização
- Nenhum dado enviado é associado publicamente à empresa.
- Dados exibidos apenas de forma agregada (percentis, medianas, distribuições).
- Granularidade mínima de exibição: 5 empresas respondentes no recorte.
- Recortes que permitiriam identificação indireta (setor + porte + região muito restritos) são omitidos automaticamente.

### 5.3 Atualização de Dados
- Cada empresa pode atualizar seus dados por tema a cada 6 meses, recebendo +5 créditos novamente.
- O dashboard reflete os dados dos últimos 12 meses (janela deslizante); dados mais antigos são arquivados.

### 5.4 Validação de Formulários
- Valores numéricos validados contra faixas de consistência de mercado.
- Valores fora da faixa geram alerta não bloqueante (usuário pode confirmar e enviar).
- Dados inconsistentes são sinalizados internamente, sem bloquear o ganho de créditos.

### 5.5 Acesso e Sessão
- Sessão expira após 24h de inatividade (ou 30 dias com "Manter conectado").
- Um administrador principal por CNPJ; múltiplos usuários por empresa só no plano Assinatura Anual.
- Empresas sem créditos podem preencher formulários e ganhar créditos, mas não acessam dashboards.

---

## 6. Fluxos de Navegação

### 6.1 Fluxo de Novo Usuário (caminho feliz principal)
```
/cadastro → (sucesso, +10 créditos) → /app/temas
  → clica "Responder" em um card → /app/temas/:slug/formulario
  → envia formulário (+5 créditos) → /app/temas/:slug/sucesso
  → clica "Ver benchmark" (−3 créditos) → /app/temas/:slug/dashboard
  → aplica filtros e explora dados
```

### 6.2 Fluxo de Usuário Retornante
```
/login → /app/temas
  → filtra por categoria → seleciona tema já respondido
  → clica "Ver benchmark" → /app/temas/:slug/dashboard
```

### 6.3 Fluxo de Créditos Insuficientes
```
/app/temas (ou /sucesso) → clica "Ver benchmark" sem créditos
  → modal "Créditos insuficientes"
      título: "Você precisa de 3 créditos para ver este benchmark"
      CTA primário: "Responder outro tema e ganhar +5" → /app/temas
      CTA secundário: "Ver planos" → /app/planos
```

### 6.4 Fluxo de Compra de Créditos
```
/app/planos → escolhe "Pacote 50 créditos" ou "Assinar agora"
  → modal de checkout (mock) → confirmação → saldo atualizado no header
```

---

## 7. Estados de Interface

### 7.1 Estados do Card de Tema

| Estado | Badge | CTA | Visual |
|---|---|---|---|
| Não respondido | "Não respondido" (cinza) | "Responder · +5 créditos" (secundário) | Card padrão |
| Respondido, benchmark não acessado | "Respondido" (verde) | "Ver benchmark · 3 créditos" (primário) | Ícone check no canto |
| Respondido, benchmark acessado | "Respondido" (verde) | "Ver benchmark" (ghost) | Ícone check no canto |
| Bloqueado por créditos | "Não respondido" (cinza) | "Ver benchmark · 3 créditos" (desabilitado) | CTA com opacidade reduzida |

### 7.2 Estados do Dashboard

| Estado | Comportamento |
|---|---|
| Filtro com dados suficientes (≥5 empresas) | Exibe todos os gráficos e métricas |
| Filtro com dados insuficientes (<5 empresas) | Substitui gráficos pela mensagem de aviso |
| Empresa respondeu o tema | Exibe Seção 3 "Sua Posição no Mercado" |
| Empresa não respondeu o tema | Oculta Seção 3, exibe CTA "Responda para ver sua posição" |
| Dados >30 dias sem atualização | Badge muda de "Dados ao vivo" para "Atualizado há N dias" (amarelo) |

### 7.3 Estados do Indicador de Créditos (Header)

| Situação | Visual |
|---|---|
| Saldo ≥ 10 créditos | Ícone + número em `--color-brand-secondary` |
| Saldo entre 1–9 créditos | Ícone + número em `--color-warning` + tooltip "Créditos baixos" |
| Saldo = 0 | Ícone + "0" em `--color-error` + CTA "Ganhar créditos" |
| Plano Assinatura/White-label ativo | Substitui saldo por badge "Plano ativo" em `--color-success` |

---

## 8. Conteúdo e Dados de Exemplo (use estes valores no protótipo)

### 8.1 Os 22 Temas da Plataforma

> Renderize todos os 22 como cards no catálogo (`/app/temas`). A coluna "Ícone" refere-se a um ícone vetorial da biblioteca Lucide — **nunca um emoji**.

| # | Tema (título do card) | Categoria | Dado-chave (descrição do card) | Ícone (Lucide) |
|---|---|---|---|---|
| 1 | Benefícios — Além do Tradicional | Benefícios | % de empresas que oferecem cada benefício não-obrigatório e custo médio mensal | `gift` |
| 2 | Carreira Y, W, Squad e Outros Modelos | Cultura e Carreira | Modelo de estrutura vigente e % que adotam trilhas técnicas vs. gestão | `git-branch` |
| 3 | Deflatores — Variações Salariais por Região | Remuneração | % de variação salarial por região no último ciclo | `map` |
| 4 | Incentivos de Curto e Longo Prazo | Remuneração | % do salário-base como bônus e tipo de ILP mais adotado | `trending-up` |
| 5 | Gestão do Público Operacional | Operacional | Práticas de controle de ponto, banco de horas e variável | `factory` |
| 6 | Home Office e Horário Flexível | Cultura e Carreira | Modelo predominante e % de auxílio home office concedido | `house` |
| 7 | Indicadores de RH | Estrutura | Turnover voluntário, absenteísmo e span of control | `bar-chart-3` |
| 8 | Orçamento de RH | Estrutura | % da folha investido em RH e T&D per capita | `wallet` |
| 9 | Políticas de Remuneração | Remuneração | Frequência de revisão, critério principal e % médio de reajuste | `scale` |
| 10 | Gestão da Área Comercial | Operacional | Estrutura de comissionamento, gatilho de pagamento e aceleradores | `handshake` |
| 11 | Estagiários e Trainees | Cultura e Carreira | Valor da bolsa por nível e % de efetivação | `graduation-cap` |
| 12 | Reembolso de Km | Operacional | Valor do reembolso por km rodado (R$/km) por porte e setor | `car` |
| 13 | Concessão de Veículos | Benefícios | % ou valor de reajuste do veículo concedido e mix de categorias | `truck` |
| 14 | Despesas de Viagens | Operacional | Valor de diária por destino e limite de categoria hoteleira por nível | `plane` |
| 15 | Diversidade e Transparência Salarial | Diversidade | % de mulheres e negros em liderança e gap salarial por gênero | `users` |
| 16 | Estruturas Organizacionais | Estrutura | Número médio de níveis hierárquicos e amplitude de controle | `network` |
| 17 | Remuneração Executiva | Remuneração | Mix de remuneração total por nível (C-level, VP, Diretor) | `briefcase` |
| 18 | Engenheiros | Remuneração | Faixa salarial por senioridade e % com remuneração variável | `code` |
| 19 | PJ, Expatriados e Estatutários | Remuneração | Múltiplo sobre CLT para PJ e pacote de expatriados | `globe` |
| 20 | Treinamento e Desenvolvimento | Cultura e Carreira | Horas de treinamento per capita/ano e modalidades | `book-open` |
| 21 | Benefícios Flexíveis | Benefícios | % de adesão ao modelo flex e crédito mensal médio por colaborador | `shuffle` |
| 22 | Transferência de Colaboradores | Benefícios | % que concedem auxílio de transferência e valor médio do pacote | `package` |

### 8.2 Categorias para os chips de filtro

`Todos os temas` · `Remuneração` · `Benefícios` · `Cultura e Carreira` · `Estrutura` · `Diversidade` · `Operacional`

### 8.3 Formulário de exemplo — Tema "Reembolso de Km" (`/app/temas/reembolso-de-km/formulario`)

**Bloco de contexto:** "Coletamos como sua empresa reembolsa o uso de veículo próprio em deslocamentos. Leva ~5 minutos. Esses dados alimentam o benchmark de R$/km por setor, porte e região."

**Grupo 1 de 3 — Política de Reembolso**
- A empresa reembolsa km rodado em veículo próprio? *(toggle Sim/Não — obrigatório)*
- Valor do reembolso por km rodado *(numérico, unidade `R$/km` — obrigatório, ex.: `R$ 1,20`)*
- A política é igual para todos os níveis hierárquicos? *(radio: Sim, igual para todos / Não, varia por nível — obrigatório)*

**Grupo 2 de 3 — Critérios e Reajuste**
- Com que frequência o valor por km é reajustado? *(select: Mensal / Trimestral / Semestral / Anual / Sem periodicidade definida)*
- Qual o índice de reajuste utilizado? *(select múltiplo: IPCA / Preço do combustível / Tabela FIPE / Decisão interna / Outro)*
- % de reajuste aplicado no último ciclo *(numérico, unidade `%` — opcional, ex.: `8%`)*

**Grupo 3 de 3 — Cobertura**
- O reembolso inclui pedágio e estacionamento? *(toggle Sim/Não)*
- Existe teto mensal de reembolso por colaborador? *(numérico, unidade `R$` — opcional, ex.: `R$ 1.500`)*
- Nível de satisfação interna percebido com a política *(escala 0–100%)*

**Rodapé:** botão primário "Enviar e ganhar 5 créditos" + microcopy "Seus dados são anonimizados antes de qualquer uso".

### 8.4 Dashboard de exemplo — Tema "Reembolso de Km"

- **Cabeçalho:** "Reembolso de Km" · badge "Dados ao vivo" · "147 empresas participaram" · "Atualizado há 2 dias".
- **Seção 1 — Percentis (R$/km):** P25 = `R$ 0,92` · P50 = `R$ 1,15` · P75 = `R$ 1,48`.
- **Seção 2 — Distribuição:** histograma com faixas e % de empresas — `R$0,70–0,90` (12%) · `R$0,90–1,10` (28%) · `R$1,10–1,30` (34%) · `R$1,30–1,50` (18%) · `R$1,50+` (8%). Linha tracejada da empresa logada em `R$ 1,20`.
- **Seção 3 — Sua Posição:** "Sua empresa: R$ 1,20/km — você está no P62 do mercado." Gauge horizontal entre P25 e P75 com marcador em 62%.
- **Seção 4 — Recorte por Segmento (P50, R$/km):** Tecnologia `1,25` · Indústria `1,32` · Varejo `1,02` · Serviços `1,10` · Saúde `1,18` · Financeiro `1,40`.
- **Seção 5 — Tendência (P50 por ciclo):** 2024-S1 `1,02` → 2024-S2 `1,08` → 2025-S1 `1,12` → 2025-S2 `1,15`.

### 8.5 Saldo e histórico de exemplo (tela de Planos / header)

- **Saldo atual:** `15 créditos`
- **Histórico recente:**
  - 12/06/2026 — "Cadastro da empresa" — `+10`
  - 14/06/2026 — "Resposta: Reembolso de Km" — `+5`
  - 16/06/2026 — "Consulta: Reembolso de Km" — `−3`

### 8.6 Usuário de exemplo (para header e avatar)
- Nome: `Marina Costa` · Empresa: `Nimbus Tecnologia` · Segmento: Tecnologia · Porte: 101–500 · Região: Sudeste.

### 8.7 Consultor e clientes de exemplo (para Seção 9)
- **Consultor:** `Rafael Lima` · Consultoria `Vértice RH` · `rafael@verticerh.com.br`.
- **Empresas-cliente do consultor:**
  - `Nimbus Tecnologia` — CNPJ `12.345.678/0001-90` — Tecnologia / 101–500 / Sudeste — saldo `15 créditos` — status `Vinculada` — 1 formulário respondido.
  - `Aurora Indústria` — CNPJ `98.765.432/0001-21` — Indústria / 501–2.000 / Sul — saldo `2 créditos` — status `Vinculada` — 3 formulários respondidos.
  - `Lumen Varejo` — CNPJ `45.111.222/0001-33` — Varejo / Acima de 2.000 / Nordeste — saldo `0 créditos` — status `Convite pendente` — aguardando aceite.

---

## 9. FLUXO EXTRA — Persona Consultor (não substitui o fluxo da Empresa)

> Este é um fluxo **adicional**. Toda a experiência da persona Empresa (Seções 4.1–4.7) permanece inalterada. O Consultor é um intermediário que gerencia várias empresas-cliente, mas **nunca possui créditos próprios**: quem ganha e paga créditos é sempre a empresa.

### 9.0 Princípios da persona Consultor

- O Consultor **não tem saldo de créditos**. Não existe header de créditos para ele, nem tela de planos própria.
- O Consultor pode vincular **quantas empresas quiser**, sem custo.
- Cada empresa-cliente é a dona dos seus próprios dados e do seu saldo. O pagamento por créditos é **sempre da empresa**.
- O Consultor só consegue abrir o dashboard de uma empresa se **aquela empresa tiver créditos suficientes** — ao abrir, debita 3 créditos do saldo *dessa empresa* (mesma regra de 3 créditos da Seção 5.1). Se a empresa não tem saldo, o Consultor é bloqueado e vê a mensagem "Esta empresa não possui créditos suficientes. Apenas a própria empresa pode adquirir créditos.".
- Consultor e empresa podem se **desvincular** a qualquer momento (por qualquer um dos lados). Após o desvínculo, **nenhum dos dois enxerga os dados do outro**. Os dados já coletados **permanecem com a empresa** (ela é a dona); o consultor perde acesso a dashboards e histórico daquela empresa.

### 9.1 Cadastro — tipo "Consultor externo" (`/cadastro`)

Quando o seletor de tipo de conta está em **"Consultor externo"**, o formulário troca para:

**Campos (tipo "Consultor"):**
- Nome completo (texto, obrigatório) — ex.: `Rafael Lima`
- E-mail profissional (e-mail, obrigatório) — ex.: `rafael@verticerh.com.br`
- Nome da consultoria (texto, obrigatório) — ex.: `Vértice RH`
- CNPJ da consultoria (texto com máscara, opcional)
- Senha / Confirmação de senha

**CTA:** botão primário "Criar conta de consultor".
**Diferenças visíveis:** sem menção a "10 créditos" (consultor não tem créditos); o painel lateral troca o 3º benefício por "Gerencie quantas empresas-cliente quiser".
**Ao concluir:** navega para `/consultor/clientes`.

### 9.2 Painel do Consultor — Lista de Clientes (`/consultor/clientes`) — TELA PRINCIPAL DO CONSULTOR

**Prompt de tela:**
> Crie o painel principal do Consultor na Athon. Topbar fixa com logomarca à esquerda e, à direita, o avatar do consultor com o nome da consultoria (Vértice RH) — **sem indicador de créditos** (consultor não tem créditos). Header de página com título "Minhas empresas-cliente" e subtítulo "Cadastre empresas, escolha formulários e acompanhe os benchmarks delas.". À direita do header, botão primário "Cadastrar nova empresa" (navega para `/consultor/clientes/novo`). Faixa de resumo com mini-indicadores: "N empresas vinculadas", "M convites pendentes". Abaixo, um grid responsivo de **cards de empresa-cliente** (use os exemplos da Seção 8.7).

**Anatomia do Card de Empresa-Cliente:**
- Nome da empresa (`--text-heading-2`) + CNPJ em `--text-caption`
- Tags: segmento · porte · região
- **Indicador de créditos da empresa** (badge de crédito mostrando o saldo daquela empresa — ex.: "15 créditos") — leitura apenas; o consultor não compra por ela
- Status badge: "Vinculada" (verde) · "Convite pendente" (amarelo) · "Desvinculada" (cinza)
- Linha de progresso: "X de 22 formulários respondidos"
- No canto superior direito, um **botão three-dots (`more-vertical`)** que abre um menu de ações:
  - "Ver dashboards da empresa" → abre o catálogo de dashboards daquela empresa (consome créditos *da empresa* ao abrir cada um; bloqueado se saldo insuficiente)
  - "Selecionar e enviar formulários" → `/consultor/clientes/:cnpj/envio`
  - "Reenviar convite" (apenas se status = Convite pendente)
  - "Desvincular empresa" (ação destrutiva, em `--color-error`)

**Regras de negócio:**
- Card com "Convite pendente" tem aparência levemente esmaecida e não permite ver dashboards até o aceite.
- "Ver dashboards da empresa" leva à mesma experiência de dashboard da Seção 4.6, porém em contexto do consultor: cada abertura debita 3 créditos *do saldo da empresa*; se saldo < 3, exibir o bloqueio descrito em 9.0.
- "Desvincular empresa" abre modal de confirmação (ver 9.6).

### 9.3 Cadastrar Nova Empresa-Cliente (`/consultor/clientes/novo`)

**Prompt de tela:**
> Crie uma tela/modal de cadastro de empresa-cliente pelo consultor. Layout de coluna única, largura máxima de 560px. Título "Cadastrar nova empresa" e subtítulo "A empresa receberá um e-mail para aceitar o vínculo e acessar a plataforma.".

**Campos:**
- CNPJ da empresa (máscara `00.000.000/0000-00`, obrigatório, validado)
- E-mail do responsável pela empresa (e-mail corporativo, obrigatório)
- Nome da empresa (texto, opcional — pode ser preenchido pela empresa no aceite)

**CTA:** botão primário "Enviar convite".

**Regras de negócio:**
- Ao enviar, cria a empresa com status **"Convite pendente"** e dispara um e-mail de aceite ao responsável (ver 9.4).
- Se o CNPJ já tiver conta ativa na Athon, vincular ao convite existente em vez de duplicar (mensagem "Esta empresa já está na Athon — enviaremos um pedido de vínculo.").
- Após enviar, retorna para `/consultor/clientes` com o novo card em "Convite pendente" e toast "Convite enviado para [e-mail]".

### 9.4 Aceite da Empresa Convidada (e-mail → ativação)

> Representar como uma tela de aceite acessada pelo link do e-mail (`/aceite/:token`), sem login prévio.

**Prompt de tela:**
> Crie a tela de aceite de vínculo. Card centralizado com logomarca, título "A consultoria Vértice RH convidou sua empresa para a Athon", e um resumo: CNPJ, e-mail responsável e o que o vínculo permite ("O consultor poderá selecionar formulários para você responder e visualizar os benchmarks que sua empresa desbloquear."). Dois botões: primário "Aceitar e acessar a plataforma" e ghost "Recusar convite".

**Regras de negócio:**
- Ao **aceitar**: a empresa entra na base de cadastro com status "Vinculada", ganha os **+10 créditos de boas-vindas** (regra da Seção 5.1) e o sistema gera uma **senha temporária** enviada ao e-mail do responsável, com aviso "Você receberá uma senha temporária por e-mail para acessar sua conta.". A empresa passa a poder entrar normalmente em `/login` e trocar a senha no primeiro acesso.
- Ao **recusar**: o card do consultor passa a status "Recusado" e nenhum vínculo é criado.
- O token de aceite expira em 7 dias; expirado, oferece "Reenviar convite".

### 9.5 Selecionar e Enviar Formulários ao Cliente (`/consultor/clientes/:cnpj/envio`)

**Prompt de tela:**
> Crie a tela onde o consultor seleciona quais formulários quer que a empresa-cliente responda. Breadcrumb "Clientes → [Nome da Empresa] → Enviar formulários". Lista dos 22 temas (Seção 8.1) com um **checkbox** em cada linha (ícone + título + categoria + dado-chave). Topo com busca e os mesmos chips de categoria do catálogo para filtrar a lista. Rodapé fixo com contagem "N formulários selecionados" e botão primário "Enviar para [Nome da Empresa]". Campo opcional de mensagem personalizada para incluir no e-mail.

**Regras de negócio:**
- Ao enviar, dispara um e-mail ao responsável da empresa contendo **um link público + uma chave de acesso** que dá acesso apenas aos formulários selecionados, **sem necessidade de login** (fluxo 9.7).
- Temas que a empresa já respondeu aparecem marcados como "Já respondido" e podem ser reenviados para atualização (a cada 6 meses, regra 5.3).
- Após enviar: toast "Formulários enviados para [e-mail]" e retorno ao painel.

### 9.6 Desvincular (dos dois lados)

**No painel do Consultor** (`/consultor/clientes`, menu three-dots → "Desvincular empresa"):
> Modal de confirmação: "Desvincular [Empresa]? Você perderá o acesso aos dashboards e ao histórico desta empresa. Os dados já enviados permanecem com a empresa." Botões: "Desvincular" (`--color-error`) / "Cancelar".

**No painel da Empresa** (`/app/consultores`, ver tela 4.8):
> Mesmo padrão: a empresa pode remover um consultor externo, cortando o acesso dele aos seus dashboards e histórico.

**Regras de negócio (ambos os lados):**
- Após o desvínculo, **nenhum dos dois enxerga dados do outro**: o consultor some da lista de consultores da empresa e a empresa some do painel do consultor (ou aparece como "Desvinculada").
- Os dados/respostas vinculados ao CNPJ **permanecem com a empresa** — ela continua acessando seus próprios dashboards normalmente.
- O dado anonimizado já enviado continua compondo o benchmark agregado do mercado (não é removido dos percentis).

### 9.7 Fluxo Público de Resposta — sem login (`/responder/:chave`)

> O cliente clica no link do e-mail e acessa **apenas os formulários selecionados pelo consultor**, sem tela de login. A chave vincula a resposta ao CNPJ da empresa.

**Tela 1 — Lista de formulários (`/responder/:chave`):**
> Crie uma tela pública (sem topbar de app logado) com a logomarca Athon, um cabeçalho "Formulários solicitados por Vértice RH para [Empresa]", subtítulo "Responda abaixo. Suas respostas ficam vinculadas à sua empresa (CNPJ) e poderão ser acessadas por você depois.". Lista de cards de formulário selecionados, cada um com título, tempo estimado e botão "Responder". Indicador de progresso "X de N respondidos".

**Tela 2 — Formulário público (`/responder/:chave/:slug`):**
> Reutiliza exatamente o layout de formulário da Seção 4.4 e os campos de exemplo (8.3), **mas sem o header de créditos** e sem exigir login. Rodapé: botão "Enviar resposta" (sem o texto "ganhar 5 créditos" exposto ao respondente — os +5 são creditados no saldo da empresa nos bastidores). Microcopy: "Vinculado ao CNPJ [12.345.678/0001-90] · suas respostas são anonimizadas no benchmark".

**Regras de negócio:**
- A chave de acesso identifica univocamente a empresa (CNPJ) e o conjunto de formulários liberados. Não dá acesso a dashboards nem a outros temas.
- Cada formulário respondido por esse fluxo credita **+5 créditos no saldo da empresa** (não do consultor) e vincula a resposta ao CNPJ.
- A empresa, ao logar depois em `/app`, encontra essas respostas já registradas como suas (mesmos dados, mesmo CNPJ).
- A chave expira após o prazo definido ou quando todos os formulários liberados forem respondidos; expirada, exibe "Este link expirou. Solicite um novo ao seu consultor.".

### 9.8 Fluxos de Navegação — Consultor (resumo)

```
/cadastro (toggle "Consultor") → /consultor/clientes
  → "Cadastrar nova empresa" → /consultor/clientes/novo → envia convite
       → (e-mail) empresa abre /aceite/:token → "Aceitar"
            → empresa ganha +10 créditos + senha temporária por e-mail
            → card vira "Vinculada"
  → menu do card → "Selecionar e enviar formulários" → /consultor/clientes/:cnpj/envio
       → (e-mail) cliente abre /responder/:chave (SEM login)
            → responde formulários → +5 créditos no saldo DA EMPRESA, vinculado ao CNPJ
  → menu do card → "Ver dashboards da empresa"
       → se empresa tem ≥3 créditos: abre dashboard (debita 3 da empresa)
       → se empresa tem <3 créditos: bloqueio "apenas a empresa pode comprar créditos"
  → menu do card → "Desvincular empresa" → confirmação → acesso mútuo cortado
```

### 9.9 Estados — Card de Empresa-Cliente (painel do consultor)

| Estado | Status badge | three-dots habilita | Visual |
|---|---|---|---|
| Convite pendente | "Convite pendente" (amarelo) | Reenviar convite / Desvincular | Card esmaecido, sem ver dashboards |
| Vinculada, com créditos (≥3) | "Vinculada" (verde) | Ver dashboards / Enviar formulários / Desvincular | Card normal, badge de saldo neutro |
| Vinculada, sem créditos (<3) | "Vinculada" (verde) | Enviar formulários / Desvincular; "Ver dashboards" bloqueado | Badge de saldo em `--color-warning` + tooltip de bloqueio |
| Desvinculada | "Desvinculada" (cinza) | (apenas remover do painel) | Card inativo, sem acesso a dados |

---

## 4.8 Empresa — Consultores Vinculados (`/app/consultores`)

**Prompt de tela:**
> Crie a tela onde a **empresa** gerencia consultores externos com acesso à sua conta. Acessível pelo menu da conta no header do app. Header "Consultores vinculados" e subtítulo "Profissionais externos que podem solicitar formulários e ver seus benchmarks.". Lista de cards de consultor: nome, consultoria, e-mail, data de vínculo, e um botão "Desvincular" (`--color-error`). Se não houver consultores, estado vazio com ícone e texto "Nenhum consultor vinculado.".

**Regras de negócio:**
- "Desvincular" abre o modal da Seção 9.6 (lado empresa): corta o acesso do consultor aos dashboards e histórico da empresa.
- Os dados permanecem com a empresa; o desvínculo é imediato e bilateral.

---

*Athon — Especificação de Design v3.0 · inclui persona Consultor · pronta para geração de protótipo*
