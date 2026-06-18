# Hermes Imobiliária (Squad) by CCB

![Demonstração](docs/imagens/demo.gif)

> **Falta o GIF de demonstração.** Grave 15–30s mostrando um lead chegando no Instagram, o agente
> qualificando (orçamento, região, comprar/alugar) e oferecendo uma visita — e o aviso no seu Telegram.
> Exporte como GIF e salve em `docs/imagens/demo.gif` (veja `docs/imagens/COMO-GRAVAR-O-GIF.md`).

## 1. O que é
Um **esquadrão de agentes** que cuida do Instagram da sua imobiliária: capta o lead, **qualifica** (orçamento, região, comprar ou alugar, prazo) e ajuda a **agendar a visita** — controlado pelo seu **Telegram**, sem você precisar mexer em código.

## 2. Benefícios
- **Nenhum lead esfria.** Responde na hora, qualifica e já encaminha pra visita — em vez de "te respondo amanhã".
- **Você só recebe lead pronto.** O esquadrão faz a triagem e te chama no Telegram quando alguém quer visitar ou está pronto pra fechar.
- **Qualificação consistente.** Sempre pergunta o essencial (orçamento, região, comprar/alugar, prazo), uma coisa de cada vez, sem afugentar.
- **Seguro por padrão.** Nunca promete aprovação de financiamento, valorização nem dá parecer jurídico — encaminha pra você.
- **Aprende com o tempo.** Anota imóveis/regiões mais procurados e objeções comuns.

## 3. Casos de uso reais
- **"Esse apê do post ainda tá disponível? Qual o valor?"** — o agente informa o que pode, pergunta orçamento/região/prazo e oferece agendar uma visita. Te avisa no Telegram.
- **"Vocês têm casa pra alugar até R$ 2.500 na zona sul?"** — qualifica (quando precisa, quantos quartos) e puxa pra visita ou pro corretor.
- **"Consigo financiar com nome sujo?"** — **não promete nada**: explica que a análise é feita pelo corretor e encaminha com cuidado.
- **DM "quero investir, o que vocês recomendam?"** — qualifica perfil (orçamento, objetivo) e marca uma conversa com o corretor.
- **Comentário "que apartamento lindo! 😍"** — responde simpático em público pra aquecer, sem DM.

Veja os roteiros completos em [docs/CASOS-DE-USO.md](docs/CASOS-DE-USO.md).

## 4. Pré-requisitos
1. Uma **VPS** com o **Hermes Agent já instalado** (Docker **ou** nativo). (Material da CCB.)
2. O Hermes com um **modelo de IA configurado** (`hermes setup`).
3. **Telegram** no celular.
4. Uma conta no **Zernio** (zernio.com) com o **Instagram da imobiliária conectado**.
5. Uma conta **Google** com uma agenda — o assistente te guia a conectar (via "conta de serviço") para o agente **marcar visitas sozinho** na sua Google Agenda.

> O assistente instala sozinho o que o **esquadrão** precisa (Node + o motor do esquadrão). Na 1ª vez ele baixa um modelinho (~23 MB), então a primeira resposta pode demorar um pouco mais.

## 5. Como instalar (1 comando)
Conecte na sua VPS por SSH e cole:

```bash
curl -fsSL https://raw.githubusercontent.com/kleinelizeu/imobiliaria-squad-ccb/main/install.sh | sudo bash
```

O assistente abre sozinho e te guia. Depois, a qualquer momento:

```bash
hermes-imobiliaria            # roda/continua o assistente
hermes-imobiliaria doctor     # confere tudo (inclui o esquadrão) e corrige problemas comuns
hermes-imobiliaria info       # mostra endereço do webhook, chave e nome do bot
hermes-imobiliaria contexto   # mostra o texto da sua imobiliária para colar no bot
```

## 6. Como usar no dia a dia
No Telegram do seu bot, peça em português normal:
- "Crie um post do apartamento de 2 quartos no Jardim X, com uma imagem bonita. Me mostra antes de publicar."
- "Responde quem comentou pedindo valor qualificando e oferecendo visita."
- "Quantos leads quentes apareceram hoje e o que cada um quer?"
- "Muda o tom pra mais próximo e prestativo."

## 7. Perguntas frequentes + comandos
**Preciso saber programar?** Não. O assistente faz tudo e explica onde clicar. Você escolhe o nicho; a parte do "esquadrão" o assistente monta sozinho.

**O agente vai prometer financiamento ou dar parecer jurídico?** Não. Por padrão ele nunca promete aprovação, valorização nem dá orientação jurídica — encaminha pra você.

**Mexe no meu Hermes que já uso?** Cria um agente **separado** (`imobiliaria`), sem mexer no que você já tem.

**Onde ficam minhas senhas e chaves?** Só na **sua VPS**, em `/root/.imobiliaria-squad-ccb/` (protegida).

**Testei do meu próprio Instagram e não respondeu.** Normal: o Zernio só dispara para **outra** pessoa.

**As respostas pararam / o esquadrão sumiu.** Rode `hermes-imobiliaria doctor` — ele confere o webhook E o esquadrão (Ruflo) e reconecta o que der.

Mais detalhes em [docs/COMO-FUNCIONA.md](docs/COMO-FUNCIONA.md), [docs/CASOS-DE-USO.md](docs/CASOS-DE-USO.md) e [docs/PROBLEMAS-COMUNS.md](docs/PROBLEMAS-COMUNS.md).
