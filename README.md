# LFS Diligent

Telemetria e ajuste de setups para o **Live for Speed 0.6V**, feito para o servidor LFS Pro Cruise: dados ao vivo do carro, histórico de sessões, biblioteca e editor de setups, e overlay dentro do jogo.

Esta página guarda só os arquivos de instalação. O código-fonte não é público.

**Neste guia:** [Antes de começar](#antes-de-começar) · [Instalar (1ª vez)](#instalar-1ª-vez) · [Atualizar](#atualizar) · [Deu problema?](#deu-problema) · [Desinstalar ou voltar de versão](#desinstalar-ou-voltar-de-versão)

---

## Antes de começar

Confira estes pontos. A maioria dos problemas de instalação vem de um deles.

- [ ] **Windows 10 ou 11** com o WebView2 (já vem no Windows 11; no 10, se a janela abrir em branco, instale o "WebView2 Runtime" da Microsoft).
- [ ] **Live for Speed 0.6V** instalado e **já aberto pelo menos uma vez** (é assim que o jogo cria o `cfg.txt`).
- [ ] A **senha de admin do multiplayer** do seu LFS (é ela que o InSim usa; o app pede no guia).
- [ ] Sua pasta do LFS **fora** de `Program Files`, da Área de Trabalho, do OneDrive e da pasta Downloads. O normal é `C:\LFS`. Nesses outros lugares o Windows costuma bloquear a gravação de arquivos e a instalação/atualização falha.
- [ ] Confirme com a administração do servidor que esse tipo de ferramenta é permitido (veja o [Aviso](#aviso)).

## Instalar (1ª vez)

**1. Baixe.** Abra **[Releases](../../releases/latest)** e, na seção **Assets**, baixe o `LFS-Diligent.exe` (não precisa dos itens "Source code").

**2. Feche tudo.** Feche o **LFS**, o **launcher do LFS PRO (`ProStudios`)** e o **LFSLazy**, se estiverem abertos. O app só instala a DLL com o LFS e o launcher fechados, e o LFS aceita **um** programa no InSim por vez.

**3. Coloque o arquivo na pasta do LFS.** Mova o `LFS-Diligent.exe` para a pasta onde está o `LFS.exe` (por exemplo `C:\LFS`). Ele cria ali, sozinho, uma pasta `LFS-Diligent` com seus dados.

**4. Abra o `LFS-Diligent.exe`.**
- Se o Windows mostrar **"O Windows protegeu o seu PC"**: clique em **Mais informações** e depois em **Executar assim mesmo**. O programa não tem assinatura digital (o certificado é pago), então isso é esperado.
- Se o **antivírus** apagar ou bloquear o arquivo: restaure-o da quarentena e adicione à lista de exceções. É um falso positivo comum em programas empacotados com PyInstaller. Se quiser conferir antes, o hash SHA-256 está no `latest.json` desta página.

**5. Siga o guia que abre sozinho.** Ele tem estes passos, nesta ordem:

| Passo | O que fazer | Quando dá errado |
|---|---|---|
| 1. Pasta do LFS | Se o app não achou sozinho, informe a pasta que tem o `LFS.exe`. | "Não achei o LFS.exe": o arquivo está na pasta errada; mova-o para junto do `LFS.exe`. |
| 2. Ligar OutSim e OutGauge | Clique em **Ajustar cfg.txt** (com o LFS **fechado**). O app guarda uma cópia de segurança ao lado. | "Ainda não existe cfg.txt": abra o LFS uma vez e feche-o normalmente. Se continuar, o guia avisa se o LFS roda em **outra pasta** (botão **Usar a pasta do LFS aberto**) ou se está numa pasta protegida do Windows (mova o LFS para `C:\LFS`). |
| 3. Senha de admin do InSim | A senha do app precisa ser **igual à senha de admin do seu LFS**. Se o LFS já tem uma, clique em **Usar a senha do LFS** (não precisa digitar). Se não tem, digite uma: o app grava nas duas (com o LFS fechado). | "password does not match your multiplayer admin password": as senhas estão diferentes; em **Configurações > Jogo e conexão** use **Usar a senha do LFS**. |
| 4. HUD no jogo (DLL) | Com o **LFS e o ProStudios fechados**, clique em **Instalar DLL**. | "LFS aberto" ou "launcher aberto": feche-os (o app pode encerrar o launcher por você, pelo botão do passo). "Já existe um d3d9.dll de outro programa": o app **nunca** o sobrescreve; renomeie esse arquivo à mão ou use o app sem o HUD. |
| 5. Conexão InSim | Abra o LFS e, no **chat do jogo**, digite `/insim 29999` e aperte Enter. | "Recusado": confira a senha do passo 3 e se o LFSLazy (ou outro programa) está aberto. |
| 6. Dados chegando | Entre numa pista e **comece a dirigir**: os dados só chegam com um carro na pista. | Se nada chega, volte ao passo 2 (cfg.txt) e reabra o LFS. |

Passos que mexem em arquivos do LFS só rodam com o **LFS fechado**. Dá para escolher **Fazer depois** e reabrir o guia em **Configurações > Diagnóstico > Abrir guia de configuração**.

**6. (Opcional) Abrir junto com o LFS.** Em **Configurações > Comportamento > Iniciar junto com o LFS** (ou no último passo do guia) você pode ligar uma opção, **desligada por padrão**, para o app abrir sozinho quando você abrir o LFS. Ela grava **uma** entrada só do seu usuário no Windows (sem administrador, sem serviço, sem tarefa agendada) que inicia um vigia leve sem janela; desligar remove só essa entrada. Se você mover o `.exe`, o app avisa e oferece corrigir.

**Pronto quando:** o guia mostra **"Tudo pronto"**, os dados do carro aparecem ao vivo no app e o HUD aparece dentro do jogo.

## Atualizar

O app avisa quando há versão nova (**Configurações > Atualizações**). Nada é instalado sem você pedir.

1. Abra **Configurações > Atualizações** e clique em **Atualizar agora** quando houver versão nova (o app baixa e confere o arquivo).
2. Quando terminar, clique em **Aplicar e reiniciar** e confirme. O app fecha, troca o arquivo e abre de novo sozinho. Guarde uma cópia do `LFS-Diligent.exe.bak-…` que ele deixa ao lado, caso queira voltar.
3. **Feche o LFS e o ProStudios e clique em "Atualizar DLL".** Esse passo é o que mais passa batido: quando a versão traz mudanças no HUD, o app novo precisa da **DLL nova** dentro da pasta do LFS. Sem isso o HUD fica na versão antiga e recursos novos (como criar binds no jogo ou a troca de placa) não funcionam direito. O botão está no guia (passo "HUD no jogo") e na tela **Overlay**; ele só funciona com o LFS fechado.
4. Abra o LFS de novo. Se o InSim não conectar, digite `/insim 29999` no chat do jogo.

Se o app não conseguir atualizar sozinho (por exemplo, o antivírus bloqueou a troca), faça à mão: **feche o app e o LFS**, baixe o `LFS-Diligent.exe` novo em **[Releases](../../releases/latest)**, substitua o arquivo antigo na pasta do LFS, abra o app e faça o passo 3 acima. Seus dados ficam na pasta `LFS-Diligent` e não são apagados.

A checagem só lê um arquivo desta página: não envia nenhum dado seu. Há um canal **Beta** para testadores, que exige um código fornecido pelo autor.

## Deu problema?

| O que aconteceu | O que fazer |
|---|---|
| A janela do app abre em branco | Instale o WebView2 Runtime da Microsoft e abra de novo. |
| O Windows ou o antivírus bloqueou o `.exe` | Veja o passo 4 de [Instalar](#instalar-1ª-vez): "Executar assim mesmo" e exceção no antivírus. |
| O app abre, mas não aparece nenhum dado do carro | Confira o passo 2 do guia (OutSim/OutGauge no `cfg.txt`, com o LFS fechado), reabra o LFS e **dirija**: sem carro na pista não chega nada. |
| "InSim : password does not match your multiplayer admin password" | A senha do app é diferente da de admin do LFS. Em **Configurações > Jogo e conexão**, clique em **Usar a senha do LFS**. |
| Chat, pista ou lista de carros não aparecem | O InSim não conectou: digite `/insim 29999` no chat do jogo, confira a senha de admin (passo 3) e feche o **LFSLazy**. |
| "Recusado" no passo do InSim | Senha de admin errada, ou outro programa (LFSLazy) ocupando o InSim. |
| O HUD não aparece dentro do jogo | A DLL não está instalada ou está de versão antiga: com o **LFS e o ProStudios fechados**, clique em **Instalar/Atualizar DLL**. |
| Não consigo instalar a DLL ("já existe um d3d9.dll") | Há outro programa usando esse arquivo. O app não o sobrescreve; renomeie-o à mão (com o LFS fechado) se quiser o HUD. |
| Depois de atualizar, binds/placa/HUD estão "estranhos" | Falta a **DLL nova**: feche o LFS e clique em **Atualizar DLL**. |
| Não consigo mexer em arquivos na pasta do LFS | O LFS está em `Program Files`, OneDrive ou outra pasta protegida; use `C:\LFS`. |
| A atualização falhou | O app restaura a versão anterior sozinho. Tente de novo ou atualize à mão (veja [Atualizar](#atualizar)). |

Para pedir ajuda, use **Configurações > Diagnóstico > Copiar diagnóstico** e envie o texto: ele não inclui a sua senha.

## Desinstalar ou voltar de versão

- **Voltar uma versão:** **Configurações > Atualizações > Reverter para a versão anterior** restaura a cópia anterior. Depois de reverter, faça também **Atualizar DLL** (com o LFS fechado) para a DLL ficar na mesma versão do app.
- **Desinstalar:** feche o LFS e o app, apague o `LFS-Diligent.exe` e a pasta `LFS-Diligent`. Para remover o HUD, apague o `d3d9.dll` da pasta do LFS (só se for o deste app; se houver um `d3d9.dll.bak-…`, ele é o seu original).
- O app **não** altera o `LFS.exe`. As únicas mudanças fora da pasta dele são o `cfg.txt` (com cópia de segurança `.bak-…`) e o `d3d9.dll`.

## Privacidade

Tudo roda no seu computador. O app não envia telemetria nem dados de jogo para a internet; a única conexão é a leitura do arquivo de versões desta página.

## Aviso

O LFS Diligent lê dados do jogo (InSim, OutSim e a memória do próprio LFS) e usa um overlay dentro do jogo. Confirme com a administração do seu servidor se esse tipo de ferramenta é permitido antes de usar.
