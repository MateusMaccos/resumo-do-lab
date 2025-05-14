# Criação e Configuração de Máquina Virtual no Microsoft Azure

Este documento descreve o processo de criação e configuração de uma máquina virtual (VM) na plataforma Microsoft Azure.

## Pré-requisitos
- Conta ativa no Microsoft Azure (conta gratuita ou paga)
- Acesso ao portal Azure (https://portal.azure.com)
- Nível de permissão adequado para criar recursos

## Processo de Criação

### 1. Acessar o Portal Azure
- Faça login no [Portal Azure](https://portal.azure.com)

### 2. Iniciar o processo de criação
- No menu principal, selecione "Criar um recurso"
- Escolha "Máquina Virtual" na seção de Computação ou pesquise por "Máquina Virtual"

### 3. Configurações básicas
Preencha as informações básicas:
- **Assinatura**: Selecione a assinatura Azure a ser utilizada
- **Grupo de recursos**: Crie um novo ou selecione um existente
- **Nome da máquina virtual**: Defina um nome único
- **Região**: Selecione a região geográfica para hospedar sua VM
- **Opções de disponibilidade**: Configure conforme necessidade de alta disponibilidade
- **Imagem**: Selecione o sistema operacional (Windows Server, Linux distribuições, etc.)
- **Tamanho**: Escolha o tamanho da VM conforme requisitos de CPU, memória e desempenho

### 4. Configuração de autenticação
- Para VMs Linux:
  - Método de autenticação: Chave SSH ou senha
  - Nome de usuário
  - Chave SSH pública ou senha
- Para VMs Windows:
  - Nome de usuário
  - Senha

### 5. Configuração de portas de entrada
- Selecione quais portas serão abertas (ex: HTTP 80, HTTPS 443, SSH 22, RDP 3389)
- Considere a segurança e abra apenas as portas necessárias

### 6. Configurações adicionais
- Discos:
  - Tipo de disco do SO (Standard HDD, Standard SSD, Premium SSD)
  - Opção para adicionar discos de dados
- Rede:
  - Configuração de rede virtual
  - Grupo de segurança de rede
- Gerenciamento:
  - Opções de monitoramento e diagnósticos
  - Identidade gerenciada (opcional)

### 7. Revisão e criação
- Revise todas as configurações
- Clique em "Criar" para iniciar a implantação
- Aguarde o processo de implantação ser concluído (pode levar alguns minutos)

## Configuração pós-criação

### 1. Conectar à VM
- **Para VMs Linux**: Use SSH com o comando fornecido no portal
- **Para VMs Windows**: Use RDP baixando o arquivo de conexão

### 2. Configurações iniciais
- Atualize o sistema operacional
- Instale softwares necessários
- Configure firewall conforme necessário

### 3. Gerenciamento contínuo
- Monitore o desempenho através do Azure Monitor
- Configure backups conforme necessário
- Gerencie custos através do Cost Management

## Considerações importantes
- Sempre desligue a VM quando não estiver em uso para evitar custos desnecessários
- Considere usar conjuntos de disponibilidade para cargas de trabalho críticas
- Configure alertas para monitorar o uso de recursos e custos

## Documentação oficial
[documentação oficial do Azure](https://docs.microsoft.com/azure/virtual-machines/)
