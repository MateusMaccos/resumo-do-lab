# Anotações e Insights: Azure Speech Studio & Language Studio

## 📌 Visão Geral
Este repositório contém anotações e insights sobre o uso das ferramentas **Azure Speech Studio** e **Language Studio** da Microsoft, com foco especial em análise de fala e processamento de linguagem natural (NLP).

## 🎤 Azure Speech Studio

### Principais Recursos
- **Conversão de Fala em Texto (Speech-to-Text)**
  - Transcrição precisa em tempo real ou assíncrona
  - Suporte a múltiplos idiomas e dialetos
  - Customização com modelos acústicos e de linguagem

- **Texto em Fala (Text-to-Speech)**
  - Vozes neurais realistas
  - Controle de entonação e velocidade
  - Criação de vozes personalizadas

### Insights Práticos
- **Customização é chave**: Modelos padrão funcionam bem, mas para domínios específicos (como medicina ou jurídico), treinar modelos customizados melhora significativamente a precisão.
- **Batch vs Real-time**: Para análise de grandes volumes de áudio, o processamento em batch é mais eficiente.
- **Dicas de áudio**: Qualidade do áudio impacta diretamente nos resultados - ruído de fundo pode reduzir a precisão em até 30%.

## 📚 Azure Language Studio

### Principais Recursos
- **Análise de Sentimento**
  - Detecção de polaridade (positivo/negativo/neutro)
  - Análise por aspecto/frase

- **Reconhecimento de Entidades (NER)**
  - Identifica pessoas, lugares, datas, etc.
  - Versão PII (Informação Pessoal Identificável) para dados sensíveis

- **Extração de Frases-chave**
  - Identifica conceitos principais
  - Útil para sumarização

- **Classificação de Texto**
  - Categorização automática
  - Suporte a domínios customizados

### Insights Práticos
- **Combinação de features**: Usar NER + Análise de Sentimento juntos proporciona insights mais ricos (ex.: saber que "Paris" é uma entidade LOCAL e que está sendo mencionada positivamente).
- **Limites de tamanho**: Algumas features têm limite de caracteres - para textos longos, considerar quebra em partes.
- **Customização com CLU**: O recurso **Conversational Language Understanding** permite treinar modelos para intenções e entidades específicas do seu domínio.

## 💡 Casos de Uso Combinados
1. **Call Center Analytics**
   - Speech-to-Text para transcrever chamadas
   - Language Studio para análise de sentimento e tópicos
   - Identificar tendências e pontos de irritação

2. **Acessibilidade**
   - Text-to-Speech para conteúdo acessível
   - Speech-to-Text para legendas automáticas
   - Extração de frases-chave para resumo de conteúdo

3. **Media Monitoring**
   - Processar áudio de programas de TV/rádio
   - Identificar entidades mencionadas
   - Analisar tom geral das discussões

## ⚠️ Limitações e Considerações
- **Custos**: Processamento de grandes volumes pode gerar custos inesperados - monitorar uso.
- **Idiomas**: Algumas features têm suporte limitado a idiomas - verificar documentação atualizada.
- **Latência**: Algumas operações (especialmente customizadas) podem ter maior latência.

## 📚 Recursos Úteis
- [Documentação Oficial Speech Studio](https://speech.microsoft.com)
- [Documentação Language Studio](https://language.cognitive.azure.com)
- [Repositório de Modelos Pré-treinados](https://github.com/microsoft/Azure-AI)

## 🚀 Próximos Passos
- Experimentar pipelines combinando ambas as ferramentas
- Explorar integração com Power BI para visualização
- Testar cenários com dados reais do seu domínio
