# Custos do MVP — Athon

Estimativa de custos para o desenvolvimento e operação da plataforma.

**Arquitetura:** Frontend SPA (React + Vite, servido como estáticos via CDN) + Backend API separado (Node/Express ou Python/FastAPI) + Banco de dados.

---

## 1. Desenvolvimento (custo único)

Base: dev **pleno** a ~R$ 8,5k/mês de salário.

| Modo | Equipe | Prazo | Custo |
|---|---|---|---|
| **Enxuto** | 2 devs PJ/freelancer (sem encargos) | 3 meses | **~R$ 51k** |
| **Time próprio** | 2 devs CLT (encargos ~70%) | 3 meses | **~R$ 87k** |

> CLT com encargos (INSS, FGTS, férias, 13º): R$ 8,5k × 1,7 ≈ R$ 14,5k/dev/mês.
> O design system já existe — economia em UI.

---

## 2. Infraestrutura (recorrente)

### Versão Básica — Static Host + Supabase
SPA estático em CDN + backend gerenciado (até ~500 empresas).

| Serviço | Função | Custo/mês |
|---|---|---|
| Vercel / Netlify / Cloudflare Pages | Hospedagem do SPA estático + CDN | R$ 0–110 |
| Supabase Pro | DB + Auth + Storage + API | ~R$ 140 |
| Resend | E-mail transacional | R$ 0–60 |
| Domínio | `.com.br` | ~R$ 4 |
| **Total** | | **~R$ 150–310/mês (~R$ 2–4k/ano)** |

**Prós:** zero DevOps, SPA estático custa quase nada (cabe no free tier). **Contras:** lock-in, menos controle.

> Como o frontend é SPA estático, a hospedagem dele é praticamente gratuita — o custo concentra-se no backend/DB.

### Versão Robusta — AWS
SPA estático no S3/CloudFront + API em container (produção, SLA, white-label).

| Etapa | Configuração | Custo/mês | Custo/ano |
|---|---|---|---|
| **AWS MVP** | S3+CloudFront (SPA) + ECS Fargate (API) + RDS Single-AZ | ~R$ 540 | ~R$ 6.5k |
| **AWS Escalado** | + Multi-AZ + Redis + WAF (200+ empresas) | ~R$ 2.000 | ~R$ 24k |

O SPA vai para **S3 + CloudFront** (estático, barato); só a **API** roda em Fargate.

**Prós:** controle total, LGPD, alta disponibilidade. **Contras:** exige DevOps.

---

## 3. Ferramentas de IA

A IA pode (a) acelerar o desenvolvimento e (b) ser embutida no produto (validação/anonimização de dados, insights de benchmark).

### IA para desenvolvimento

| Ferramenta | Uso | Custo/mês |
|---|---|---|
| GitHub Copilot | Autocomplete de código | ~R$ 60/dev |
| Claude / ChatGPT | Pair programming, debug | ~R$ 110/dev |
| Cursor / Claude Code | IDE com IA | ~R$ 110/dev |
| **Total (2 devs)** | | **~R$ 300–500/mês** |

> Acelera o dev em 20–40% — reduz custo total de desenvolvimento.

### IA embutida no produto (API)

Para validação de dados, geração de insights e resumos de benchmark.

| Modelo | Uso recomendado | Custo aprox. |
|---|---|---|
| Claude Haiku 4.5 | Validação/anonimização em volume | ~US$1 / milhão tokens entrada |
| Claude Sonnet 4.6 | Insights e análises complexas | ~US$3 / milhão tokens entrada |

**Estimativa MVP (baixo volume):** ~US$30–80/mês (~R$ 170–460/mês).
Escala conforme o número de consultas — pode ser repassado via créditos.

---

## 4. Plataforma de Pagamentos

Necessária para cobrar assinaturas (R$ 3k/ano), pacotes de créditos (R$ 500) e white-label (R$ 12k/ano). **Custo variável** — cobra-se % por transação, sem mensalidade.

