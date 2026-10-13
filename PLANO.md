# Plano ATLAS.victor — atualizado em 12/10/2026

Continua o plano de 01/10 (`Plano — ATLAS.victor depois da avaliação de 01/10`). As fases 0–5 daquele plano seguem valendo para o cofre. Esta página é a cópia que vive na pasta do projeto. O quadro `quadro/AGORA.md` continua sendo o agora do cofre, não este arquivo.

Em 12/10 entram duas peças no plano. Nenhuma das duas está construída.

## B0 — Hermes novo na VM

O Hermes que já está no PC do Daniel não entra neste projeto. A frota do Victor é outra, instalada na VM.

O Hermes da VM é a estrutura dos agentes. Um agente é um profile, com pasta e estado próprios. O primeiro profile é a Berlota, a voz. Os outros agentes do projeto nascem ali, do mesmo jeito. O Hermes decide e reparte o trabalho. Não sobe arquivo, não publica e não mexe no Mandar.

O que fica de fora desta peça:

- O Hermes do PC do Daniel (`hermes-local`, profiles `daniel-ops` e `science`).
- O Mandar. Continua o script na Mac da Erica.
- O programinha do Resolve. Ele é a mão do Cineasta, não um profile.
- Chat dentro do Mac. Victor e Erica falam pelo Telegram, que continua quieto até o Daniel dizer **manda**.

O dashboard de atividade dos agentes mora na VM e se vê pelo túnel. Não é a primeira entrega. Com um agente só, o painel nativo do Hermes basta. A página para eles olharem entra quando houver mais de um trabalho longo ao mesmo tempo.

## B4 — Cineasta, no Resolve deles

O Cineasta é um profile do Hermes da VM. A mão fica no Mac do Victor, onde o Studio já está ativado. A licença é chave Blackmagic, nos dois MacBooks. A VM não roda o DaVinci e não gasta vaga.

```
Hermes na VM
    profile Cineasta manda uma ordem já limitada
        |  túnel privado, sem porta pública
        v
Mac A ou Mac B — só um ativo
        programinha em 127.0.0.1
        Resolve Studio aberto + Lucid + projeto
```

Regras do corte:

1. External scripting fica em **Local**. A opção Network não tem senha. A porta **1144** não vai para a internet. Quem alcança essa porta manda no Resolve e pode rodar comando no Mac.
2. O programinha escuta só em `127.0.0.1`, com um token, e só aceita a VM pelo túnel (Tailscale ou WireGuard).
3. O Resolve tem que estar aberto, com o Lucid montado e o projeto carregado. Fechou o programa, o Cineasta para. O `-nogui` fica para depois.
4. No Mac, `scriptapp("Resolve")` sem o IP da rede muitas vezes volta vazio. O programinha trata isso.
5. Só um Mac recebe ordem por vez. O outro espera. Os dois no mesmo projeto se atropelam.
6. O primeiro teste é só leitura: versão, projeto aberto e timeline. Se voltar vazio, para.
7. O short nasce como timeline `ATLAS-SHORT-` numa cópia do projeto que eles já usam. Não se cria projeto novo por short. Não se mexe no projeto ao vivo até o corte ter sido visto.
8. Não apaga, não move e não relinka mídia. Não publica. A fila de render passa por uma pessoa.
9. Mídia original fica só leitura para o agente. O primeiro trabalho é o que dá para desfazer: marcar, organizar, montar a timeline. Nota, cor final e entrega ficam com uma pessoa.
10. Esta mão não mexe no Mandar e não espera o `FECHOU`.

O Studio 21.1 tem MCP nativo em **File > Setup AI Assistants**. A chave é da Blackmagic, então o menu deve existir quando o Mac estiver no 21.1. Esse MCP configura um assistente no próprio Mac. Não substitui o túnel, porque o Cineasta mora na VM. O programinha pode usar esse MCP por baixo, em Local, se a versão do Mac for 21.1 ou mais nova. Antes disso, ler a versão. Durante o setup: não mudar mídia, e deixar **Automatic scripted actions** em Allow safe.

## O que mudou em 12/10

