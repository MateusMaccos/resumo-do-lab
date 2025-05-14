# Configurando Recursos e Dimensionamentos em Máquinas Virtuais na Azure

Este guia fornece instruções sobre como configurar e dimensionar recursos para máquinas virtuais (VMs) no Microsoft Azure, garantindo desempenho otimizado e custo-efetividade.

## 📌 Índice
- [Pré-requisitos](#pré-requisitos)
- [Selecionando a Série de VM Adequada](#selecionando-a-série-de-vm-adequada)
- [Configurando CPU e Memória](#configurando-cpu-e-memória)
- [Gerenciamento de Discos (SSD/HDD)](#gerenciamento-de-discos-ssdhdd)
- [Redimensionamento de VMs](#redimensionamento-de-vms)
- [Configuração de Rede Virtual (VNet)](#configuração-de-rede-virtual-vnet)
- [Monitoramento e Autoescala](#monitoramento-e-autoescala)
- [Melhores Práticas](#melhores-práticas)

---

## Pré-requisitos
✔ **Conta ativa no Azure** (com permissões de contribuidor ou owner)  
✔ **Assinatura válida** (Pay-As-You-Go, Enterprise, ou Free Trial)  
✔ **Azure CLI** ou **Portal Azure** configurado  

---

## Selecionando a Série de VM Adequada
O Azure oferece várias séries de VMs para diferentes cargas de trabalho:

| Série          | Caso de Uso                     | Exemplo de VM |
|----------------|--------------------------------|--------------|
| **B**         | Cargas variáveis (burst)       | B2s         |
| **D**         | Propósito geral               | D4s_v3      |
| **E**         | Memória otimizada             | E4s_v3      |
| **F**         | Computação otimizada          | F2s_v2      |
| **NC/NV**     | GPU (IA/processamento gráfico)| NC6s_v3     |

🔹 **Como selecionar?**  
Acesse o [Portal Azure](https://portal.azure.com) > **Criar VM** > Escolha a série conforme sua necessidade.

---

## Configurando CPU e Memória
- **Tamanhos flexíveis**: Algumas séries permitem seleção personalizada de vCPUs e RAM.  
- **Recomendação**: Use o [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/) para estimar custos antes de definir recursos.

### Comando Azure CLI para listar tamanhos disponíveis:
```bash
az vm list-sizes --location eastus --output table
```

---

## Gerenciamento de Discos (SSD/HDD)
| Tipo de Disco  | Latência | Indicado para           |
|---------------|----------|-------------------------|
| **HDD Standard** | Alta    | Backup/dados raros      |
| **SSD Standard** | Média    | Servidores de teste     |
| **SSD Premium**  | Baixa    | Produção (SQL, SAP)     |

🔹 **Expandindo um disco**:  
1. No Portal Azure, vá para **Discos** > Selecione o disco anexado à VM.  
2. Aumente o tamanho e reinicie a VM.

---

## Redimensionamento de VMs
Para alterar o tamanho de uma VM em execução:
1. **Pare a VM** (Portal Azure > VM > **Parar**).  
2. Selecione **Tamanho** e escolha um novo SKU.  
3. Reinicie a VM.

⚠ **Limitação**: Algumas séries exigem migração para hardware diferente.

---

## Configuração de Rede Virtual (VNet)
- **IP Público**: Atribua um IP estático/dinâmico conforme necessidade.  
- **NSGs (Network Security Groups)**: Restrinja tráfego por portas (ex: 80, 443, 22).  

### Exemplo de NSG via CLI:
```bash
az network nsg create --name MyNSG --resource-group MyRG
az network nsg rule create --name AllowHTTP --nsg-name MyNSG --priority 100 --access Allow --protocol Tcp --direction Inbound --destination-port-ranges 80
```

---

## Monitoramento e Autoescala
- **Azure Monitor**: Acompanhe desempenho via métricas (CPU%, disco, rede).  
- **Conjuntos de Escala de VM**: Automatize o dimensionamento horizontal com regras baseadas em métricas.  

🔹 **Exemplo de regra de autoescala** (aumentar instâncias se CPU > 70% por 5 min):
```json
{
  "metricTrigger": {
    "metricName": "Percentage CPU",
    "threshold": 70,
    "timeAggregation": "Average",
    "timeWindow": "PT5M"
  },
  "scaleAction": {
    "direction": "Increase",
    "type": "ChangeCount",
    "value": "1"
  }
}
```

---

## Melhores Práticas
✅ **Sizing Right-Sizing**: Evite superprovisionamento. Use o [Azure Advisor](https://portal.azure.com/#blade/Microsoft_Azure_Expert/AdvisorMenuBlade/overview) para recomendações.  
✅ **Discos Gerenciados**: Prefira discos gerenciados para melhor confiabilidade.  
✅ **Tags**: Organize recursos com tags (ex: `env:production`).  
✅ **Backup Automatizado**: Configure o **Azure Backup** para VMs críticas.  

---

📚 **Documentação Oficial**:  
- [Tamanhos de VMs no Azure](https://docs.microsoft.com/azure/virtual-machines/sizes)  
- [Preços de VMs](https://azure.microsoft.com/pricing/details/virtual-machines/)  

🛠 **Próximos Passos**:  
- [ ] Criar uma VM de teste com tamanho B2s.  
- [ ] Configurar um alerta de CPU no Azure Monitor.  

---
✉ **Dúvidas?** Contate o [Suporte Azure](https://azure.microsoft.com/support/options/).
