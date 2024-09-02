Para garantir que o script de monitoramento de rede e detecção de ataques seja executado em segundo plano desde a inicialização da máquina, você pode configurar o Windows Task Scheduler para executar o script PowerShell automaticamente. Aqui está um guia passo a passo para fazer isso:

### 1. **Crie o Script PowerShell**

Salve o script PowerShell que você criou, por exemplo, como `Monitoramento.ps1`.

### 2. **Crie uma Tarefa no Agendador de Tarefas**

1. **Abra o Agendador de Tarefas:**
   - Pressione `Win + R`, digite `taskschd.msc` e pressione `Enter`.

2. **Crie uma Nova Tarefa:**
   - No painel direito, clique em "Criar Tarefa".

3. **Configurar Geral:**
   - Dê um nome para a tarefa, como "Monitoramento de Rede".
   - Marque a opção "Executar com privilégios mais altos" para garantir que a tarefa tenha permissões necessárias.

4. **Configurar Disparadores:**
   - Vá para a guia "Disparadores" e clique em "Novo".
   - Selecione "Ao iniciar o computador" no menu suspenso "Iniciar a tarefa".
   - Clique em "OK" para salvar o disparador.

5. **Configurar Ações:**
   - Vá para a guia "Ações" e clique em "Novo".
   - Em "Ação", selecione "Iniciar um programa".
   - Em "Programa/script", digite `powershell.exe`.
   - Em "Adicionar argumentos (opcional)", digite o seguinte:
     ```plaintext
     -File "C:\Caminho\Para\Seu\Script\Monitoramento.ps1"
     ```
     Substitua `"C:\Caminho\Para\Seu\Script\Monitoramento.ps1"` pelo caminho real onde você salvou seu script.

6. **Configurar Condições e Configurações:**
   - Você pode ajustar as condições e configurações conforme necessário, mas as configurações padrão geralmente são suficientes.

7. **Salvar a Tarefa:**
   - Clique em "OK" para salvar a tarefa.

### 3. **Testar a Tarefa**

Para garantir que a tarefa foi configurada corretamente:

1. **Inicie o Agendador de Tarefas:**
   - Vá para "Biblioteca do Agendador de Tarefas".

2. **Encontre sua Tarefa:**
   - Encontre a tarefa "Monitoramento de Rede" na lista.

3. **Execute a Tarefa Manualmente:**
   - Clique com o botão direito na tarefa e selecione "Executar" para verificar se o script funciona conforme o esperado.

4. **Reinicie o Computador:**
   - Reinicie o computador para confirmar se a tarefa é executada automaticamente na inicialização.

Com essas etapas, seu script PowerShell deve iniciar automaticamente em segundo plano sempre que a máquina for inicializada.
