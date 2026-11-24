## VMware: VM Windows ou Linux sem acesso à rede local ou internet (NAT vs. Bridge)
> **Alerta de Segurança:**  Alterações na configuração de rede podem expor a VM à rede local. Antes de modificar adaptadores virtuais, faça snapshots e backups para evitar perda de dados ou indisponibilidade.
## 1. Quando Aplicar (Sintoma)
Utilize este procedimento quando uma máquina virtual (VM) Windows ou Linux, executada no VMware Workstation, não conseguir acessar a rede local ou a internet.
## 2. Ferramentas/Componentes Necessários
* **Hardware / Físico:** Computador host, placa de rede Ethernet ou Wi-Fi e memória RAM suficiente para executar a VM.
* **Software:**  VMware Workstation Pro/Player, Windows ou Linux instalado na VM e Virtual Network Editor.
## 3. Passo a Passo Rápido
1. Desligue a VM e acesse VM > Settings > Network Adapter.
2. Habilite Connected e Connect at power on.
3. Selecione o modo de rede adequado:
    - NAT: compartilha a conexão de internet do host.
    - Bridge: conecta a VM diretamente à rede física, utilizando IP próprio.
4. No modo NAT, verifique se os serviços VMware DHCP Service e VMware NAT Service estão ativos no host. No modo Bridge, confirme o adaptador físico correto no Virtual Network Editor.
5. Inicie a VM e renove o endereço IP.
    * Windows: ``bash`` ``ipconfig /release`` ``ipconfig /renew`` ``ipconfig /all``
    * Linux: ``bash`` ``ip addr`` ``ip route`` ``sudo dhclient -v``
6. Teste de Validação: Verifique o endereço IP, o gateway e a conectividade externa:
    * Teste: ``bash`` ``ping 8.8.8.8`` ``ping google.com``
Se o primeiro teste funcionar e o segundo falhar, investigue a configuração DNS. Se ambos funcionarem, o acesso à internet foi restabelecido.
!!!
