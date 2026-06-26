# Wallacy Corretor — CRM para Corretor de Imóveis

Documentação do projeto. Estado atual: **protótipo navegável aprovado para apresentação**.
Objetivo: validar a ideia com o corretor **Wallacy (Ubá-MG)** antes de construir o MVP real.
Visão de longo prazo: transformar em **produto SaaS** para corretores autônomos da região.

> **Status:** aguardando aprovação do Wallacy. Quando ele topar, seguir para a seção
> [Próximos passos (quando aprovado)](#-próximos-passos-quando-aprovado).

---

## 🔗 Links publicados (GitHub Pages)

| O quê | Link |
|---|---|
| **Protótipo** (app navegável) | https://glaucoaraujop-sketch.github.io/wallacy-corretor/ |
| **Calculadora de lucro** (unit economics) | https://glaucoaraujop-sketch.github.io/wallacy-corretor/calculadora.html |
| **Proposta comercial** (web) | https://glaucoaraujop-sketch.github.io/wallacy-corretor/proposta.html |
| Repositório | https://github.com/glaucoaraujop-sketch/wallacy-corretor |

Conta GitHub: `glaucoaraujop-sketch`. Repositório **público** (exigência do GitHub Pages gratuito).

---

## 📁 Arquivos do projeto

| Arquivo | Descrição |
|---|---|
| `index.html` | **Protótipo** completo (HTML + Tailwind via CDN + JS puro). Tudo num arquivo, sem build. |
| `calculadora.html` | Calculadora interativa de unit economics (margem, lucro, ponto de equilíbrio). |
| `proposta.html` | Proposta comercial (5 páginas, formatada para A4/impressão). |
| `Proposta_Wallacy_Corretor.pdf` | PDF gerado a partir do `proposta.html` (para enviar pronto). |
| `Calculadora_Lucro_Wallacy.xlsx` | Planilha Excel com fórmulas vivas (edite as células verdes). |
| `README.md` | Este documento. |

**Stack do protótipo:** HTML único + [Tailwind CSS](https://cdn.tailwindcss.com) (CDN) + [Lucide icons](https://unpkg.com/lucide) (CDN) + JavaScript puro. Sem backend, sem instalação. Dados fictícios embutidos no próprio JS.

---

## 🎯 O conceito

Sistema mobile-first para o corretor de rua, com foco em resolver os **gargalos reais**:

1. **Lead esfria** antes de ser respondido (cai no WhatsApp misturado com a vida pessoal).
2. **Follow-up esquecido** — 60-80 clientes "na cabeça".
3. **Match manual** — não lembra quem procurava o imóvel que acabou de entrar.
4. **Retrabalho** — cadastra o mesmo imóvel em vários canais.
5. **Documentação/prazos** — um documento atrasado derruba o negócio.
6. **Sem números** — não sabe qual canal traz cliente que fecha nem a comissão prevista.

**Os 3 diferenciais que vendem:**
- **Match automático** imóvel ↔ cliente (nos dois sentidos).
- **Nenhum lead esfria** (funil + alertas).
- **Feito pra rua** (celular, simples, em PT-BR, realidade de Ubá).

---

## 📱 Telas do protótipo (o que já está demonstrado)

Navegação por barra inferior: **Início · Funil · Imóveis · Envios · Clientes · Negócios**.

- **Início** — banner de "leads aguardando resposta", KPIs (visitas, propostas, clientes, comissão prevista), tarefas do dia e o card de **match automático** (cenário da Larissa, apto até R$ 300 mil).
- **Funil** — kanban (Novo → Contatado → Visita → Proposta → Fechado), com origem de cada lead (WhatsApp/ZAP/Insta/Indicação).
- **Imóveis** — cards com selo de publicação (ZAP/Viva/Insta) e badge de match. Botão **"Ver clientes que procuram isso"** → painel com % de compatibilidade e envio por cliente.
- **Envios (WhatsApp)** — **modelo Click-to-WhatsApp**: lista de mensagens prontas (apontamentos). Cada uma abre uma prévia da mensagem + botão **"Abrir conversa no WhatsApp"**. Banner reforça: *"Seu WhatsApp continua no seu celular, nada fica conectado."*
- **Clientes** — cada cliente com **intenção de compra** (perfil de busca em chips) e status. Botão **"Registrar intenção de compra"** → formulário → **tela de confirmação que já mostra o imóvel que bate (97%)** pronto pra enviar.
- **Negócios** — checklist da proposta à escritura, com barra de progresso e alerta de documento atrasado.

**Fluxo "uau" para a demo ao vivo:**
Clientes → *Registrar intenção de compra* → *Salvar* → aparece na hora o imóvel que bate (97%) → *Enviar no WhatsApp*.

---

## ✅ Decisões de produto (já tomadas)

| Tema | Decisão |
|---|---|
| **Cliente-alvo do piloto** | 1 corretor autônomo: **Wallacy**, Ubá-MG. |
| **Identidade** | Nome "Wallacy Corretor", cor verde (brand/emerald), mobile-first. |
| **Dados de exemplo** | Bairros e preços de Ubá (Bom Pastor, Centro, San Raphael, Eldorado, etc.). |
| **WhatsApp (modelo principal)** | **Click-to-WhatsApp**: o sistema prepara a mensagem e abre o app nativo; **não conecta** no número, sem risco de banimento, sem custo por mensagem. Resolve o medo dele de "perder o WhatsApp". |
| **WhatsApp (upgrade futuro)** | Integração completa (API oficial) com histórico no sistema — fica no plano Profissional. |
| **Modelo de negócio** | SaaS por assinatura. Wallacy entra como **piloto** (uso gratuito por alguns meses em troca de feedback + virar case). |

### Estratégia de WhatsApp — os 3 caminhos (referência)

1. **API Oficial (Meta/Cloud API)** — oficial e segura, mas o número **sai do app nativo** (não dá pra usar nos dois ao mesmo tempo). Cobra por mensagem iniciada pelo corretor; **responder cliente em até 24h é grátis**.
2. **Número comercial dedicado** — segundo número só pro negócio na API; o WhatsApp pessoal fica intocado. (Recomendado quando ele quiser integração de verdade.)
3. **Click-to-WhatsApp (escolhido para o MVP)** — não conecta nada; abre o app nativo com a mensagem pronta. Zero risco, zero custo de mensagem, mais barato/rápido de construir. **Trade-off:** o histórico das conversas não sincroniza para dentro do sistema (compensado movendo o card no funil / botão "registrar contato").

---

## 💰 Precificação

### Planos (preço ao cliente final)

| Plano | Preço/mês | Inclui |
|---|---|---|
| **Essencial** | **R$ 147** | Funil, clientes, imóveis, match, **Envio no WhatsApp (1 toque / Click-to-WhatsApp)**, agenda. |
| **Profissional** ⭐ | **R$ 237** | Tudo do Essencial + **WhatsApp integrado + histórico** + publicação nos portais + relatórios + 500 disparos/mês inclusos. |
| **Imobiliária** | **R$ 397** | Tudo do Profissional + equipe/divisão de carteira + R$ 49 por corretor extra. |

Referência de mercado (corretor autônomo): R$ 80–250/mês (Tecimob, Jetimob, Imoview, Vista).
Sugestão tática: **1º mês grátis** para testar com a carteira real.

**Argumento de ROI:** comissão numa venda de R$ 400 mil passa de R$ 10 mil. O Profissional custa R$ 2.844/ano — **uma venda a mais no ano já paga 3x**.

### Unit economics (cenário-base na calculadora)

Premissas: R$ 237/mês · 50 assinantes · 120 disparos/cliente · R$ 0,12/disparo · infra R$ 4 · taxa 5% · fixo R$ 500.

| Métrica | Valor aproximado |
|---|---|
| Custo por cliente | ~R$ 30 |
| **Margem por cliente** | **~R$ 207 (≈87%)** |
| Lucro líquido / mês | **~R$ 9,8 mil** |
| Lucro líquido / ano | **~R$ 118 mil** |
| Ponto de equilíbrio | **~3 assinantes** |

> Custo de WhatsApp é pequeno porque responder cliente (em 24h) é grátis; o custo só incide em disparos iniciados pelo corretor. Dá pra **embutir no plano** com folga e ainda ter espaço para desconto de lançamento (a R$ 147 a margem segue ~80%).

**Quem paga o WhatsApp:** modelo recomendado = você (plataforma) paga a Meta e **embute no plano** com uma franquia mensal de disparos (ex: 500 inclusos, excedente R$ 0,15). No MVP com Click-to-WhatsApp, esse custo nem existe.

---

## 🚀 Próximos passos (quando aprovado)

Roteiro para sair do protótipo e construir o **MVP funcional de verdade**.

### Stack sugerida
- **Frontend:** evoluir o protótipo para um app web real (React/Next.js ou manter HTML/Tailwind + Alpine para simplicidade). PWA para "instalar" no celular.
- **Backend/Banco:** **Supabase** (Postgres + Auth + Storage + Realtime). Já há plugin/credenciais no ambiente.
- **WhatsApp (MVP):** Click-to-WhatsApp via link `wa.me` / deep link (sem API, sem custo).
- **Hospedagem:** Vercel/Netlify (frontend) + Supabase (dados). Domínio próprio (~R$ 40/ano).

### Modelo de dados inicial (Supabase)
- `clientes` (nome, contato, status, origem)
- `intencoes_compra` (cliente_id, tipo, dormitórios, bairros, valor_min, valor_max) → base do match
- `imoveis` (tipo, bairro, preço, m², dormitórios, vagas, fotos, código, canais publicados)
- `leads` / `funil` (cliente_id, etapa, origem, timestamps)
- `negocios` (imovel_id, cliente_id, valor, comissão, etapa, checklist de documentos com prazos)
- `tarefas` / `follow_ups` (cliente_id, data, tipo, status)
- **Match:** query/trigger que cruza `imoveis` novos com `intencoes_compra` (tipo + bairro + faixa de preço + dormitórios) e gera apontamentos.

### Fases sugeridas do MVP
1. **Fundação** — auth (login do Wallacy), modelo de dados, deploy.
2. **Núcleo** — CRUD de clientes (com intenção de compra) + imóveis + funil.
3. **Match + Click-to-WhatsApp** — o coração: apontamentos automáticos e envio com mensagem pronta. (É o diferencial; priorizar.)
4. **Agenda & follow-ups** — lembretes (integração Google Calendar opcional).
5. **Negócios** — checklist de documentos com prazos/alertas.
6. **Painel** — métricas (conversão por etapa, por canal, comissão prevista).

### Custos recorrentes esperados (operação)
- Supabase/hospedagem: R$ 0–150/mês no começo (escala com uso).
- WhatsApp: **R$ 0** no MVP (Click-to-WhatsApp). Só há custo se migrar para API oficial.
- Domínio: ~R$ 40/ano.

### Caminho de monetização
1. Wallacy como **piloto gratuito** → feedback + depoimento/case.
2. Ajustar o produto ao uso real.
3. Vender o SaaS para outros corretores da região (Ubá + Zona da Mata).
   - Conta de padaria: **50 corretores × R$ 150/mês ≈ R$ 7.500/mês** recorrente.

---

## 🛠️ Como rodar / editar / republicar

**Rodar local:** basta abrir os arquivos `.html` no navegador (duplo clique). Não precisa de servidor.

**Editar:** os arquivos são autocontidos. No `index.html`, os dados fictícios ficam no bloco
`/* ===================== DADOS FICTÍCIOS ===================== */` (arrays `leads`, `clientes`,
`imoveis`, `matchClientes`, `envios`, `agenda`, `negocios`).

**Regerar o PDF da proposta** (precisa do Google Chrome instalado):
```bash
cd ~/Projects/chave-crm
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="Proposta_Wallacy_Corretor.pdf" \
  "file://$(pwd)/proposta.html"
```

**Republicar (após editar):** qualquer alteração vai ao ar em ~1 min após:
```bash
cd ~/Projects/chave-crm
git add -A && git commit -m "ajustes" && git push
```

---

## 📜 Histórico de versões

| Data | Commit | Mudança |
|---|---|---|
| 25/06 16:28 | `548d8af` | Protótipo inicial (CRM, telas base). |
| 25/06 21:26 | `f6d490b` | Calculadora de unit economics (HTML + xlsx). |
| 25/06 21:33 | `6b6381e` | Proposta comercial (HTML + PDF 5 páginas). |
| 25/06 22:10 | `e7f6dee` | Click-to-WhatsApp + intenção de compra/match + valores 147/237/397. |
| 25/06 22:24 | `18cb938` | Tela de confirmação após salvar intenção (match imediato). |

---

*Documento mantido por Glauco Araújo · glaucoaraujop@gmail.com*
