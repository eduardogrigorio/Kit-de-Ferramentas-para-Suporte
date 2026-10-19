# 🛠️ Kit de Ferramentas para Suporte de TI
 
> Coleção em português das ferramentas mais úteis para técnicos de suporte, sysadmins e entusiastas: boot e recuperação, diagnóstico, rede, acesso remoto, automação com Chocolatey e utilitários online como o **IT-Tools**.
 
![Licença](https://img.shields.io/badge/licença-MIT-green)
![Idioma](https://img.shields.io/badge/idioma-PT--BR-blue)
![Contribuições](https://img.shields.io/badge/contribuições-bem--vindas-brightgreen)
 
---
 
## 📑 Índice
 
1. [IT-Tools (utilitários online)](#-it-tools-utilitários-online)
2. [Pendrive de boot multiferramentas](#-pendrive-de-boot-multiferramentas)
3. [Chocolatey: instalação em massa](#-chocolatey-instalação-em-massa)
4. [Diagnóstico de hardware](#-diagnóstico-de-hardware)
5. [Sysinternals](#-sysinternals)
6. [Rede e conectividade](#-rede-e-conectividade)
7. [Acesso remoto (MeshCentral e outros)](#-acesso-remoto)
8. [Monitoramento, inventário e helpdesk](#-monitoramento-inventário-e-helpdesk-self-host)
9. [Backup, clonagem e recuperação](#-backup-clonagem-e-recuperação)
10. [Limpeza e análise de disco](#-limpeza-e-análise-de-disco)
11. [Segurança, senhas e remoção de malware](#-segurança-senhas-e-remoção-de-malware)
12. [Utilitários extras populares](#-utilitários-extras-populares)
13. [Comandos úteis do Windows](#-comandos-úteis-do-windows)
14. [Winget (alternativa ao Chocolatey)](#-winget-alternativa-ao-chocolatey)
15. [Boas práticas](#-boas-práticas)
16. [Contribuindo](#-contribuindo)
---
 
## 🧰 IT-Tools (utilitários online)
 
**[IT-Tools](https://github.com/CorentinTh/it-tools)** é uma coleção de ferramentas úteis para desenvolvedores e profissionais de TI, com ótima experiência de uso. É open source (licença GPL-3.0), construído com Vue.js e TypeScript.
 
- 🌐 Versão online: <https://it-tools.tech>
- 📦 Repositório: <https://github.com/CorentinTh/it-tools>
Ele roda 100% no navegador, ou seja, os dados que você digita não precisam sair do seu computador.
 
### Tipos de ferramenta que você encontra nele
 
| Categoria | Exemplos de uso |
|---|---|
| Conversores | Base64, JSON, YAML, cores, datas, bases numéricas |
| Web | Codificação de URL, gerador de User-Agent, parser de URL |
| Imagens e vídeos | Gerador de QR Code, gerador de SVG |
| Desenvolvimento | Formatadores (JSON, SQL, XML), diff de texto, regex |
| Rede | Calculadora de sub-redes IPv4, gerador de MAC, intervalo de IPs |
| Criptografia | Hash (MD5, SHA), geradores de token e senha, bcrypt |
| Matemática | Avaliador de expressões, conversor de unidades |
| Texto | Contador de caracteres, comparador, gerador de Lorem Ipsum |
 
> A lista de ferramentas cresce com frequência. Veja o site oficial para a relação atualizada.
 
### 🏠 Hospedar o seu próprio IT-Tools (self-host)
 
**Docker Hub:**
 
```bash
docker run -d --name it-tools --restart unless-stopped -p 8080:80 corentinth/it-tools:latest
```
 
**GitHub Packages:**
 
```bash
docker run -d --name it-tools --restart unless-stopped -p 8080:80 ghcr.io/corentinth/it-tools:latest
```
 
Depois, acesse `http://localhost:8080`.
 
**Outras opções de instalação:** [Cloudron](https://www.cloudron.io/store/tech.ittools.cloudron.html) · [Runtipi](https://www.runtipi.io/docs/apps-available) · [Unraid](https://unraid.net/community/apps?q=it-tools)
 
### 👨‍💻 Rodar localmente para desenvolvimento
 
```bash
git clone https://github.com/CorentinTh/it-tools.git
cd it-tools
pnpm install
pnpm dev
```
 
---
 
## 💾 Pendrive de boot multiferramentas
 
### Ventoy
 
Cria um pendrive de boot onde você apenas **copia os arquivos ISO** para o disco, sem precisar formatar de novo a cada imagem. Suporta BIOS Legacy e UEFI.
 
- 🌐 Site: <https://www.ventoy.net>
- 📦 GitHub: <https://github.com/ventoy/Ventoy>
```powershell
choco install ventoy -y
```
 
**Como usar:**
 
1. Abra o Ventoy2Disk e selecione o pendrive.
2. Clique em **Instalar** (apaga o conteúdo do pendrive).
3. Copie suas ISOs (Windows, Linux, WinPE, antivírus de boot etc.) para a partição principal.
4. Dê boot pelo pendrive e escolha a ISO no menu.
> 💡 Dica: se o computador usa **Secure Boot**, será preciso registrar a chave do Ventoy (MOK) no primeiro boot, ou usar a opção de Secure Boot na instalação.
 
### Sergei Strelec WinPE
 
Ambiente **Windows PE** pronto para suporte, com dezenas de programas de particionamento, backup, recuperação de senha, diagnóstico de disco, ferramentas de rede e muito mais. É muito usado em bancada junto com o Ventoy.
 
- Procure sempre pela **fonte oficial** do projeto e confira o hash da ISO quando disponível.
- Cole a ISO no pendrive Ventoy e dê boot por ela.
> ⚠️ **Atenção:** WinPEs de terceiros são ferramentas de técnico e **não são produtos oficiais da Microsoft**. Baixe somente da fonte oficial do autor, evite versões repackadas em sites aleatórios e use em ambiente controlado.
 
### Outras opções de boot
 
| Ferramenta | Para que serve | Site |
|---|---|---|
| **Rufus** | Criar pendrive bootável de uma ISO (Windows, Linux) | <https://rufus.ie> |
| **Balena Etcher** | Gravar imagens em pendrives e cartões SD | <https://etcher.balena.io> |
| **Medicat USB** | Pendrive de boot com ferramentas de recuperação baseado em Ventoy | <https://medicatusb.com> |
| **Hiren's BootCD PE** | WinPE gratuito com ferramentas de diagnóstico e recuperação | <https://www.hirensbootcd.org> |
| **SystemRescue** | Distribuição Linux de resgate | <https://www.system-rescue.org> |
| **Clonezilla Live** | Clonagem e imagem de discos | <https://clonezilla.org> |
| **GParted Live** | Particionamento gráfico em Linux | <https://gparted.org> |
| **Memtest86+** | Teste de memória RAM | <https://www.memtest.org> |
| **Windows Media Creation Tool** | Mídia oficial de instalação do Windows | <https://www.microsoft.com/software-download> |
 
```powershell
choco install rufus etcher -y
```
 
---
 
## 🍫 Chocolatey: instalação em massa
 
O **[Chocolatey](https://chocolatey.org)** é um gerenciador de pacotes para Windows. Com ele você instala, atualiza e remove programas por linha de comando, perfeito para formatar e configurar máquinas rapidamente.
 
### Instalação
 
Abra o **PowerShell como Administrador** e execute:
 
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
 
> 🔒 Boa prática: antes de rodar qualquer script baixado da internet, leia o conteúdo. Consulte as instruções atuais em <https://chocolatey.org/install>.
 
Verifique:
 
```powershell
choco --version
```
 
### Comandos essenciais
 
| Ação | Comando |
|---|---|
| Instalar um pacote | `choco install nome-do-pacote -y` |
| Instalar vários | `choco install pacote1 pacote2 pacote3 -y` |
| Buscar pacote | `choco search nome` |
| Ver informações | `choco info nome-do-pacote` |
| Listar instalados | `choco list` |
| Ver desatualizados | `choco outdated` |
| Atualizar um pacote | `choco upgrade nome-do-pacote -y` |
| Atualizar tudo | `choco upgrade all -y` |
| Desinstalar | `choco uninstall nome-do-pacote -y` |
| Fixar versão | `choco pin add -n=nome-do-pacote` |
 
### 🚀 Kit completo de suporte (copie e cole)
 
**Utilitários básicos:**
 
```powershell
choco install 7zip notepadplusplus vlc sumatrapdf googlechrome firefox powertoys microsoft-windows-terminal -y
```
 
**Ferramentas de técnico:**
 
```powershell
choco install ventoy rufus etcher sysinternals putty winscp mobaxterm everything wiztree -y
```
 
**Diagnóstico de hardware:**
 
```powershell
choco install cpu-z gpu-z hwinfo hwmonitor crystaldiskinfo crystaldiskmark hddscan occt prime95 -y
```
 
**Rede:**
 
```powershell
choco install wireshark nmap advanced-ip-scanner angryip -y
```
 
**Acesso remoto:**
 
```powershell
choco install anydesk teamviewer mremoteng tightvnc -y
```
 
> O **MeshCentral** não é instalado pelo Chocolatey. Veja a instalação via Node.js na seção [Acesso remoto](#-acesso-remoto).
 
**Segurança e senhas:**
 
```powershell
choco install keepassxc bitwarden veracrypt malwarebytes -y
```
 
**Utilitários extras populares:**
 
```powershell
choco install winmerge sharex filezilla virtualbox speccy furmark bluescreenview adwcleaner snappy-driver-installer-origin revo-uninstaller smartmontools speedtest iperf3 scrcpy drawio -y
```
 
**Desenvolvimento e scripts:**
 
```powershell
choco install git vscode powershell-core python nodejs-lts -y
```
 
> ℹ️ Os nomes dos pacotes podem mudar ou ser descontinuados. Se algum falhar, use `choco search nome` ou consulte <https://community.chocolatey.org/packages>.
 
### 📄 Instalação por arquivo (`packages.config`)
 
Crie um arquivo `packages.config` para reaproveitar a mesma lista em várias máquinas:
 
```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="7zip" />
  <package id="notepadplusplus" />
  <package id="googlechrome" />
  <package id="vlc" />
  <package id="sysinternals" />
  <package id="putty" />
  <package id="winscp" />
  <package id="mremoteng" />
  <package id="crystaldiskinfo" />
  <package id="hwinfo" />
</packages>
```
 
Execute:
 
```powershell
choco install packages.config -y
```
 
### 🔄 Atualização automática semanal
 
Crie uma tarefa agendada que mantém tudo atualizado:
 
```powershell
$acao = New-ScheduledTaskAction -Execute "choco.exe" -Argument "upgrade all -y"
$gatilho = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 3am
Register-ScheduledTask -TaskName "Atualizar Chocolatey" -Action $acao -Trigger $gatilho -User "SYSTEM" -RunLevel Highest
```
 
---
 
## 🔍 Diagnóstico de hardware
 
| Ferramenta | Função | Pacote Chocolatey |
|---|---|---|
| **CPU-Z** | Informações detalhadas de CPU, RAM e placa-mãe | `cpu-z` |
| **GPU-Z** | Informações e monitoramento da placa de vídeo | `gpu-z` |
| **HWiNFO** | Inventário completo e sensores em tempo real | `hwinfo` |
| **HWMonitor** | Temperaturas, tensões e velocidades de ventoinhas | `hwmonitor` |
| **CrystalDiskInfo** | Saúde de HDD/SSD via S.M.A.R.T. | `crystaldiskinfo` |
| **CrystalDiskMark** | Benchmark de velocidade de disco | `crystaldiskmark` |
| **HDDScan** | Teste de superfície e S.M.A.R.T. | `hddscan` |
| **OCCT** | Teste de estresse de CPU, GPU e fonte | `occt` |
| **Prime95** | Teste de estresse de CPU | `prime95` |
| **MemTest86 / Memtest86+** | Teste de memória RAM (boot) | via pendrive |
| **Display Driver Uninstaller (DDU)** | Remoção completa de drivers de vídeo | `ddu` |
| **Speccy** | Resumo rápido de hardware e temperaturas | `speccy` |
| **FurMark** | Teste de estresse da placa de vídeo | `furmark` |
| **BlueScreenView** | Analisa dumps de tela azul (BSOD) | `bluescreenview` |
| **smartmontools** | S.M.A.R.T. por linha de comando (`smartctl`) | `smartmontools` |
| **Snappy Driver Installer Origin** | Instala drivers de forma offline | `snappy-driver-installer-origin` |
 
### Fluxo rápido de diagnóstico em bancada
 
1. **Saúde do disco** com CrystalDiskInfo (atenção a setores realocados e pendentes).
2. **Memória RAM** com Memtest86+ por pelo menos um ciclo completo.
3. **Temperaturas** com HWMonitor ou HWiNFO durante carga.
4. **Estresse** com OCCT ou Prime95 por 15 a 30 minutos.
5. **Drivers** e atualizações pendentes do Windows.
---
 
## 🪟 Sysinternals
 
Suíte oficial da Microsoft, indispensável para investigar problemas no Windows.
 
```powershell
choco install sysinternals -y
```
 
| Ferramenta | Para que serve |
|---|---|
| **Process Explorer** | Gerenciador de tarefas avançado |
| **Process Monitor** | Monitora arquivos, registro e processos em tempo real |
| **Autoruns** | Mostra tudo que inicia com o Windows |
| **TCPView** | Conexões TCP/UDP abertas e processos associados |
| **PsExec** | Executa comandos em máquinas remotas |
| **Disk2vhd** | Converte disco físico em VHD/VHDX |
| **BGInfo** | Mostra informações do sistema no papel de parede |
| **RAMMap** | Análise detalhada de uso de memória |
| **Sigcheck** | Verifica assinatura digital e hash de arquivos |
 
Documentação: <https://learn.microsoft.com/sysinternals>
 
---
 
## 🌐 Rede e conectividade
 
| Ferramenta | Função |
|---|---|
| **Wireshark** | Captura e análise de pacotes |
| **Nmap** | Varredura de portas e descoberta de serviços |
| **Advanced IP Scanner** | Varredura rápida de IPs na rede local |
| **Angry IP Scanner** | Scanner de IPs e portas, multiplataforma |
| **PuTTY / MobaXterm** | Clientes SSH, Telnet e serial |
| **WinSCP** | Transferência de arquivos via SFTP/SCP |
| **iperf3** | Teste de largura de banda entre dois pontos |
| **Speedtest CLI (Ookla)** | Teste de velocidade da internet por linha de comando |
| **WireGuard** | VPN leve e moderna |
| **Tailscale** | VPN em malha (mesh) fácil de configurar; verifique os limites do plano gratuito |
| **Fing** | Descoberta de dispositivos na rede (app mobile e desktop) |
| **FileZilla** | Cliente FTP/FTPS/SFTP |
 
> 🔐 Faça varreduras e capturas **apenas em redes e equipamentos que você tem autorização para testar**.
 
### Comandos de rede do Windows
 
```cmd
ipconfig /all
ipconfig /flushdns
ipconfig /release && ipconfig /renew
ping 8.8.8.8 -t
tracert google.com
nslookup google.com
netstat -ano
netsh wlan show profiles
netsh int ip reset
netsh winsock reset
```
 
> 💡 Para calcular sub-redes, máscaras e intervalos de IP, use a calculadora de sub-redes do [IT-Tools](https://it-tools.tech).
 
---
 
## 🖥️ Acesso remoto
 
### ⭐ MeshCentral (destaque)
 
**[MeshCentral](https://meshcentral.com)** é uma plataforma de gerenciamento remoto de computadores **gratuita e de código aberto** (Apache 2.0), criada por Ylian Saint-Hilaire. Você hospeda o seu próprio servidor e controla suas máquinas pelo navegador, sem depender de serviços de terceiros.
 
- 🌐 Site: <https://meshcentral.com>
- 📦 GitHub: <https://github.com/Ylianst/MeshCentral>
**Principais recursos:**
 
- Área de trabalho remota, terminal e transferência de arquivos direto no navegador
- Agentes para Windows, Linux e macOS
- Gerenciamento de múltiplos dispositivos e grupos, com usuários e permissões
- Suporte a Intel AMT (gerenciamento fora de banda, quando o hardware permite)
- Autenticação em dois fatores
**Instalação básica (Windows ou Linux com Node.js):**
 
```powershell
choco install nodejs-lts -y
mkdir meshcentral
cd meshcentral
npm install meshcentral
node node_modules/meshcentral
```
 
Depois:
 
1. Acesse o endereço mostrado no terminal (por padrão, `https://localhost`).
2. Crie a primeira conta. Ela se torna a **administradora do servidor**.
3. Crie um **grupo de dispositivos** e use **Adicionar Agente** para baixar o instalador para cada máquina.
4. Para acesso pela internet, configure um domínio/DNS e portas no `config.json`.
> 🔒 **Segurança:** exponha o servidor somente com **HTTPS válido**, ative **2FA**, use senhas fortes e mantenha o MeshCentral atualizado. Consulte o [guia oficial](https://meshcentral.com/docs) para configurações avançadas.
 
### Outras ferramentas de acesso remoto
 
| Ferramenta | Característica | Pacote Chocolatey |
|---|---|---|
| **MeshCentral** | Servidor próprio, 100% via navegador, código aberto | via Node.js (npm) |
| **Tactical RMM** | RMM de código aberto: monitoramento, scripts e acesso remoto (usa MeshCentral) | auto-hospedado |
| **Apache Guacamole** | Gateway remoto sem cliente (RDP, SSH, VNC pelo navegador) | auto-hospedado |
| **AnyDesk** | Leve e simples para suporte pontual | `anydesk` |
| **TeamViewer** | Muito difundido, uso pessoal gratuito | `teamviewer` |
| **Chrome Remote Desktop** | Acesso simples via conta Google | extensão do Chrome |
| **TightVNC / UltraVNC** | VNC clássico, leve e gratuito | `tightvnc` / `ultravnc` |
| **mRemoteNG** | Gerencia várias conexões (RDP, SSH, VNC) | `mremoteng` |
| **Área de Trabalho Remota (RDP)** | Nativa do Windows (`mstsc`) | já incluída |
| **Quick Assist** | Assistência rápida nativa do Windows | já incluída |
 
> ⚠️ Ferramentas de acesso remoto são alvo frequente de ataques. Use sempre autenticação forte e limite o acesso a quem precisa.
 
---
 
## 📡 Monitoramento, inventário e helpdesk (self-host)
 
Soluções gratuitas e muito usadas por equipes de TI, ideais para rodar em Docker, um servidor ou uma VM.
 
| Ferramenta | Função |
|---|---|
| **Uptime Kuma** | Monitoramento de disponibilidade com alertas, simples e bonito |
| **Zabbix** | Monitoramento completo de servidores, redes e aplicações |
| **LibreNMS** | Monitoramento de rede (SNMP), com descoberta automática |
| **Netdata** | Métricas em tempo real com instalação fácil |
| **Grafana + Prometheus** | Dashboards e coleta de métricas |
| **GLPI** | Inventário de ativos e sistema de chamados (muito usado no Brasil) |
| **Snipe-IT** | Controle de ativos e patrimônio |
| **OCS Inventory** | Inventário automático de hardware e software |
| **osTicket / Zammad** | Sistemas de chamados (helpdesk) |
| **BookStack / Wiki.js** | Base de conhecimento e documentação interna |
 
**Exemplo: Uptime Kuma com Docker**
 
```bash
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma
```
 
Acesse `http://localhost:3001`. Confira a documentação do projeto para a tag de versão recomendada.
 
---
 
## 💽 Backup, clonagem e recuperação
 
| Ferramenta | Uso |
|---|---|
| **Clonezilla** | Clonagem e imagem de discos, gratuito |
| **Macrium Reflect** | Imagem de sistema (verifique a edição disponível atualmente) |
| **AOMEI Backupper** | Backup e clonagem com interface gráfica |
| **Veeam Agent for Windows** | Backup de estações e servidores |
| **TestDisk / PhotoRec** | Recuperação de partições e arquivos apagados |
| **Recuva** | Recuperação simples de arquivos |
| **Disk2vhd** | Virtualização de um disco físico |
| **Duplicati** | Backup criptografado para nuvem e servidores (`duplicati`) |
| **rclone** | Sincroniza e copia arquivos para dezenas de provedores de nuvem (`rclone`) |
| **UrBackup** | Backup cliente/servidor de código aberto |
 
### Regra 3-2-1 de backup
 
- **3** cópias dos dados
- **2** tipos de mídia diferentes
- **1** cópia fora do local (nuvem ou outro site)
---
 
## 🧹 Limpeza e análise de disco
 
| Ferramenta | Função | Pacote Chocolatey |
|---|---|---|
| **WizTree** | Mostra o que ocupa espaço, muito rápido | `wiztree` |
| **TreeSize Free** | Análise de espaço por pastas | `treesizefree` |
| **WinDirStat** | Mapa visual de uso de disco | `windirstat` |
| **Everything** | Busca instantânea de arquivos | `everything` |
| **BleachBit** | Limpeza de arquivos temporários | `bleachbit` |
 
---
 
## 🔐 Segurança, senhas e remoção de malware
 
| Ferramenta | Função |
|---|---|
| **KeePassXC** | Gerenciador de senhas local e open source |
| **Bitwarden** | Gerenciador de senhas com opção de auto-hospedagem |
| **VeraCrypt** | Criptografia de discos e volumes |
| **Malwarebytes** | Análise de malware sob demanda |
| **Microsoft Defender Offline** | Verificação antes da inicialização do Windows |
| **Autoruns** | Auditoria de itens de inicialização |
 
### Remoção de malware sob demanda
 
| Ferramenta | Função | Pacote Chocolatey |
|---|---|---|
| **AdwCleaner** | Remove adware, barras de ferramentas e PUPs | `adwcleaner` |
| **Microsoft Safety Scanner** | Verificador gratuito da Microsoft (válido por 10 dias após o download) | site oficial |
| **Kaspersky Virus Removal Tool** | Verificador gratuito sob demanda | site oficial |
| **ESET Online Scanner** | Verificação online gratuita | site oficial |
| **Malwarebytes** | Detecção e remoção de malware (versão gratuita sob demanda) | `malwarebytes` |
 
---
 
## 🧩 Utilitários extras populares
 
Programas gratuitos, bem avaliados e muito usados no dia a dia do suporte.
 
| Ferramenta | Função | Pacote Chocolatey |
|---|---|---|
| **Ninite** | Instala vários apps de uma vez por um único instalador | <https://ninite.com> |
| **Revo Uninstaller (Free)** | Desinstalação completa de programas | `revo-uninstaller` |
| **WinMerge** | Compara arquivos e pastas | `winmerge` |
| **ShareX** | Capturas de tela, GIFs e gravação com upload automático | `sharex` |
| **Greenshot** | Captura de tela leve com anotações | `greenshot` |
| **FileZilla** | Cliente FTP/SFTP | `filezilla` |
| **VirtualBox** | Máquinas virtuais para testes | `virtualbox` |
| **Draw.io (diagrams.net)** | Diagramas de rede e fluxos | `drawio` |
| **Tabby** | Terminal moderno com SSH e serial | `tabby` |
| **scrcpy** | Espelha e controla Android pelo PC | `scrcpy` |
| **Notepad++** | Editor de texto e logs | `notepadplusplus` |
| **Obsidian / Joplin** | Anotações e documentação pessoal | `obsidian` / `joplin` |
| **Windows Admin Center** | Gerenciamento de servidores Windows (Microsoft) | site oficial |
| **PowerToys** | Utilitários de produtividade da Microsoft | `powertoys` |
 
---
 
## ⌨️ Comandos úteis do Windows
 
### Reparo do sistema
 
```cmd
sfc /scannow
DISM /Online /Cleanup-Image /CheckHealth
DISM /Online /Cleanup-Image /ScanHealth
DISM /Online /Cleanup-Image /RestoreHealth
chkdsk C: /f /r
```
 
### Informações do sistema
 
```cmd
systeminfo
msinfo32
wmic bios get serialnumber
whoami /all
```
 
### Gerenciamento de usuários e políticas
 
```cmd
net user
gpupdate /force
gpresult /r
```
 
### Atalhos de ferramentas administrativas
 
| Comando (Win + R) | Abre |
|---|---|
| `devmgmt.msc` | Gerenciador de Dispositivos |
| `diskmgmt.msc` | Gerenciamento de Disco |
| `services.msc` | Serviços |
| `eventvwr.msc` | Visualizador de Eventos |
| `compmgmt.msc` | Gerenciamento do Computador |
| `gpedit.msc` | Política de Grupo Local |
| `msconfig` | Configuração do Sistema |
| `resmon` | Monitor de Recursos |
| `perfmon` | Monitor de Desempenho |
| `appwiz.cpl` | Programas e Recursos |
| `ncpa.cpl` | Conexões de Rede |
 
---
 
## 📦 Winget (alternativa ao Chocolatey)
 
O **winget** já vem incluído no Windows 10/11 moderno e é mantido pela Microsoft.
 
```powershell
winget search ventoy
winget install Ventoy.Ventoy
winget upgrade --all
winget export -o apps.json
winget import -i apps.json
```
 
| Chocolatey | Winget |
|---|---|
| `choco install pacote -y` | `winget install pacote` |
| `choco upgrade all -y` | `winget upgrade --all` |
| `choco uninstall pacote -y` | `winget uninstall pacote` |
| `choco list` | `winget list` |
| `choco search nome` | `winget search nome` |
 
> Os dois podem conviver na mesma máquina. Muitos técnicos usam o Chocolatey pelo vasto repositório e pelo suporte a automação, e o winget por vir nativo.
 
---
 
## ✅ Boas práticas
 
- 🔎 **Baixe apenas de fontes oficiais** e confira o hash (SHA-256) quando disponível.
- 💾 **Faça backup antes** de qualquer formatação, particionamento ou clonagem.
- 🧪 **Teste em máquina virtual** (VirtualBox, VMware, Hyper-V) antes de aplicar em produção.
- 📝 **Documente** o que foi feito em cada atendimento.
- 🔁 **Mantenha o pendrive Ventoy atualizado** e as ISOs verificadas.
- ⚖️ **Respeite as licenças** dos softwares usados profissionalmente. Algumas ferramentas gratuitas para uso pessoal exigem licença comercial em empresas.
- 🛡️ **Tenha autorização** antes de acessar remotamente ou varrer redes de terceiros.
---
 
## 🤝 Contribuindo
 
Sugestões são bem-vindas!
 
1. Faça um **fork** deste repositório.
2. Crie uma branch: `git checkout -b minha-sugestao`
3. Adicione sua ferramenta com **nome, descrição curta, link oficial e pacote Chocolatey** (se existir).
4. Envie um **Pull Request**.
---
 
## 📜 Licença
 
Este conteúdo está sob a licença **MIT**. As ferramentas listadas pertencem aos seus respectivos autores e têm licenças próprias.
 
---
 
## 🙏 Créditos
 
- [IT-Tools](https://github.com/CorentinTh/it-tools) por [Corentin Thomasset](https://corentin.tech)
- [Ventoy](https://github.com/ventoy/Ventoy)
- [MeshCentral](https://github.com/Ylianst/MeshCentral) por Ylian Saint-Hilaire
- [Chocolatey](https://chocolatey.org)
- [Sysinternals](https://learn.microsoft.com/sysinternals) (Microsoft)
- Comunidade de suporte de TI 💙
---
 
<p align="center">⭐ Se este guia te ajudou, deixe uma estrela no repositório!</p>
 
