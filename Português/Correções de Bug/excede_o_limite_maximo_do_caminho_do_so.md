# Como Habilitar Nomes Longos de Arquivos no Windows 10


A partir do Windows 10 versão 1803, é possível utilizar nomes de arquivos com até 32.767 caracteres, uma melhoria significativa em relação ao limite anterior de 260 caracteres. Para aproveitar essa funcionalidade, você precisa ativar o suporte a caminhos longos. Veja como fazer isso:

# 1 - Opção 1: Via Política de Grupo (GPO)
  * Abra o Editor de Políticas de Grupo : 

  * Pressione Win + R para abrir a caixa de diálogo Executar.
  * Digite gpedit.msc e pressione Enter.
  * Navegue até a configuração necessária:
  
  * Vá para Configuração do Computador > Modelos Administrativos > Sistema > Sistema de Arquivos.
  * Ative o suporte a caminhos longos:
  
  * Encontre e clique duas vezes na política Ativar caminhos longos do NTFS.
  * Selecione Habilitado e clique em OK.
  * Reinicie o computador para que as alterações entrem em vigor.

# 2 - Opção 2: Via Editor de Registro
  * Inicie o Editor de Registro:

  * Pressione Win + R para abrir a caixa de diálogo Executar.
  * Digite regedit e pressione Enter.
  * Navegue até a chave de registro:
  
  * Vá para HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem.
  * Modifique o valor de LongPathsEnabled:

  * Clique duas vezes em LongPathsEnabled.
  * Defina o valor como 1 e clique em OK.
  * Reinicie o computador para aplicar as mudanças


  