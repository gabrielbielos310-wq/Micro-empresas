<!-- coderabbit-ai-generated:v1 -->

# Configuração do AI Gateway

## Pré-requisitos

Node.js 24 ou superior e npm. Execute `npm ci --ignore-scripts` na raiz. As versões estão fixadas em package-lock.json. Não é necessário configurar Vercel, Docker ou credenciais para os testes com MockModel.

## Variáveis do servidor

| Variável | Uso |
| --- | --- |
| AI_GATEWAY_API_KEY | Chave do Vercel AI Gateway; obrigatória para execução real. |
| JARVIS_MODEL | ID `provedor/modelo` disponível no catálogo do Gateway; não há modelo padrão. |
| JARVIS_ADMIN_ID | Identidade administrativa estável provisionada no servidor. |
| JARVIS_ADMIN_TOKEN | Token aleatório secreto, com pelo menos 32 caracteres. |

Copie `.env.example` para `services/eve/.env.local`, preencha localmente e mantenha fora do Git. Não use prefixos NEXT_PUBLIC_. Não cole credenciais em conversas ou logs. A Eve carrega o ambiente de seu diretório de aplicação. Alternativamente, injete variáveis pelo ambiente do processo.

## Comandos

- `npm test`: testes locais com o mockModel oficial da Eve, incluindo servidor descartável.
- `npm run typecheck`: verificação TypeScript.
- `npm run build`: build Node da Eve.
- `npm run dev`: servidor local da Eve; use o cliente `JarvisSessions` no servidor com token administrativo. O terminal padrão da Eve não possui automaticamente esse token.

O módulo JarvisSessions permite `create()`, `attach(id)` e `execute(session, mensagem, true)` para solicitar o schema de plano. O handle oficial permite `snapshot()`, `cancel()` e `end()`; essas operações também passam pela verificação de proprietário no servidor. Não exponha o token diretamente ao navegador. O painel e uma API própria para seus usuários ainda não existem.

## Validação externa pendente

Nenhuma geração real pelo Gateway foi realizada. É necessário configurar uma chave válida, escolher modelo disponível e autorizar consumo. Preços variam por modelo e uso; não foi contratada capacidade nem efetuado pagamento. Consultar o [catálogo oficial](https://vercel.com/ai-gateway/models) e [documentação do Gateway](https://vercel.com/docs/ai-gateway) antes do teste. MockModel não comprova conectividade nem faturamento.
