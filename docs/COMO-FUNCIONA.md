# Como funciona (em linguagem simples)

O Hermes Imobiliária liga o **Instagram** da sua imobiliária, o **Zernio** e o seu **agente Hermes**, com o **Telegram** como seu painel. A diferença para os outros: aqui o agente trabalha como um **esquadrão**, seguindo o fluxo **captar → qualificar → agendar visita**.

## As duas demonstrações

### Demo 1 — Posts com imagem
Você pede um post pelo Telegram (ex.: "crie um post do apartamento de 2 quartos no Jardim X"). O agente escreve a legenda, gera a imagem e mostra para você aprovar. Aprovou, publica no Instagram pelo Zernio.

### Demo 2 — Atendimento automático (esquadrão)
Quando alguém comenta ou manda DM, o Zernio avisa o agente na hora (*webhook*). O esquadrão capta, **qualifica** o lead (orçamento, região, comprar/alugar, prazo) e oferece **agendar a visita**, sempre te avisando no Telegram.

```
Comentário/DM no Instagram
        │
        ▼
     Zernio  ──(internet, HTTPS)──►  seu agente Hermes  ──►  esquadrão (captar/qualificar/agendar)
        ▲                                  │
        │                                  ├─ responde no Instagram
        └────────── publica posts ◄────────┤
                                           └─ te avisa no Telegram (lead qualificado / quer visitar)
```

## O que é o "esquadrão"
É a parte que organiza o atendimento em etapas (captar, qualificar, agendar). O assistente instala e conecta isso **sozinho** durante a instalação — você nunca precisa configurar a tecnologia por trás. Por isso o instalador baixa o **Node** e o motor do esquadrão na primeira vez (inclui um modelinho de ~23 MB), o que pode deixar a primeira resposta um pouco mais lenta.

## Por que precisa de "endereço HTTPS"
Para o Zernio falar com o seu agente pela internet, o agente precisa de um endereço seguro (https).
- **Docker:** o Traefik do seu Hermes cria esse endereço automaticamente (estável).
- **Nativo:** usamos o **Cloudflare Tunnel** (cloudflared). Esse endereço pode mudar se a VPS reiniciar — por isso existe o `hermes-imobiliaria doctor`, que detecta o novo e te avisa para atualizar no Zernio.

## Onde ficam suas informações
Tudo que você digita fica só na sua VPS, em `/root/.imobiliaria-squad-ccb/`, com acesso restrito. As "instruções de trabalho" do agente você mesmo cola no bot do Telegram para ele guardar na memória.
