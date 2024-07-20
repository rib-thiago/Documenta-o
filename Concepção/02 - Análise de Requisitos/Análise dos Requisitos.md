# Análise de Requisitos

**Objetivo**: Identificar e documentar os requisitos críticos, com foco em aproximadamente 10% dos casos de uso e requisitos não funcionais importantes.

## Requisitos Funcionais

1. **Upload e Armazenamento de Documentos**

- **Formatos de Documentos Suportados**: PDF, TXT, PNG e JPEG.
- **Restrições de Tamanho e Tipo**: Documentos PDF grandes devem ser divididos em partes para processamento. O sistema deve tratar erros para formatos inválidos e permitir a carga de arquivos em diretórios, filtrando por formatos válidos.
- **Organização e Recuperação**: Informações como título, autor, data de escrita, idioma deverão ser forncecidas pelo usuário e metadados adicionais (número de páginas, linhas e caracteres, formato do arquivo, etc.) serão coletadas. A pesquisa e a recuperação serão facilitadas por tags e metadados.

2. **Extração de Texto com OCR**

- **Precisão Esperada**: O usuário deve poder ajustar parâmetros e preprocessar imagens para melhorar a precisão. Técnicas de pré-processamento e ajustes são necessários para garantir a qualidade da extração.
- **Tratamento Especial**: Atenção especial para documentos com alfabetos cirílicos, que podem necessitar de transliteração ou outras adaptações.
- **Serviços e Bibliotecas**: A preferência inicial é usar Tesseract-OCR e a biblioteca pytesseract. Sugestões para bibliotecas de pré-processamento de texto são bem-vindas.

3. **Tradução Automática**

- **Idiomas Suportados**: Português, Inglês, Espanhol e Russo.
- **Limites de Tradução**: Considerar limitações das APIs selecionadas. Utilizar a biblioteca deep_translator como ponto de partida para suportar várias APIs de tradução.
- **API Preferida**: Avaliar entre as APIs disponíveis na deep_translator, com preferência inicial para Google Translate e DeepL.

## Requisitos Não Funcionais

1. **Desempenho**

- **Tempo Máximo de Processamento**: O sistema deve ser não bloqueante, permitindo a navegação enquanto processos longos estão em execução. Implementar uma fila para processamento de documentos grandes e garantir que o estado dos processos seja salvo em caso de falha.
- **Número de Documentos Processados**: Normalmente um documento por vez, com múltiplas ações para documentos extensos.

2. **Segurança**

- **Requisitos de Segurança**: Garantir a integridade das transações e a segurança do banco de dados. Para a aplicação web, implementar segurança adicional para proteger a privacidade dos usuários.
- **Políticas de Segurança**: Seguir boas práticas de proteção de dados e respeitar direitos autorais.

3. **Escalabilidade**

- **Expectativas de Escalabilidade**: A aplicação começará como TUI e pode evoluir para uma aplicação web com Flask. Considerar aumento de usuários e volume de documentos na arquitetura.
- **SGBD**: Dados serão persistidos no mongodb, mas deverá ser flexível para persistir em sqlite também (repository pattern)
- **Planos de Expansão**: Futuras funcionalidades podem incluir processamento de linguagem natural e treinamento de modelos.

## Arquitetura e Integrações

1. **Integração com OCR**

- **Expectativa de Integração**: A integração deve ser flexível para permitir a substituição de ferramentas OCR e incluir opções para pré-processamento de imagens e textos.

2. **Integração com API de Tradução**

- **Uso no Fluxo de Trabalho**: Tradução pode ser feita em tempo real ou em lote, com capacidade de revisão antes de persistir. Registrar a API utilizada e versionar documentos para controle de alterações.
- **Gestão de Custos**: Implementar controle para não exceder os limites da API e garantir que todas as traduções na fila sejam concluídas.

## Arquitetura e Escalabilidade

- **Padrões de Arquitetura**: Seguir princípios SOLID, padrões de design e padrões de arquitetura como o Repository Pattern.
- **Funcionalidades Futuras**: Preparar a arquitetura para suportar processamento de linguagem natural e treinamento de modelos.




## lista de casos de usos:

- **UC01** - Upload de Documentos
- **UC02** - Armazenamento e Organização de Documentos
- **UC03** - Extração de Texto com OCR
- **UC04** - Tradução de Texto
- **UC05** - Pesquisa e Recuperação de Documentos
- **UC06** - Validação de Dados
- **UC07** - Conversão de Formatos de Documentos
- **UC08** - Ajuste de Qualidade de Imagens para OCR
- **UC09** - Registro e Controle de API de Tradução
- **UC10** - Revisão e Aprovação de Traduções
- **UC11** - Gerenciamento de Metadados
- **UC12** - Processamento de Documentos em Lote
- **UC13** - Backup e Recuperação de Documentos
- **UC14** - Interface de Usuário para Upload e Processamento
- **UC15** - Configuração de Parâmetros de OCR
- **UC16** - Gestão de Usuários e Permissões
- **UC17** - Exportação de Dados para Treinamento de Modelos
- **UC18** - Monitoramento e Logging de Processos
- **UC19** - Geração de Relatórios de Processamento
- **UC20** - Integração com Sistemas Externos
