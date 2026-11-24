# Procedimento Técnico: Erro ao Restaurar Snapshot e Boas Práticas de Backup de Máquinas Virtuais
Aluna: Laíz Flávia Moreira da Costa
Tema: VirtualBox / VMware – Snapshot e Backup de VMs

> **Alerta de Segurança:** Antes de realizar qualquer alteração, desligue a máquina virtual quando necessário e faça um backup dos arquivos importantes. Nunca exclua arquivos de snapshots manualmente.

## 1. Quando Aplicar (Sintoma)
Este procedimento deve ser aplicado quando uma máquina virtual apresenta erros ao restaurar um snapshot, não inicia corretamente ou apresenta falhas após alterações no sistema. Também é indicado para prevenir a perda de dados por meio de backups periódicos.

## 2. Ferramentas/Componentes Necessários
*Hardware / Físico:*

Computador com memória RAM e processador compatíveis.

HD ou SSD com espaço livre suficiente.

HD externo ou outro local seguro para armazenar backups.

*Software:*

Oracle VirtualBox ou VMware.

Sistema operacional instalado na máquina virtual.

Ferramenta de backup.

Explorador de arquivos para localizar os arquivos da VM.

## 3. Passo a Passo Rápido
Verificar se a máquina virtual está desligada e se existe espaço livre no disco.

Abrir o VirtualBox ou VMware e localizar a máquina virtual que apresenta o erro.

Conferir a lista de snapshots e identificar o ponto de restauração desejado.

Verificar se os arquivos da máquina virtual estão disponíveis e se não foram movidos ou excluídos.

Tentar restaurar o snapshot pelo próprio programa, seguindo as opções disponíveis.

Para realizar um backup, desligar a máquina virtual e copiar seus arquivos para um local seguro, preservando a estrutura e os arquivos relacionados aos snapshots.

Caso o erro continue, verificar os registros de funcionamento do programa e identificar possíveis falhas de armazenamento ou arquivos ausentes.

Teste de Validação: Iniciar a máquina virtual e verificar se o sistema operacional funciona normalmente, se os arquivos estão acessíveis e se o backup foi armazenado corretamente.

Resultado esperado: A máquina virtual deve voltar a funcionar corretamente ou ter seus dados protegidos por meio de um backup seguro, reduzindo os riscos de perda de informações.