O Victor já tem o DaVinci Resolve Studio nos dois MacBooks dele. Essas duas ativações são as duas máquinas dele. Não compramos terceira vaga e não colocamos a chave dele em outra máquina.

O agente que estamos montando fica na VM. O Resolve fica num dos Macs, aberto, no projeto, com o Lucid montado. A VM não roda o DaVinci, não precisa de GPU e não gasta licença. Ela manda trabalho para um programinha no Mac. O programinha fala com o Resolve só ali, em Local.

Os dois Macs entram no mesmo túnel. O agente conhece os dois. Só um recebe ordem por vez: o que estiver com o projeto aberto e marcado livre. O outro fica em espera. Os dois ao mesmo tempo no mesmo projeto se atropelam.

## Ponte — programinha e túnel

Isto serve o projeto inteiro, não só o corte. O mesmo túnel é o caminho privado entre a VM e os dois Macs do Victor. Não abre porta no Starlink.

```
VM (agente ATLAS, na conta do Victor)
        |  túnel privado, sem porta pública
        v
Mac A ou Mac B  —  só um ativo
        programinha no loopback
        Resolve Studio aberto + Lucid + projeto
```

Regras:

1. External scripting fica em **Local**. A opção Network (`scriptapp("Resolve", "IP")`) não tem senha. No fórum da Blackmagic (março de 2025) quem alcança a porta manda no Resolve e, pelo Fusion, roda comando no sistema. A documentação do scripting escuta na porta **1144**. Essa porta não vai para a internet.
2. O programinha escuta só em `127.0.0.1`, com um token, e só aceita a VM pelo túnel (Tailscale ou WireGuard). A VM não importa o `fusionscript` de longe.
3. O Resolve tem que estar aberto, com alguém logado no Mac. Fechou o programa, a ponte cai. O `-nogui` existe na documentação e fica para depois. A primeira versão é o app aberto.
4. No Mac, `scriptapp("Resolve")` sem IP muitas vezes volta `None`: o Resolve se anuncia no IP da rede, não em localhost. O programinha trata isso. Quem documentou de novo em setembro de 2026 foi a biblioteca `dvr`.
5. A ponte não apaga, não move e não relinka mídia. Não publica no YouTube. O primeiro teste é só leitura: qual projeto e qual timeline estão abertos.
6. Short entra como timeline `ATLAS-SHORT-` numa cópia do projeto, nunca no projeto ao vivo, até o corte ter sido visto.
7. Esta ponte não mexe no Mandar, não publica app e não espera o `FECHOU`.

### O que a ponte faz primeiro

1. Os dois Macs e a VM no mesmo túnel. Cada Mac tem nome fixo.
2. No Mac que for o alvo: Resolve Studio aberto, scripting em Local, programinha no ar.
3. Da VM: ler versão, projeto e timeline. Se voltar vazio, parar.
4. Trava: um Mac ativo. Pedido para o outro espera ou recusa.
5. Só então, numa cópia: criar a timeline `ATLAS-SHORT-` e marcar. Render continua com uma pessoa olhando a fila.

### Studio 21.1 no próprio Mac

Em 8 de setembro de 2026 o Studio 21.1 ganhou um MCP nativo. O caminho oficial é **File > Setup AI Assistants**. Ele configura o assistente naquela máquina. É Studio, e é atualização grátis para quem já tem a chave da Blackmagic.

Isso não substitui a ponte. O MCP oficial fala com um assistente no próprio Mac. O nosso agente está na VM. O programinha no Mac pode usar o MCP oficial por baixo, em Local, se o Resolve desse Mac for 21.1 ou mais novo. A licença do Victor é chave da Blackmagic, não Mac App Store. Antes de instalar ponte de terceiro, ler a versão e ver se o menu existe.

Enquanto o setup roda: não instalar ponte de terceiro se o oficial já conectar, não mudar mídia, e deixar **Automatic scripted actions** em Allow safe. Quem publicou esse roteiro no X em 8 de setembro foi o Duyifo.

## O que a gente leu antes de fechar isto

