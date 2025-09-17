# cisco-router-commands
Comandos CISCO Router

Este repositório contém os comandos básicos para configuração de roteadores Cisco, incluindo tanto a forma longa quanto os atalhos dos comandos.

## Comandos Básicos de Configuração

### 1. Alterar o Nome do Roteador (Hostname)

**Forma longa:**
```
Router> enable
Router# configure terminal
Router(config)# hostname NOVO_NOME
NOVO_NOME(config)# exit
NOVO_NOME#
```

**Atalho:**
```
Router> en
Router# conf t
Router(config)# host NOVO_NOME
NOVO_NOME(config)# exit
NOVO_NOME#
```

### 2. Configurar IP em uma Interface

**Forma longa:**
```
Router> enable
Router# configure terminal
Router(config)# interface gigabitethernet 0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)#
```

**Atalho:**
```
Router> en
Router# conf t
Router(config)# int g0/0
Router(config-if)# ip add 192.168.1.1 255.255.255.0
Router(config-if)# no shut
Router(config-if)# exit
Router(config)#
```

### 3. Atribuir Senha para Acesso Console e Lines VTY

**Forma longa:**
```
Router> enable
Router# configure terminal

! Configurar senha do console
Router(config)# line console 0
Router(config-line)# password SENHA_CONSOLE
Router(config-line)# login
Router(config-line)# exit

! Configurar senha das linhas VTY (Telnet/SSH)
Router(config)# line vty 0 4
Router(config-line)# password SENHA_VTY
Router(config-line)# login
Router(config-line)# exit
Router(config)#
```

**Atalho:**
```
Router> en
Router# conf t

! Console
Router(config)# line con 0
Router(config-line)# pass SENHA_CONSOLE
Router(config-line)# login
Router(config-line)# exit

! VTY
Router(config)# line vty 0 4
Router(config-line)# pass SENHA_VTY
Router(config-line)# login
Router(config-line)# exit
Router(config)#
```

### 4. Atribuir Senha para Modo Exec Privilegiado

**Forma longa:**
```
Router> enable
Router# configure terminal
Router(config)# enable secret SENHA_PRIVILEGIADA
Router(config)# exit
Router#
```

**Atalho:**
```
Router> en
Router# conf t
Router(config)# en sec SENHA_PRIVILEGIADA
Router(config)# exit
Router#
```

### 5. Criptografar Todas as Senhas

**Forma longa:**
```
Router> enable
Router# configure terminal
Router(config)# service password-encryption
Router(config)# exit
Router#
```

**Atalho:**
```
Router> en
Router# conf t
Router(config)# serv pass-enc
Router(config)# exit
Router#
```

### 6. Configurar Banner Apropriado

**Forma longa:**
```
Router> enable
Router# configure terminal
Router(config)# banner motd #
Enter TEXT message.  End with the character '#'.
Somente Acesso Autorizado. Infratores sofrerão as consequências da lei
#
Router(config)# exit
Router#
```

**Atalho:**
```
Router> en
Router# conf t
Router(config)# ban motd #
Enter TEXT message.  End with the character '#'.
Somente Acesso Autorizado. Infratores sofrerão as consequências da lei
#
Router(config)# exit
Router#
```

### 7. Salvar as Configurações

**Forma longa:**
```
Router# copy running-config startup-config
Destination filename [startup-config]? [Enter]
Building configuration...
[OK]
Router#
```

**Atalho:**
```
Router# copy run start
Destination filename [startup-config]? [Enter]
Building configuration...
[OK]
Router#
```

**Alternativa mais simples:**
```
Router# write memory
Building configuration...
[OK]
Router#
```

**Atalho da alternativa:**
```
Router# wr
Building configuration...
[OK]
Router#
```

### 8. Listar as Configurações

**Forma longa:**
```
! Ver configuração atual (running)
Router# show running-config

! Ver configuração salva (startup)
Router# show startup-config

! Ver configuração de uma interface específica
Router# show running-config interface gigabitethernet 0/0

! Ver resumo das interfaces
Router# show ip interface brief
```

**Atalho:**
```
! Configuração atual
Router# sh run

! Configuração salva
Router# sh start

! Interface específica
Router# sh run int g0/0

! Resumo das interfaces
Router# sh ip int br
```

## Exemplo de Configuração Completa

```
Router> enable
Router# configure terminal
Router(config)# hostname ROUTER_EMPRESA
ROUTER_EMPRESA(config)# interface gigabitethernet 0/0
ROUTER_EMPRESA(config-if)# ip address 192.168.1.1 255.255.255.0
ROUTER_EMPRESA(config-if)# no shutdown
ROUTER_EMPRESA(config-if)# exit
ROUTER_EMPRESA(config)# line console 0
ROUTER_EMPRESA(config-line)# password console123
ROUTER_EMPRESA(config-line)# login
ROUTER_EMPRESA(config-line)# exit
ROUTER_EMPRESA(config)# line vty 0 4
ROUTER_EMPRESA(config-line)# password vty123
ROUTER_EMPRESA(config-line)# login
ROUTER_EMPRESA(config-line)# exit
ROUTER_EMPRESA(config)# enable secret privileged123
ROUTER_EMPRESA(config)# service password-encryption
ROUTER_EMPRESA(config)# banner motd #
Somente Acesso Autorizado. Infratores sofrerão as consequências da lei
#
ROUTER_EMPRESA(config)# exit
ROUTER_EMPRESA# copy running-config startup-config
ROUTER_EMPRESA# show running-config
```

## Notas Importantes

- **enable**: Entra no modo privilegiado
- **configure terminal**: Entra no modo de configuração global
- **exit**: Sai do modo atual
- **end**: Sai diretamente para o modo privilegiado
- **?**: Mostra ajuda para comandos disponíveis
- **Tab**: Completa automaticamente os comandos
- **Ctrl+C**: Cancela comando atual
- **Ctrl+Z**: Sai para o modo privilegiado

## Verificações Úteis

```
! Verificar interfaces
Router# show ip interface brief

! Verificar tabela de roteamento
Router# show ip route

! Verificar configuração de uma interface
Router# show interface gigabitethernet 0/0

! Verificar versão do IOS
Router# show version

! Verificar usuários conectados
Router# show users
```
