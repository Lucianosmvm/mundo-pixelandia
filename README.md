# Mundo Pixelândia

Simulador de vila pixel art com moradores inscritos do YouTube e Estúdio de Vídeos.

Abra `index.html` em navegador moderno. Para usar PWA, hospede por HTTPS.

## Narração no Estúdio

Em **Estúdio → Escolha a próxima obra** ou **Evento especial**, abra **Narração com ElevenLabs** para gerar a voz dos cards com o Eleven v4 em português. Selecione **Usar no vídeo**. Na votação, abra **Prévia** para conferir o áudio com as legendas. Nos eventos, **Ver roteiro** permite ouvir cada card. O Estúdio inclui a voz no arquivo gravado, mesmo com a música desligada. O áudio gerado fica disponível até recarregar a página.

Para conectar o Estúdio ao ElevenLabs, publique [`narration-worker.mjs`](narration-worker.mjs) como um Cloudflare Worker. No painel do Worker, configure estas variáveis em **Settings → Variables and Secrets**:

| Nome | Tipo | Valor |
|---|---|---|
| `STUDIO_ORIGIN` | Variável | `https://lucianosmvm.github.io` para o site publicado, sem o caminho do projeto |
| `ELEVENLABS_VOICE_ID` | Variável | Voice ID do seu clone compatível com Eleven v4, na mesma conta da chave |
| `ELEVENLABS_API_KEY` | Segredo | Chave do ElevenLabs com acesso a Text to Speech |
| `STUDIO_TOKEN` | Segredo | Código aleatório forte para proteger seu serviço de narração |

No Estúdio, informe a URL HTTPS do Worker e o valor de `STUDIO_TOKEN` como código de acesso. A chave do ElevenLabs fica no Worker. Consulte a [documentação de segredos do Cloudflare Workers](https://developers.cloudflare.com/workers/configuration/secrets/).
