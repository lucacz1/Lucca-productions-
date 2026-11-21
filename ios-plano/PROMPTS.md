# Plano iOS — Prompts para o Grok + Guia Hackintosh 8 GB

> Tudo começa do zero. Nenhum prompt anterior é reaproveitado. DJI Spark fora do plano.

---

## ETAPA 1 — Prompt para o Grok: "iPhone Web" (iOS 15/16/17 em HTML)

Copie e cole no Grok exatamente como está:

```
Crie um único arquivo HTML (HTML + CSS + JavaScript puro, sem frameworks, sem dependências externas)
que simule a interface de um smartphone no estilo iOS 15/16/17, rodando dentro do navegador.

REQUISITOS GERAIS
- Moldura de celular centralizada na tela (proporção 19.5:9, cantos arredondados, "notch"/Dynamic Island).
- Barra de status no topo: hora real (atualiza a cada minuto), sinal, Wi-Fi, bateria.
- Tela de bloqueio com hora/data grandes; deslizar para cima (ou clique) desbloqueia.
- Tela inicial (Home) com grade de ícones 4 colunas + Dock com 4 ícones.
- Ícones GENÉRICOS desenhados em SVG inline ou CSS (formas simples + gradientes). Não usar logotipos
  oficiais de nenhuma empresa. Nome do app abaixo de cada ícone.
- Abrir app: animação de zoom a partir do ícone. Fechar: barra inferior (home indicator) — clique ou
  arraste para cima volta para a Home.
- Seletor de modo claro/escuro no app Ajustes, salvo em localStorage (com try/catch).
- Layout responsivo: em tela de celular real, ocupa a tela inteira sem moldura.

APPS (somente estes, nenhum outro)
1. Safari (navegador 1): barra de endereço, botões voltar/avançar/recarregar, abas.
   Carrega sites num <iframe>. Se o site bloquear iframe (X-Frame-Options/CSP), mostrar aviso
   "Este site não permite ser aberto aqui" com botão "Abrir em nova aba" (window.open).
   Página inicial com favoritos: Wikipedia, YouTube, Google, DuckDuckGo.
2. Firefox (navegador 2): mesma lógica do Safari, mas visual diferente (barra de endereço embaixo,
   cor laranja/roxa genérica), página inicial com atalhos próprios.
3. App Store (loja): lista de apps "instaláveis" com botão OBTER. Ao instalar, o ícone aparece na Home
   (salvo em localStorage). Apps na loja: os editores abaixo + atalhos web (Instagram Web,
   TikTok Web, Facebook Web, Adobe Express Web) que abrem o site oficial em nova aba.
4. Fotos: galeria que aceita upload de imagens do computador (input file), grade de miniaturas,
   visualização em tela cheia.
5. Editor de Fotos: abrir imagem, ajustes com sliders (brilho, contraste, saturação, matiz, desfoque,
   sépia, P&B) via filtros de <canvas>, cortar, girar 90°, espelhar, desfazer, exportar PNG/JPG.
6. Editor de Vídeo: importar vídeo local, player com timeline, cortar início/fim (trim), ajustar
   velocidade (0.5x/1x/2x), filtros CSS em tempo real, exportar o trecho usando
   canvas.captureStream() + MediaRecorder (WebM).
7. Câmera: usa getUserMedia, tira foto e salva na galeria Fotos.
8. Ajustes: modo claro/escuro, papel de parede (4 gradientes), tamanho do texto, "Sobre" com
   versão simulada selecionável (15 / 16 / 17) que muda pequenos detalhes visuais
   (ex.: 16+ tem widgets na tela bloqueada; 17 tem Dynamic Island animada).
9. Arquivos: lista os arquivos exportados pelos editores (guardados em IndexedDB, com try/catch).

REGRAS
- Nenhum outro app além dos listados.
- Código organizado em seções comentadas (ESTILO, SISTEMA, APPS).
- Tudo funciona offline, exceto os sites carregados nos navegadores.
- No final, me dê o arquivo completo num único bloco de código, e uma lista de como testar cada app.
```

### Como medir a Etapa 1 (checklist)
| # | Teste | OK? |
|---|-------|-----|
| 1 | Abre no Chrome/Edge/Firefox do PC sem erro no console (F12) | ☐ |
| 2 | Desbloqueio e Home funcionam | ☐ |
| 3 | Safari carrega Wikipedia no iframe | ☐ |
| 4 | Safari mostra aviso + "nova aba" no Instagram | ☐ |
| 5 | Firefox abre e tem visual diferente | ☐ |
| 6 | App Store instala app e ele aparece na Home após recarregar | ☐ |
| 7 | Editor de Fotos exporta PNG | ☐ |
| 8 | Editor de Vídeo exporta WebM cortado | ☐ |
| 9 | Câmera pede permissão e salva foto | ☐ |
| 10 | Troca 15/16/17 muda visual | ☐ |

---

## ETAPA 2 — Hackintosh com 8 GB de RAM (dicas)

**Resposta curta: sim, dá — com versões mais antigas do macOS.** O limite real não é só a RAM,
é a **placa de vídeo** e o **chip de áudio** do seu PC.

### Qual versão escolher com 8 GB
| macOS | Ano | 8 GB? | Observação |
|-------|-----|-------|-----------|
| High Sierra 10.13 | 2017 | Ótimo | Última com driver NVIDIA (Web Drivers, GTX 600–10xx) |
| Mojave 10.14 | 2018 | Ótimo | Leve, bom p/ Final Cut/Photoshop antigos. Sem NVIDIA moderna |
| Catalina 10.15 | 2019 | Bom | Só apps 64-bit |
| Big Sur 11 | 2020 | Aceitável | Mais pesado, precisa SSD |
| Monterey 12 / Ventura 13+ | 2021+ | Sofre | Funciona, mas com 8 GB fica lento com editores de vídeo |

