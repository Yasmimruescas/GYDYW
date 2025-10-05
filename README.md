# 🛡️ Antiransomware

## 📖 Descrição Geral

Aplicação desenvolvida em **C\# (.NET 8)** que tem como objetivo **detectar e reagir a comportamentos suspeitos de ransomware em tempo real**.

O monitor cria **honeypots** (arquivos “isca” estrategicamente posicionados) e utiliza o **`FileSystemWatcher`** para monitorar continuamente modificações em arquivos críticos do sistema. Quando uma alteração maliciosa é detectada, o sistema tenta **suspender, analisar e eliminar processos suspeitos**, coletando **dumps de memória** para fins forenses.

-----

## ⚙️ Funcionalidades Principais

  * 🪤 **Criação de Honeypots:** Cria arquivos isca em pastas públicas e temporárias para atrair e detectar o ransomware.
  * 👁️ **Monitoramento em Tempo Real:** Monitora as alterações de arquivos usando o `FileSystemWatcher`.
  * 🔐 **Verificação de Integridade:** Realiza verificações periódicas de integridade usando **hash SHA-256** nos arquivos monitorados.
  * 📊 **Detecção de Anomalias:** Identifica atividades suspeitas baseadas na frequência e no padrão das alterações.
  * 🧩 **Resposta Rápida:** Tenta suspender e analisar processos suspeitos, gerando **dumps de memória** antes da finalização.
  * ✅ **Whitelist de Processos:** Inclui uma lista de permissão (whitelist) para processos legítimos do sistema, evitando falsos positivos.
  * 🗂️ **Coleta de Evidências:** Armazena logs, manifestos e dumps para análise forense posterior.

-----

## 💻 Requisitos

| Categoria | Requisito | Notas |
| :--- | :--- | :--- |
| **Sistema Operacional** | Windows 10 ou 11 | Compatibilidade com as APIs do sistema de arquivos. |
| **Compilação** | .NET 8.0 SDK | Necessário para compilar o projeto do código-fonte. |
| **Execução** | .NET Runtime | Necessário para rodar o executável (`.exe`). |

-----

## 🛠️ Compilação (Build)

### 1\. Criando e Compilando Manualmente

Para configurar o projeto do zero:

```bash
# 1. Crie um novo projeto de console
dotnet new console -n AntiRansomMonitorWithHoneypots

# 2. Acesse o diretório do projeto
cd AntiRansomMonitorWithHoneypots

# 3. Substitua o arquivo Program.cs pelo código-fonte
#    (Inclua o código da aplicação aqui)

# 4. Compile o projeto
dotnet build
```

### 2\. Compilando o Projeto Existente

Se o repositório já contiver o arquivo `.csproj`:

```bash
dotnet build
```

### 3\. Teste Rápido

Para compilar e executar o projeto diretamente:

```bash
dotnet run
```

-----

## 💿 Instalação

1.  **Obtenha o Executável:** Compile o projeto ou use o arquivo `.exe` pré-compilado.

2.  **Crie o Diretório de Ferramentas:** Copie o executável gerado para o caminho:
    `C:\Ferramentas\AntiRansom\`

3.  **Crie o Diretório de Logs (Como Administrador):** Crie a pasta **`C:\Temp`** (necessita de permissões de administrador):

    ```powershell
    mkdir C:\Temp
    ```

-----

## ▶️ Execução

O monitor **deve ser executado com permissões de administrador** para garantir seu funcionamento completo, especialmente nas funções de suspensão de processos e geração de *dumps*.

### Formas de Execução

  * **Pelo Explorer:** Navegue até o executável, clique com o **botão direito** e selecione **"Executar como administrador"**.

  * **Pelo Terminal/Prompt:** Acesse o diretório e execute:

    ```powershell
    cd C:\Ferramentas\AntiRansom\
    .\AntiRansomMonitorWithHoneypots.exe
    ```

-----

## 🔍 O que acontece ao iniciar

Ao ser iniciado, o programa realiza as seguintes ações no sistema:

| Ação | Localização | Notas |
| :--- | :--- | :--- |
| **Criação de Honeypots** | `C:\Users\Public\Desktop` | Isca em uma pasta de alto valor. |
| **Criação de Honeypots** | `C:\Users\Public\Documents` | Isca em uma pasta de alto valor. |
| **Criação de Honeypots** | `%TEMP%\honeypots` | Isca em uma pasta temporária. |
| **Manifesto** | `C:\Temp\honeypot_manifest.json` | Registro dos hashes e locais dos honeypots. |
| **Logs** | `C:\Temp\security_log.txt` | Logs de monitoramento e detecção. |
| **Dumps** | `C:\Temp\dumps\` | Diretório para despejos de memória (*dumps*) de processos suspeitos. |

-----

## ⏹️ Encerrando a Execução

Para parar o monitor, utilize uma das opções:

  * Pressione **`CTRL + C`** na janela do terminal onde o programa está em execução.
  * Feche a janela do console.

-----

## ⚠️ Recomendações Importantes

  * **Execute como Administrador:** É fundamental executar o programa **como administrador** para que as etapas de **suspensão de processos** e **geração de *dumps*** funcionem corretamente.
  * **Modo de Execução Normal:** Em execução sem privilégios elevados, o monitor pode falhar ao tentar suspender processos ou gerar *dumps* de memória.
  * **Uso:** Use esta ferramenta **apenas em ambientes de teste, acadêmicos ou laboratórios controlados**.

-----

## 🧩 Estrutura de Detecção e Resposta

O ciclo de vida do monitoramento segue a sequência abaixo:

1.  **Criação de Honeypots**
2.  **Monitoramento Contínuo**
3.  **Verificação de Integridade**
4.  **Detecção de Anomalias**
5.  **Suspensão de Processos**
6.  **Geração de Dumps**
7.  **Finalização**
8.  **Registro e Preservação de Evidências**

-----

## 🧑‍🔬 Equipe de Desenvolvimento

**Grupo DYGYW**