| Onde | Quando | O que serve aqui |
|---|---|---|
| Fórum Blackmagic, “authentication for External Scripting” | mar/2025 | Network não tem senha. Fusion executa comando no Mac. Não abrir essa porta. |
| Documentação do scripting (porta 1144, `-nogui`) | lida em out/2026 | A porta é conhecida. Headless fica para depois. |
| CineD, Digital Production, ScenePaper, Y.M.Cinema | 8 set–1 out 2026 | MCP oficial é Studio 21.1, menu File > Setup AI Assistants. Primeiro trabalho é o que dá para desfazer: renomear, bin, marcador, fila de render. Nota, cor final e entrega ficam com uma pessoa. A Blackmagic avisa que o script tem o mesmo acesso a disco e rede que o assistente. Mídia original fica só leitura para o agente. |
| `dvr` no PyPI | 19 set 2026 | No Mac, `scriptapp("Resolve")` sem o IP da rede volta `None`. |
| @Duyifo no X | 8 set 2026 | Setup oficial: Local, Allow safe, não mexer em timeline durante a instalação, não fechar o Resolve sem pedir. |
| @qrzfkg no X | 19 set 2026 | Studio comprado na Mac App Store pode não receber o AI Assistant no 21.1. |
| @DanteBorgese no X | 12 out 2026 | Um bot numa máquina sem placa de vídeo não instala o Resolve. Ele achou o Resolve que já estava no Mac e só ligou o MCP. É o nosso caso: a VM não instala o DaVinci. |
| @JohannPadma no X | 12 out 2026 | Estúdio com MCP do Studio, Hermes e bots próprios em cima do pipeline que já existe. Não troca o projeto. |
| @kapicode no X | 11 out 2026 | MCP é o caminho curto. Plano B, se a API falhar: transcrição e XML, sem dirigir o Resolve. |

Não achamos um relato recente de alguém tunelando a porta 1144 pela internet de propósito. Quem trabalha de longe ou senta o assistente no Mac, ou usa um túnel privado até um serviço local. A porta aberta é o exemplo que o fórum pede para não repetir.

## Fases que já existiam

0. Push dos commits do `inbox-mac`. Feito (`c815611`). Não publicou app novo.
1. `COMO_FUNCIONA.md` e a nota no README do `atlas-victor`. Feito no doc local e no README.
2. Patch do Mandar (timeout, unfinished sem `fileInfo`, rclone só abaixo de 64 MB). Escrito no git local (`ec58573`). Publicar só com o Mac da Erica parado e sem multipart aberto.
3. `atlas-index.json` para o Drive mostrar percentual. Não começou.
4. Tirar a chave da URL pública do Drive, depois de avisar a Erica e o Victor. Não começou.
5. Conteúdo pela planilha. Primeiro lote publicado na mão, com OK. Sem fábrica B4–B8.

A ponte do Cineasta é a fase **R**. Não espera o patch do Mandar e não mistura com ele.

## Ordem a partir de 12/10

Estrutura, separada do cofre:

1. Hermes novo na VM. Um profile, a Berlota. Sem instalar nada no Mac e sem usar o Hermes deste PC.
2. Túnel até os dois Macs e o programinha em Local. O Cineasta, pela VM, só lê o projeto aberto.
3. Numa cópia do projeto: timeline `ATLAS-SHORT-`. Publicar continua na mão.

Cofre, quando o Mandar estiver parado e sem multipart:

4. Testar o patch da fase 2 em ~2 GB e só então publicar.
5. Manifest e a tela de progresso do Drive.
6. Trava do Drive, combinada com eles.

## Ainda em aberto

- Qual dos dois Macs é o de editar e qual fica aberto para o agente, quando os dois estão ligados.
- Versão do Studio em cada Mac. A licença é chave da Blackmagic, confirmada em 12/10. Não é Mac App Store, então o menu File > Setup AI Assistants deve existir no 21.1.
- Onde está a planilha. A última edição conhecida é 15/09.
- Música famosa no Shorts: alcance ou receita.
- Lançamento combinado no WhatsApp de 22/09: quinta 29/10/2026, 14h em Nova York. A planilha ainda diz 07/10.
