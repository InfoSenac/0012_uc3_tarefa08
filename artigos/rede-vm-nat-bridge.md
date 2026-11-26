# VMware / Oracle VirtualBox: VM Windows ou Linux sem acesso à rede local ou internet (NAT, Bridge e Host-Only)
>**Alerta de Segurança:** Alterações na configuração de rede podem expor a VM à rede local. Antes de modificar adaptadores virtuais, faça snapshots e backups para evitar perda de dados ou indisponibilidade.
## 1. Quando Aplicar (Sintoma)
Utilize este procedimento quando uma máquina virtual (VM) Windows ou Linux, executada no VMware Workstation ou Oracle VirtualBox, não conseguir acessar a rede local ou a internet, ou apresentar problemas de conectividade entre o host e outras máquinas virtuais.

## 2. Ferramentas/Componentes Necessários
- **Hardware / Físico:** 
    - Computador host
    - Placa de rede Ethernet ou Wi-Fi 
    - Memória RAM suficiente para executar a VM.
- **Software:**
    - VMware Workstation Pro/Player.
    - Oracle VirtualBox.
    - Windows ou Linux instalado na VM.
    - VMware Virtual Network Editor.
    - Oracle VirtualBox Manager (Configurações de Rede).
    - Serviços e componentes de rede:
    - VMware DHCP Service.
    - VMware NAT Service.
    - Adaptadores de rede virtuais do VMware e VirtualBox.

## 3. Passo a Passo Rápido

- 3.1. VMware Workstation
Desligue a VM e acesse VM > Settings > Network Adapter.
Habilite as opções Connected e Connect at power on.
Selecione o modo de rede adequado:

    - NAT: Compartilha a conexão de internet do host, permitindo que a VM acesse redes externas por meio do host.
    - Bridge: Conecta a VM diretamente à rede física, utilizando um endereço IP próprio, fornecido pela rede local.
    - Host-Only: Cria uma rede isolada entre o host e as VMs, permitindo a comunicação entre eles, mas sem acesso direto à internet.

No modo NAT, verifique se os serviços VMware DHCP Service e VMware NAT Service estão ativos no host. No modo Bridge, confirme se o adaptador físico correto está selecionado no Virtual Network Editor.
Inicie a VM e renove o endereço IP.

- 3.2. Oracle VirtualBox
Desligue a VM e acesse Configurações > Rede.
Selecione a aba Adaptador 1 e habilite a opção Habilitar Placa de Rede.
Marque a opção Cabo conectado.
No campo Conectado a, selecione o modo de rede adequado:

    - NAT: Compartilha a conexão de internet do host, permitindo que a VM acesse a internet por meio do host.
    - Placa em modo Bridge: Conecta a VM diretamente à rede física, utilizando um endereço IP próprio na rede local.
    - Placa exclusiva de hospedeiro (Host-Only): Cria uma rede isolada entre o host e as VMs, permitindo comunicação entre eles, mas sem acesso direto à internet.

No modo Bridge, selecione a interface física correta (Ethernet ou Wi-Fi) no campo Nome.
No modo Host-Only, confirme se existe um adaptador Host-Only configurado no VirtualBox e se o DHCP está habilitado, caso seja necessário distribuir endereços IP automaticamente.
Salve as configurações, inicie a VM e renove o endereço IP.

- 3.3. Renovação de IP e Testes de Conectividade

Após configurar o adaptador de rede, execute os comandos correspondentes ao sistema operacional da VM.

Windows:

```bash
ipconfig /release
ipconfig /renew
ipconfig /all
```

Linux:

```bash
ip addr
ip route
sudo dhclient -v
```

- 3.4. Teste de Validação

Verifique o endereço IP, o gateway padrão e a conectividade externa.

Teste de conectividade IP:

```bash
ping 8.8.8.8
```

Teste de resolução DNS:

```bash
ping google.com
```

**Interpretação dos resultados:**

- Se o primeiro teste funcionar e o segundo falhar, investigue a configuração DNS.
- Se ambos funcionarem, o acesso à internet foi restabelecido.
- Se ambos falharem, verifique o endereço IP, a máscara de rede, o gateway, o DHCP e a configuração do adaptador virtual.
- No modo Host-Only, a ausência de acesso à internet é esperada. Valide apenas a comunicação entre o host e as VMs.