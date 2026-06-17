# Problemas comuns (e como resolver)

A maioria se resolve rodando:

```bash
hermes-imobiliaria doctor
```

(O doctor confere o webhook **e** o esquadrão — Node e o motor do esquadrão.)

---

### "Comentei/mandei DM e o agente não respondeu"
**Quase sempre não é bug.** O Zernio só dispara o webhook para interações de **outra** pessoa. Teste de **outra conta** do Instagram.

### "O esquadrão não está respondendo / as tools sumiram"
Rode `hermes-imobiliaria doctor`. Ele confere se o **Node 20+** está presente, se o **Ruflo** (motor do esquadrão) está instalado e conectado, e reconecta o que der. Se precisar reinstalar à mão: `npm install -g ruflo@latest` e rode `hermes-imobiliaria` de novo.

### "A primeira resposta demorou muito"
Na primeira vez, o esquadrão baixa um modelinho (~23 MB). Depois fica em cache e acelera. Modelos de IA gratuitos no Hermes também deixam as respostas mais lentas — configure um modelo mais rápido no perfil.

### "As respostas pararam de funcionar do nada" (instalação nativa)
O endereço do túnel (Cloudflare) provavelmente **mudou** (a VPS reiniciou). Rode `hermes-imobiliaria doctor`: ele mostra o **endereço novo**. Atualize no painel do Zernio em *Webhooks → seu webhook → Endpoint URL*.

### "O bot do Telegram não responde"
O token pode ter sido revogado no @BotFather. Rode `hermes-imobiliaria` de novo e cole o token atual.

### "O agente prometeu financiamento / deu parecer jurídico"
Não deveria. Essas restrições ficam no contexto do negócio. Rode `hermes-imobiliaria contexto`, confira o texto e cole de novo no bot pedindo "salve isso na sua memória". Reforce a restrição rodando `hermes-imobiliaria` e ajustando "o que o agente NUNCA deve fazer".

### "O agente responde 'qual contato? qual interação?'"
A rota do webhook está sem os dados do evento. O assistente cria a rota com o marcador `{__raw__}`. Rode `hermes-imobiliaria doctor` para recriar.

### "O Zernio mostra 401 (não autorizado)"
A **chave de segurança** (Signing Secret) no painel do Zernio difere da que está na VPS. Rode `hermes-imobiliaria info` para ver a chave certa e cole no Zernio.

### "Depois de atualizar o Hermes, parou" (instalação nativa)
Atualizar o Hermes apaga o ajuste da assinatura (`X-Zernio-Signature`). Rode `hermes-imobiliaria doctor` — ele reaplica.

---

Se nada disso resolver, leve a saída do `hermes-imobiliaria doctor` para a comunidade.