**Recomendação para 8 GB: Mojave (10.14) ou Catalina (10.15), instalado direto no SSD (bare metal), não em máquina virtual.**

### Bare metal vs. máquina virtual
- **Máquina virtual (VMware/VirtualBox/QEMU) num PC de 8 GB:** você só dá ~4 GB ao macOS, e
  **não tem aceleração de vídeo** → gráfico pior que o Windows, áudio com estalos. Serve só para testar.
- **Bare metal (instalado direto no SSD com OpenCore):** aqui o gráfico e o áudio podem ficar
  iguais ou melhores que no Windows — **mas só se seu hardware for compatível**.

### "O gráfico/áudio é melhor que o Windows?" — como testar de verdade
Não é automaticamente melhor; depende do hardware. Meça assim nos dois sistemas:
1. **Gráfico:** Cinebench R15/R20 (CPU) e **Geekbench 5 (Metal/OpenCL)** vs. OpenCL no Windows.
   Também confira em *Sobre este Mac → Relatório do Sistema → Gráficos* se aparece "Metal: Compatível"
   e a VRAM correta (se aparecer 7 MB, a aceleração NÃO está funcionando).
2. **Áudio:** grave/toque o mesmo arquivo WAV em ambos, verifique latência (no macOS o Core Audio
   costuma ter latência menor que o driver padrão do Windows; sem ASIO o Windows perde).
   No Hackintosh o áudio depende do kext **AppleALC** + o *layout-id* certo do seu codec Realtek.
3. Anote numa tabela: FPS, pontuação, travamentos, temperatura.

### Compatibilidade rápida
- **CPU:** Intel 4ª a 10ª geração = mais fácil. AMD Ryzen funciona com patches, mais trabalho.
- **GPU:** Intel HD/UHD integrada (HD 4600, 530, 630) ✅ · AMD RX 400/500/5000/6000 ✅ ·
  NVIDIA GTX 600–10xx só até High Sierra · NVIDIA RTX ❌.
- **Wi-Fi:** placas Intel precisam do kext AirportItlwm; Broadcom é a mais compatível.

### Passos para medir (roteiro)
1. Liste seu hardware (CPU, GPU, placa-mãe, codec de áudio, Wi-Fi) — rode `msinfo32` / HWiNFO no Windows.
2. Siga o **Guia Dortania OpenCore** (dortania.github.io/OpenCore-Install-Guide) — é a referência atual.
3. Baixe o macOS escolhido com o script `macrecovery.py` do OpenCorePkg (vem dos servidores da Apple).
4. Monte o pendrive EFI (OpenCore + kexts: Lilu, VirtualSMC, WhateverGreen, AppleALC, rede).
5. Instale num SSD separado (não apague o Windows).
6. Rode os testes da tabela acima e compare.

> Aviso: a licença da Apple só permite macOS em hardware Apple. Hackintosh é usado por hobby/teste,
> por sua conta e risco.
>
> Sobre "usar a nuvem do Grok": o Grok só gera texto/código; ele não te dá uma máquina virtual
> para instalar macOS. O Hackintosh tem que rodar no seu PC.

---

## ETAPA 3 — Prompt para o Grok: "iPhone de mentira" com apps reais

**Importante (limite técnico real):** apps nativos de iOS (.ipa — Instagram, TikTok, Facebook,
Adobe Lightroom/Photoshop) **não rodam dentro de HTML** nem em Hackintosh/Windows em PC Intel/AMD.
O que dá para fazer de verdade:
- Usar as **versões web oficiais** (instagram.com, tiktok.com, facebook.com, Adobe Express,
  Photoshop Web) — abertas em nova aba/janela a partir do "iPhone", porque esses sites bloqueiam iframe.
- Se quiser o app iOS real: só num iPhone/iPad real, num Mac com chip Apple (M1+ roda apps de iPhone),
  ou via Xcode Simulator (que só roda apps de desenvolvedor, não Instagram da App Store).

Prompt (cole no Grok depois que a Etapa 1 funcionar):

```
Pegue o arquivo HTML do "iPhone Web" que você gerou e adicione um modo "Apps Web Reais":
- Na App Store, crie a categoria "Redes e Criação" com: Instagram, TikTok, Facebook,
  Adobe Express e Photoshop Web, cada um com ícone GENÉRICO (sem logotipo oficial).
- Ao tocar no ícone na Home: abrir a URL oficial (https://www.instagram.com, https://www.tiktok.com,
  https://www.facebook.com, https://new.express.adobe.com, https://photoshop.adobe.com)
  em uma janela pop-up com tamanho de celular (window.open com width=390,height=844),
  para parecer o app dentro do iPhone.
- Antes de abrir, mostrar uma tela de "carregando" de 1 segundo no estilo iOS.
- Adicionar no Safari e no Firefox um botão "Modo celular" que explica ao usuário como ativar
  o modo dispositivo móvel do navegador (F12 → ícone de celular) para os sites mostrarem a versão mobile.
- Manifesto PWA (manifest.json embutido via data URL) para eu poder "Instalar" o iPhone Web
  como aplicativo no Chrome/Edge.
Me devolva o arquivo completo atualizado.
```

### Como medir a Etapa 3
| # | Teste | OK? |
|---|-------|-----|
| 1 | Cada app abre a janela tamanho celular | ☐ |
| 2 | Login no Instagram/Facebook/TikTok funciona na janela | ☐ |
| 3 | Adobe Express abre e edita | ☐ |
| 4 | "Instalar app" aparece no Chrome/Edge | ☐ |
