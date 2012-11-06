# Hiperorgânicos OSC
Arquivos e instruções básicas para o setup da conectividade OSC (Open Sound Control) que será utilizada no open lab

---

### 1: download do OscGroups

Todos os arquivos estão neste repositório no diretório OscGroups, mas vocês podem baixar pelos links:

- Windows e Mac: http://code.google.com/p/oscgroups/downloads/list
- Ubuntu: http://devolts.org/oscgroupslinux.tar.gz (compilados pelo glerm)

### 2: instalação

- Windows: descompactar arquivos
- Mac e Ubuntu: descompactar e copiar binarios para pasta **/usr/bin**

### 3: entrando na rede

Antes de abrir Puredata Processing etc, é preciso abrir o cliente do OscGroups e logar na rede

     OscGroupClient <serveraddress> <serverport> <localtoremoteport> <localtxport> <localrxport> <username> <password> <groupname> <grouppassword>

Vamos usa as portas padrão do OscGroups, de 22241 a 22244

##### Windows

Pelo prompt de comando, acesse o diretorio onde os binarios foram extraidos e abra o cliente com exatamente estes parametros (exceto username e password, que voces vao escolher)

    cd Downloads
    cd oscgroups
    OscGroupClient hiperorganicos.tk 22242 22241 22243 22244 <username> <password> hiperorganicos nano
    
##### Mac e Ubuntu

Pelo terminal, abra o cliente com exatamente estes parametros (exceto username e password, que voces vao escolher)

    OscGroupClient hiperorganicos.tk 22242 22241 22243 22244 <username> <password> hiperorganicos nano
    
    
### 4: testando conectividade

A vantagem do OscGroups é o broadcast de dados: você envia mensagens pro seu próprio IP 127.0.0.1 / localhost na porta 22243,
e o servidor envia para todos os pontos conectados; assim como todas mensagens enviadas pelos outros pontos chegam pra você na porta 22244.

Na pasta PD deste repositório tem um patch de PD-extended para testarmos a conectividade.

### 5: modelo das mensagens OSC

Para facilitar o fluxo de dados, sugerimos o modelo **/user/interface** para as mensagens OSC,
enviando valores de **0.0** a **1.0**, algo como o exemplo abaixo:

    /guto/breathing       0.51
    /guto/ha              0.55
    /barbara/kinect_x     0.67
    /barbara/kinect_y     1.00
    /barbara/kinect_z     0.90
    ...
    
### 6: IP / Domínio

#### hiperorganicos.tk
