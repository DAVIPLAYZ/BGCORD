# BGCORD v0.2 — protótipo de comunidade

Este é um projeto original de aprendizado, inspirado em categorias comuns de apps de comunidade. Não copia código, marca, logotipo, interface exata ou recursos proprietários do Discord.

## Executar no Windows
1. Extraia o ZIP.
2. Abra a pasta do projeto no Explorador, digite `cmd` na barra de endereço e pressione Enter.
3. Execute `npm.cmd install`
4. Execute `copy .env.example .env`
5. Execute `npm.cmd start`
6. Abra http://localhost:3000

Requer Node.js LTS. Os dados locais ficam na pasta `data`.

## Recursos presentes no protótipo
- Registro e login com hash bcrypt e sessões SQLite.
- Comunidade inicial automática, criação de outras comunidades e convite por código.
- Canais de texto e voz (estrutura inicial).
- Chat em tempo real com histórico local.
- Presença de usuários conectados.
- Pedidos de amizade e aceitação simples.
- Formulário básico de denúncia.
- Painel de configurações e preferências demonstrativas.
- Captura local de câmera e compartilhamento de tela pelo navegador.
- Base inicial de sinalização WebRTC.

## Ainda não pronto para público
A sinalização WebRTC está incompleta: ofertas e respostas são encaminhadas, mas não há negociação automática robusta entre todos os pares, e a tela/mídia capturada não é distribuída de forma completa a todos os participantes. Não anuncie chamadas como funcionais até completar testes e implementar a malha de peers. Configure TURN para usuários em redes restritivas.

Também faltam confirmação de e-mail, recuperação de senha, 2FA, exclusão/exportação de conta, bloqueio funcional, moderação de servidor, permissões detalhadas, rate limiting, anti-spam, upload e armazenamento de arquivos, notificações, testes, monitoramento e revisão de segurança.

Para produção:
- Defina `SESSION_SECRET` com valor longo e aleatório.
- Use HTTPS/WSS e cookies seguros.
- Implemente limitação de requisições, validação de dados, proteção contra abuso e backups.
- Avalie PostgreSQL/Redis e escalabilidade antes de crescer.
- Crie Termos de Uso, Política de Privacidade e processos LGPD.
- Não exponha diretamente a porta local à internet.

## Aplicativo Windows
A próxima etapa pode adicionar Electron e electron-builder para empacotar o frontend em um instalador. Para o lançamento, prefira um backend hospedado e que o aplicativo desktop se conecte ao serviço via HTTPS; não embuta banco de dados ou segredo de produção no cliente.


## BGCORD 0.3.0 — instalação simplificada
Esta versão remove dependências nativas que exigiam compilação C++ no Windows. Ela usa `node:sqlite` integrado ao Node.js (Node 22.13+ recomendado) e sessões em memória para desenvolvimento local. Para lançamento público, configure um armazenamento de sessão persistente, segredo seguro, HTTPS, limites de requisição e infraestrutura de voz/vídeo.


## Atualização 0.3.1
- Logo vermelha do BGCORD aplicada na tela de entrada, barra de comunidades e cabeçalho.
- Foto de perfil configurável em Configurações → Minha conta; aceita PNG/JPG/WEBP/GIF até 2 MB.
- A foto fica armazenada no banco local de usuários.


## Amigos (v0.3.2)
- Cada conta tem um nick de usuário; use o botão **Copiar** ao lado de “Seu nick” para compartilhar.
- Para adicionar alguém, digite o nick exato no campo e clique em **Enviar pedido**.
- O destinatário verá **Pedido recebido** e poderá clicar em **Aceitar**. Depois, ambos aparecem como **Amigos**.
- O projeto continua em desenvolvimento e ainda precisa de testes de segurança e implantação antes de lançamento público.


## BGCORD 0.4.0 — arquivos e emojis
- O chat ganhou seletor básico de emojis.
- Usuários autenticados podem enviar arquivos de até 100 MB para o servidor local e compartilhar o link no canal.
- Os arquivos são gravados em `data/uploads`. Planeje cotas, backups, verificação de conteúdo e armazenamento externo antes de hospedar publicamente.
- **Detecção automática de jogos no Windows ainda não está ativada nesta versão.** O site no navegador não pode inspecionar processos do Windows por segurança. Para isso, será necessário empacotar o BGCORD como aplicativo desktop (por exemplo, Electron) e criar um módulo local de detecção com permissões explícitas. O indicador na interface é apenas informativo.


## Atualização 0.4.1
- Seletor ampliado de emojis Unicode (a aparência pode variar conforme o Windows).
- Envio de imagens com pré-visualização no chat.
- Reprodução de áudios enviados com controles do navegador.
- Gravação de áudio de voz pelo microfone: clique em 🎙 para iniciar e novamente para parar e enviar.
- Envio de vídeo com player no chat.
- Limite de 100 MB por arquivo.

A gravação pelo microfone requer permissão do navegador e contexto seguro (localhost é aceito). Os uploads são armazenados no disco do servidor e precisam de quotas, varredura de arquivos e armazenamento adequado antes de uso público.
