# LFS Diligent

Telemetria e ajuste de setups para o **Live for Speed 0.6V**, feito para o servidor LFS Pro Cruise: dados ao vivo do carro, histórico de sessões, biblioteca e editor de setups, e overlay dentro do jogo.

Esta página guarda só os arquivos de instalação. O código-fonte não é público.

## Baixar

Pegue o arquivo `LFS-Diligent.exe` na página de versões: **[Releases](../../releases/latest)** (na seção "Assets" da versão mais recente).

## Instalar

1. Feche o LFS e o LFS Diligent, se estiverem abertos.
2. Coloque o `LFS-Diligent.exe` dentro da pasta do LFS (por exemplo `C:\LFS`).
3. Abra o `LFS-Diligent.exe`. Na primeira vez ele cria a própria pasta de dados ao lado.
4. Para o overlay dentro do jogo, use o botão de instalar a DLL no app, **com o LFS fechado**.

## Aviso do Windows ao abrir

O programa **não tem assinatura digital** (esse certificado é pago), então o Windows pode mostrar "O Windows protegeu o seu PC" (SmartScreen). Isso é esperado:

1. Clique em **Mais informações**.
2. Clique em **Executar assim mesmo**.

Alguns antivírus também podem alertar, porque o programa é empacotado com PyInstaller. É um falso positivo comum desse tipo de programa; se o seu antivírus bloquear, adicione o arquivo às exceções. Se preferir conferir o arquivo antes, o hash SHA-256 de cada versão está no `latest.json` desta página.

## Atualizações

O app avisa quando há versão nova (Configurações > Atualizações) e atualiza com um clique. Nada é instalado sem você pedir. A checagem só lê um arquivo desta página: não envia nenhum dado seu.

Há um canal **Beta** para testadores, que exige um código fornecido pelo autor.

## Privacidade

Tudo roda no seu computador. O app não envia telemetria nem dados de jogo para a internet; a única conexão é a leitura do arquivo de versões acima.

## Requisitos

- Windows 10 ou 11 com WebView2 (já vem no Windows 11).
- Live for Speed 0.6V.

## Aviso

O LFS Diligent lê dados do jogo (InSim, OutSim e a memória do próprio LFS) e usa um overlay dentro do jogo. Confirme com a administração do seu servidor se esse tipo de ferramenta é permitido antes de usar.