| Plataforma | Taxa (cartão) | Boleto / Pix | Observação |
|---|---|---|---|
| **Stripe** | ~3.99% + R$ 0,39 | Pix ~1.19% | Melhor para SaaS/assinaturas, billing recorrente nativo |
| **Pagar.me / Mercado Pago** | ~3.49% + R$ 0,49 | Boleto R$ 3,49 · Pix ~0.99% | Forte no Brasil, boleto e Pix nativos |
| **Asaas / Iugu** | ~2.99–3.49% | Pix/boleto baratos | Focado em cobrança recorrente B2B |

**Estimativa de custo** (sobre a receita, não fixo):
- Meta Ano 1: R$ 600k de receita → taxa média ~3,5% = **~R$ 21k/ano** em taxas.
- Pix reduz bastante (taxa ~1%): incentivar Pix para assinaturas anuais corta o custo pela metade.

> É custo proporcional à receita — só existe quando há venda. Implementação: ~20–40h de dev (webhook + reconciliação de créditos).

---

## 5. Resumo Consolidado

| Cenário | Dev (único) | Infra/ano | IA/ano | Pagamentos/ano* | **Total Ano 1** |
|---|---|---|---|---|---|
| **Básico** (PJ + static host + IA dev) | R$ 51k | R$ 2–4k | R$ 4–6k | ~R$ 21k | **~R$ 78–82k** |
| **Robusto** (CLT + AWS escalado + IA produto) | R$ 87k | R$ 24k | R$ 6–12k | ~R$ 21k | **~R$ 138–144k** |

\* Taxas de pagamento são variáveis (~3,5% da receita); valor estimado sobre a meta de R$ 600k/ano. Só ocorre com venda efetiva — se autofinancia.

---

## 6. Recomendação por fase

| Fase | Stack | Infra/mês |
|---|---|---|
| Protótipo / Hackathon | Static host + Supabase (free) | R$ 0 |
| MVP (0–50 empresas) | Static host + Supabase Pro | ~R$ 150–310 |
| Tração (50–200) | AWS MVP | ~R$ 540 |
| Escala (200+) | AWS completo | ~R$ 2k |

**Caminho recomendado:** começar simples (SPA estático + Supabase + IA via API), migrar para AWS quando o MRR justificar. A migração não exige reescrever código — o SPA estático já vai para S3+CloudFront e o PostgreSQL migra direto para o RDS; só a API precisa virar container no Fargate.

---

## 7. Resumo Final — Valor Total

Visão geral de tudo (frontend SPA + backend + infra + IA + pagamentos) para o **Ano 1**.

Base: dev pleno ~R$ 8,5k/mês · equipe de 2 devs · MVP em 3 meses.

| Categoria | Básico | Robusto |
|---|---|---|
| Desenvolvimento (2 devs, 3 meses) | R$ 51k | R$ 87k |
| Infraestrutura (12 meses) | R$ 2–4k | R$ 24k |
| Ferramentas de IA | R$ 4–6k | R$ 6–12k |
| Pagamentos (~3,5% da receita)* | R$ 21k | R$ 21k |
| **TOTAL ANO 1** | **~R$ 78–82k** | **~R$ 138–144k** |

### 💰 Valor total recomendado

> **MVP enxuto (cenário Básico): ~R$ 78–82k no Ano 1**
> Cobre todo o desenvolvimento, infra, IA e pagamentos para validar o produto com até ~500 empresas.

\* Pagamentos são **custo variável** sobre a receita (meta R$ 600k/ano) — só ocorrem com venda efetiva, logo se autofinanciam. Sem considerá-los, o **custo de entrada cai para ~R$ 57–61k**.

**Em resumo:**
- **Para começar (sem taxas de venda):** R$ 57–61k
- **Ano 1 completo (com pagamentos):** R$ 78–82k
- **Versão robusta AWS (escala):** R$ 138–144k

---

*Athon — Transformando dados em decisões de RH mais inteligentes*
