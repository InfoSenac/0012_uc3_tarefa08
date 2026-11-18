VirtualBox/VMware:Tela Pequena e Área de Transferencia não Funciona 
Alerta de Segurança: Desligue a Maquina virtual antes de instalar componentes de integração para evitar tranvamento de video.

1. Quando Aplicar (Sintoma)
A VM fica com a tela pequena e quadrada, a resolução não aumenta mesmo maximizando a janela e não é possível copiar e colar texto ou arquivos entre o Windows real e a VM 

2. Ferramentas/Componentes Necessários
* Hardware/Físico:Nenhum - procedimento apenas lógico 
* Software: VirtualBox Guest Additions ou VMware Tools/Open-VM-Tools

3. Passo a Passo Rápido
Primeiro passo objetivo:Ligue a VM, no menu superior clique em Dispositivos > Inserir imagem de CD dos adicionais para Convidado.
Segundo passo objetivo:Dentro da VM, abra o Explorador de Arquivos > Este Computador e execute o VboxWindos Additions.
Terceiro passo:Reinicie a VM quando pedir.

Teste de Validação: Maximize a janela da VM e veja se a tela fica em tela cheia automaticamente.
Depois tente copiar um texto no Windows e colar dentro da VM para confirmar que funcionou.