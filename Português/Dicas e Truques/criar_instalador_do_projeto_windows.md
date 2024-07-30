# Como Configurar o Inno Setup para Criar um Instalador para Aplicações Flutter no Windows


* Para criar um instalador de uma aplicação Flutter para Windows, você pode usar o Inno Setup, uma ferramenta popular para criar instaladores no Windows. O Inno Setup ajuda a empacotar e distribuir sua     aplicação de maneira profissional. Abaixo está um guia passo a passo para configurar o Inno Setup e criar um instalador para o seu build do Flutter.

* Pré-requisitos
  Inno Setup Instalado: Faça o download e instale o Inno Setup a partir do site oficial.
  [Link](https://jrsoftware.org/isdl.php#stable)

* Passos para Criar o Instalador
  Prepare o Build da Aplicação Flutter

* Primeiro, você precisa gerar a pasta de build da sua aplicação Flutter. Abra o terminal e navegue até o diretório do seu projeto Flutter, então execute o comando:
  - flutter build windows --release
  Isso criará um diretório build\windows\runner\Release que contém o executável da sua aplicação e todos os arquivos necessários.

* Crie um Script Inno Setup
  Inno Setup usa scripts .iss para definir como o instalador deve ser configurado. Abra o Inno Setup e crie um novo script. Você pode usar o assistente para gerar um script básico e então personalizá-lo.
  Abaixo está um exemplo básico de script Inno Setup para uma aplicação Flutter:

```
  [Setup]
  AppName=ProjectName
  AppVersion=1.0
  DefaultDirName={pf}\ProjectName
  DefaultGroupName=ProjectName
  OutputDir=output
  OutputBaseFilename=ProjectName
  Compression=lzma
  SolidCompression=yes
  
  [Files]
  Source: "PATH-PROJECT\build\windows\x64\runner\Release\*"; DestDir: "{app}"; Flags: ignoreversion recursesubdirs createallsubdirs
  
  [Icons]
  Name: "{group}\ProjectName"; Filename: "{app}\ProjectName.exe"
  Name: "{group}\Uninstall ProjectName"; Filename: "{uninstallexe}"

  [Run]
  Filename: "{app}\MinhaAplicacao.exe"; Description: "{cm:LaunchProgram,MinhaAplicacao}"; Flags: nowait postinstall skipifsilent
```

# Explicação dos principais blocos:
  
  [Setup]: Define as configurações básicas do instalador, como nome do aplicativo, versão e diretório padrão.
  [Files]: Especifica os arquivos que serão incluídos no instalador e seus destinos.
  [Icons]: Cria atalhos no menu Iniciar e na área de trabalho.
  [Run]: Define o que deve ser executado após a instalação, como iniciar a aplicação.


* Compile o Script
  Após criar e salvar o script .iss, clique em "Compile" no Inno Setup para gerar o instalador. O Inno Setup irá criar um arquivo .exe no diretório especificado (OutputDir) que pode ser distribuído e usado para instalar a sua aplicação.

* Teste o Instalador
  Execute o instalador gerado em um ambiente de teste para garantir que tudo funcione como esperado. Verifique se a aplicação é instalada corretamente e se todos os arquivos e atalhos são criados conforme  especificado.

* Distribua o Instalador
  Após testar e confirmar que o instalador funciona corretamente, você pode distribuir o arquivo .exe para os usuários finais. Eles poderão instalar sua aplicação com facilidade usando o instalador criado.

* Dicas Adicionais
  Documentação: Consulte a documentação oficial do Inno Setup para mais detalhes e opções avançadas.
  Customização: Você pode personalizar ainda mais o instalador adicionando telas de instalação personalizadas, idiomas e muito mais.