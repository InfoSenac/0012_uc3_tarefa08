# VirtualBox / VMware: Erro ao restaurar Snapshot e boas práticas de backup de VMs

> **Alerta de Segurança:** Desligue completamente a VM e faça uma cópia manual da pasta do disco virtual antes de alterar arquivos de configurações ou snapshots. Evite acumular muitos snapshots, pois isso causa degradação de desempenho e risco de corrupção em cadeia caso um disco pai seja danificado.

## 1. Quando Aplicar (Sintoma)

Quando a VM apresentar falha ao usar um snapshot e exibir mensagens de erro, arquivos corrompidos ou quando precisa garantir a integridade dos dados antes de uma atualização importante.

## 2. Ferramentas/Componentes Necessários

* **Hardware / Físico:** Espaço livre em disco (HD/SSD) suficiente para armazenar clones completos e memória RAM adequada.
* **Software:** VirtualBox ou VMware e gerenciador de arquivos da máquina hospedeira.

## 3. Passo a Passo Rápido

1. Feche totalmente o VirtualBox ou VMware e verifique no gerenciador de tarefas se não há nenhum processo em aberto.
2. Localize a pasta da VM no computador hospedeiro e copie os arquivos principais para um diretório externo de backup.
3. Abra o **Gerenciador de Snapshots** (*Snapshots* no VirtualBox / *Snapshot Manager* no VMware), verifique se há snapshots com avisos de erro e remova apenas os vínculos corrompidos ou reverta (*Restaurar / Reverter*) um estado com segurança.
4. Para escolher a melhor estratégia de proteção e recuperação, existe três recursos:
   **Snapshot:** ponto de restauração rápido, mas dependente do disco base (não substitui backup).
   **Clone Completo (*Full Clone*):** cria uma cópia totalmente independente da VM.
   **Exportar Appliance (`.ova` / `.ovf`):** gera um pacote portátil ideal para backup externo e migração entre hipervisores.

   ```bash
   VBoxManage snapshot "Nome-da-VM" list
   VBoxManage snapshot "Nome-da_VM" restore "Nome-do-Snapshot"
   ```

5. **Teste de Validação:** Inicie a máquina virtual restaurada ou clonada e confirme se o sistema operacional abrirá normalmente sem alertas de disco ou perda de arquivos.