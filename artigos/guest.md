# Corrigir Resolução Travada e Ativar Área de Transferência Compartilhada com VMware Tools e Guest Additions

> **Alerta de Segurança:** Faça um Snapshot da VM antes de instalar. Não desligue a VM na meio da instalação, pois pode corromper o sistema.

## 1. Quando Aplicar (Sintoma)
AVM fica com a tela pequena e travada em 800x600 ou 1024x768, não aumenta quando maximiza a janela, e o copiar e colar (Ctrl + C /Ctrl + V) entre o PC físico e a VM não funciona. Isso indica que os pacotes de integração do hipervisor não estão instalados.

## 2. Ferramentas/Componentes Necessários
* **Hardware / Físico:** PC com VMware Workstation Pro ou VirtualBox instalado, VM Windows 11 e VM Linux Mint / Ubuntu
* **Software:** VMware Tools (Windows), open-vm-tools (Linux), VirtualBox Guest Additions, terminal do Linux

## 3. Passo a Passo Rápido

1. Lingue a VM Windows 11.
2. No menu do VMware, clique em `VM > Install VMware Tools`.
   ```powershell
   # Comando de diagnóstico - confere se o VMware Tools está rodando
   Get-Service -Name VMTools

3. **Teste de Validação:** Como confirmar que o problema/instrução foi concluído.
Maximize a janela da VM - a resolução deve ajustar sozinha para 1920x1080, sem borda preta.
Copie um texto no pc físico com `Ctrl + C` e cole dentro da VM com `Ctrl + V`, depois faça o contrário (copiar dentro da VM e colar no PC).
Se a tela aumentou e colou nos dois sentidos, o VMware Tools / Guest Additions foi instalado com sucesso.
