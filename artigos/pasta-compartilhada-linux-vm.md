# Configurar pasta compartilhada do Windows em uma VM Linux no VMware

> **Alerta de Segurança:** Compartilhe apenas pastas necessárias e conceda acesso somente a usuários autorizados.

## 1. Quando Aplicar (Sintoma)
Aplique este procedimento quando o Linux da máquina virtual não conseguir acessar uma pasta do Windows configurada no VMware.
Ele cobre a ativação do recurso, a instalação das ferramentas no Linux e a montagem da pasta.

## 2. Ferramentas/Componentes Necessários
* **Hardware / Físico:** Computador com Windows e máquina virtual Linux.
* **Software:** VMware Workstation, VMware Tools ou `open-vm-tools`.

## 3. Passo a Passo Rápido
1. Desligue a VM. Em **VM Settings > Options > Shared Folders**, habilite o recurso, adicione a pasta do Windows e marque **Enable this share**.
2. Inicie o Linux e instale as ferramentas, se ainda não estiverem instaladas:
   ```bash
   sudo apt update && sudo apt install open-vm-tools open-vm-tools-desktop
   ```
3. Crie o ponto de montagem e monte as pastas compartilhadas:
   ```bash
   sudo mkdir -p /mnt/hgfs
   sudo vmhgfs-fuse .host:/ /mnt/hgfs
   ```
4. **Teste de Validação:** Execute `ls /mnt/hgfs` e confirme que o nome da pasta compartilhada aparece.
