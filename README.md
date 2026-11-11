# Mundo Pixelândia

Simulador de vila pixel art com moradores inscritos do YouTube e Estúdio de Vídeos.

Abra `index.html` em navegador moderno. Para usar PWA, hospede por HTTPS.

## Narração no Estúdio

Escolha qualquer tipo de vídeo no **Estúdio**, abra **Narração com ElevenLabs**, clique em **Gerar narração** e selecione **Usar no vídeo**. O Estúdio monta o roteiro e sincroniza a voz com os cards, mesmo com a música desligada. Em **Boas-vindas**, o roteiro acompanha as chegadas, mostra como ficou a vila e inclui as obras da votação quando selecionadas. No modo expresso, os nomes são narrados em grupos de até cinco.

Na votação, abra **Prévia** para conferir o áudio com as legendas. Nos eventos, **Ver roteiro** permite ouvir cada card. O áudio gerado fica disponível até recarregar a página. Se mudar o roteiro, gere a narração novamente.

Para conectar o Estúdio ao ElevenLabs, publique [`narration-worker.mjs`](narration-worker.mjs) como um Cloudflare Worker. No painel do Worker, configure estas variáveis em **Settings → Variables and Secrets**:

| Nome | Tipo | Valor |
|---|---|---|
| `STUDIO_ORIGIN` | Variável | `https://lucianosmvm.github.io` para o site publicado, sem o caminho do projeto |
| `ELEVENLABS_VOICE_ID` | Variável | Voice ID do seu clone compatível com Eleven v4, na mesma conta da chave |
| `ELEVENLABS_API_KEY` | Segredo | Chave do ElevenLabs com acesso a Text to Speech |
| `STUDIO_TOKEN` | Segredo | Código aleatório forte para proteger seu serviço de narração |

No Estúdio, informe a URL HTTPS do Worker e o valor de `STUDIO_TOKEN` como código de acesso. A chave do ElevenLabs fica no Worker. Consulte a [documentação de segredos do Cloudflare Workers](https://developers.cloudflare.com/workers/configuration/secrets/).
