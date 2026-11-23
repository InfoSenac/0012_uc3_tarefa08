
# VirtualBox / VMware: Tela pequena e falha ao copiar/colar

**Alerta de Segurança:** Salve seu trabalho antes de alterar as configurações da máquina virtual.

## 1. Quando Aplicar (Sintoma)
Aplicar quando a máquina virtual apresentar tela pequena, resolução limitada ou falhas na transferência de textos entre o computador físico e o virtual.

## 2. Ferramentas/Componentes Necessários
- **Hardware:** Computador com memória RAM e armazenamento disponíveis.
- **Software:** VirtualBox ou VMware, Guest Additions ou VMware Tools.
- **Sistema:** Windows ou Linux instalado na máquina virtual.

## 3. Passo a Passo Rápido
1. Identificar o virtualizador utilizado e iniciar a máquina virtual.
2. Instalar as ferramentas de integração correspondentes:
   - **VirtualBox:** Dispositivos > Inserir Imagem de CD dos Adicionais para Convidado.
   - **VMware:** VM > Install VMware Tools.
3. No Linux, para VMware, instalar os componentes:

   ```bash
   sudo apt update
   sudo apt install open-vm-tools open-vm-tools-desktop -y
   ```

4. Ativar os recursos de integração:
   - **VirtualBox:** Área de Transferência Compartilhada > Bidirecional.
   - **VMware:** Guest Isolation > Enable copy and paste.
5. Reiniciar a máquina virtual para aplicar as alterações.

## 4. Como Validar (Teste Final)
- **Teste 1:** Verificar se a resolução da tela acompanha o tamanho da janela.
- **Teste 2:** Testar a cópia e colagem de textos entre o computador físico e a máquina virtual.
