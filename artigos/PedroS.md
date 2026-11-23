# Linux Guest (VirtualBox / VMware): Erro de permissão ao acessar Pastas Compartilhadas
**Alerta de segurança:**Crie um Snapshot da máquina virtual e faça backup da pasta no sistema Host para salvar o estado atual do sistema Linux e evitar a perda de arquivos.
## Quando Aplicar (Sintoma)
Este procedimento deve ser aplicado quando ocorre um problema lógico de privilégios no sistema de arquivos, no qual o Linux Guest monta a pasta compartilhada pertencente exclusivamente ao usuário root, bloqueando o acesso do usuário comum com o erro "Permission denied" e exigindo a configuração manual de grupos ou parâmetros de montagem.
## Ferramentas/Componentes Necessários
- Hardware / Físico: Computador Hospedeiro,memórioa RAM e armazenamento com capacidade sufciente para realizar o procedimento.
- Software: VirtualBox/VMware, sistema operacional Linux e utilitários do sistema Linux.
## Passo a Passo Rápido
1. Primeiro Passo Objetivo: Diagnóstico do Erro
Abra o terminal do Linux Guest e verifique as permissões atuais do ponto de montagem e os grupos do seu usuário para confirmar o bloqueio.
- Comando de diagnóstico (Permissões):
ls -ld /media/sf_* /mnt/hgfs
- Comando de diagnóstico (Usuário):
id
- O que observar: Se a pasta pertencer ao usuário root e ao grupo vboxsf (sem que vboxsf apareça na lista do comando id), ou se o diretório /mnt/hgfs estiver inacessível, o bloqueio lógico está confirmado.
2. Segundo Passo Objetivo: Correção das Permissões
Aplique o comando correspondente ao virtualizador que você está utilizando para liberar o acesso ao seu usuário padrão.
- Se usar Oracle VirtualBox:
Adicione seu usuário ao grupo vboxsf e reinicie a sessão da máquina virtual:
sudo usermod -aG vboxsf $USER
- Se usar VMware:
Monte a pasta compartilhada liberando o acesso para usuários comuns com o parâmetro allow_other:
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other -o uid=1000,gid=1000
3. Teste de validação 
Confirme que o problema foi resolvido testando o acesso de leitura e escrita diretamente na pasta compartilhada sem usar sudo.
- Listar os arquivos da pasta: 
ls -la /media/sf_<nome_da_pasta>    No VirtualBox
ls -la /mnt/hgfs/<nome_da_pasta>    No VMware
- Testar criação de arquivo: 
touch /media/sf_<nome_da_pasta>/teste.txt
- Resultado esperado: O terminal deve exibir os arquivos exixstentes e criar o arquivo "teste.txt" sem retornar a mensagem "Permission denied".
