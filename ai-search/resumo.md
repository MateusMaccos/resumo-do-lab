# Azure AI Search Index (UI) - Guia e Insights

## 🌟 Visão Geral
Este documento reúne observações e melhores práticas sobre a criação e gestão de índices no Azure AI Search utilizando a interface do usuário (UI).

## 🔍 O que é Azure AI Search?
Serviço de busca em nuvem que oferece:
- Indexação poderosa sobre diversos tipos de dados
- Capacidades avançadas de busca semântica
- Integração nativa com outros serviços Azure AI

## 🛠️ Criando um Índice via UI

### Passos Básicos
1. **Definição do Índice**
   - Nome do índice (não pode ser alterado posteriormente)
   - Chave primária (campo obrigatório)

2. **Adição de Campos**
   - Tipos suportados: String, Int32, Int64, Double, Boolean, DateTime, GeographyPoint
   - Atributos por campo:
     - **Retrievable** (pode ser retornado nos resultados)
     - **Filterable** (pode ser usado em filtros)
     - **Sortable** (permite ordenação)
     - **Facetable** (permite faceting/navegação facetada)
     - **Searchable** (incluído na busca full-text)

3. **Configurações Avançadas**
   - Sugestores (para autocomplete)
   - Perfis de pontuação (customização de relevância)
   - Opções semânticas (habilita busca semântica)

## 💡 Insights Práticos

### Design de Índice
- **Pense nos casos de uso**: Estruture campos baseado em como os dados serão consultados
- **Otimize campos searchable**: Só marque como searchable campos que realmente precisam ser pesquisados
- **Use facets estrategicamente**: Campos facetáveis devem ser de baixa cardinalidade (ex: categorias, não IDs)

### Performance
- **Índices complexos** podem impactar performance - comece simples e evolua
- **Evite muitos campos filterable/sortable** se não forem necessários
- **Atualizações frequentes** podem exigir estratégia de indexação específica

## 🔄 Processo de Indexação
1. **Conectar fonte de dados** (Azure SQL, Cosmos DB, Blob Storage, etc.)
2. **Mapear campos** entre fonte e índice
3. **Configurar skillset** (opcional - para enriquecimento cognitivo)
4. **Agendar execução** (one-time ou recorrente)

## 🧩 Recursos Avançados via UI

### Enriquecimento com AI
- Extração de entidades
- Detecção de idioma
- Extração de frases-chave
- Análise de sentimento

### Busca Semântica
- Habilita compreensão contextual
- Melhora relevância para consultas complexas
- Requer camada Standard ou superior

### Teste na Interface
- **Gerenciador de busca**: Teste consultas em tempo real
- **Visualização JSON**: Entenda a estrutura subjacente
- **Estatísticas**: Analise distribuição de termos

## ⚠️ Limitações e Considerações
- **Limite de campos**: Até 1000 campos por índice
- **Tamanho máximo**: 2GB para índices básicos
- **UI vs API**: Algumas funcionalidades só estão disponíveis via API

## 🏆 Melhores Práticas
1. Comece com um protótipo simples
2. Documente seu schema de índice
3. Use aliases para gerenciar mudanças
4. Monitore métricas de performance
5. Planeje estratégia de atualização

## 📚 Recursos Úteis
- [Documentação Oficial](https://learn.microsoft.com/en-us/azure/search/)
- [Referência de Sintaxe de Consulta](https://learn.microsoft.com/en-us/azure/search/query-lucene-syntax)
- [Exemplos de Índices](https://github.com/Azure-Samples/azure-search-sample-indexes)

## 🚀 Próximos Passos
- Explorar integração com outros serviços Azure AI
- Testar cenários de reindexação com zero downtime
- Implementar camadas de segurança no índice
