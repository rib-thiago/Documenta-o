# Perguntas para Alinhar Objetivos e Expectativas

1. **Objetivos Gerais do Projeto**:

- Quais são os principais objetivos que você espera alcançar com o sistema de manipulação e gerenciamento de documentos digitalizados?
- **resposta**: Meu objetivo é criar uma plataforma que funcione como uma interface que concentre diversas ferramentas para manipulação de documentos digitalizados de modo a facilitar o trabalho com o conteúdo destes documentos. Especificamente para mim, é importante trablhar aspectos de transliteração e tradução de textos porque minhas fontes de pesquisa são documentos soviéticos dos anos 1920 e anos 1930, ou seja, são documentos datilografados posteriormente digitalizados via scanner e eu quero poder acessar seu conteúdo, traduzir e citart em minhas pesquisas.


- Há algum problema específico que este sistema deve resolver para você ou para sua área de atuação?
- **resposta**: Sim. Documentos digitalizados são dificeis de transcrever e citar porque não é possível copiar o texto com o mouse, então é preciso reccorrer a tecnicas tanto para extrair o texto com OCR ou converter o pdf em pdf pesuisável. Além disso, existem por aí diversas ferramentas que fazem parte do trabalhado de um pesquisador, por exemplo: Para extrair apenas algumas páginas de um pdf para depois extrair o texto com ocr e traduzir os trechos extraídos, eu preciso acessar multiplas ferramentas, em sites diferentes, com várias ações de download e upload.
Textos extraídos com ocr costumam ter muito ruído, então é preciso pensar em preprocessamento dos textos. além disso, certas tarefas de nlp precisam de lemantização, stemização e etc..

2. **Público-Alvo**:

- Quem são os principais usuários do sistema? Você mencionou profissionais como pesquisadores, historiadores, advogados e jornalistas. Existem outros perfis de usuários que devemos considerar?
- **resposta**: De uma forma genérica, essa aplicação se destina a qualquer pessoa que queira extrair e aproveitar de alguma forma o conteúdo de documentos digitalizados sem perder uma forma de referência ao documento original. Mas vale a pena considerar o cenário de extrair materiais para treinamento de modelos de linguagens.

- Quais são as principais necessidades e expectativas desses usuários em relação ao sistema?
- **resposta**: as principais necessidades e expectativas são que a aplicação seja prática de usar no sentido de que o documento seja carregado apenas uma vez em sistema e que de uma forma fácil os dados relevantes sejam extraídos e armazenados para os posteriores trabalhos seja de tradução, seja de análise, treinamento de modelos de linguagens. Além disso deve ser fácil realizar operações especificas a depender da fonte de entrada, por exemplo, extrair páginas de um pdf ou mesclar páginas de dois pdfs, converter para preto e branco e outras operações para ajustar a qualidade da imagem para o ocr. Tudo isso num ambiente que permita que acessa multiplas ferramentas, com suas respectivas views de uma forma integrada.

3. **Funcionalidades e Recursos**:

- Quais funcionalidades principais você considera essenciais para o sistema? Por exemplo, você mencionou tradução e análise de documentos; há outras funcionalidades que são imprescindíveis?
- **resposta**: mecanismo de pesquisa em base dados, criação de bases de dados (coleções de documentos, citações reunidas arbitrariamente pelo usuário), manipulação de pdfs e manipulação de imagens. Posteriormente, seria interessante extrair conteúdo de páginas html.


- Há alguma integração com outras ferramentas ou sistemas que o sistema precisa ter?
- **resposta**: não sei a resposta, mas penso que com o sistema de gerenciamento de banco de dados mongodb, tesseract-ocr, apis de tradução

4. **Escopo do Projeto**:

- Qual deve ser o escopo inicial do projeto? Há algum aspecto específico do gerenciamento e manipulação de documentos que deve ser priorizado?
- **resposta**: Se eu entendi a pergunta, inicialmente precisamos de uma aplicação que seja capaz de receber entrada e determinar se se trata de um pdf, de uma imagem ou de um arquivo txt. em caso de imagem, usar ocr para extrair o texto, se for pdf, converter as páginas em imagens e seguir como imagem (passar pelo ocr), se for texto, ou se tiver passado pelas etapas anteriores e agora for texto, coletar informações sobre o documento inserido e armazenar no banco de dados. Ser capaz de recuperar as informações, como lista de documentos ou o conteúdo próprio de um documento.

Com o passar do tempo podemos melhorar para oferecer suporte a outros idiomas, tradução de trechos do documento e aprimorar o serviço de ocr.


- Existe alguma limitação ou restrição que devemos considerar ao definir o escopo do projeto?
- **resposta**:  Eu sei que apis de tradução de texto possuem limitação de caracteres e de requisições por segundo e minuto. Acredito que segmentar por paragrafos e/ou sentenças ou ser capaz de fazer essa segmentação, além de poder fazer fila e trabalhar asíncronamente se for preciso em caso de docuemntos grandes. O projeto deve ser modularizado e ter uma arquitetura que permita separação de responsabilidades, que aproveite o melhor dos recursos de orientação a objetos e padrões de design de projetos, para facilitar a escalabilidade e ser flexivel para suportar mudanças de tecnologias.

5. **Objetivos de Alto Nível**:

- Quais são os principais objetivos de alto nível que você deseja atingir com este projeto? Por exemplo, melhoria da eficiência, redução de erros, aumento da acessibilidade, etc.
- **resposta**: Não sei responder, me ajude aí
- Como você medirá o sucesso do projeto? Existem métricas ou indicadores específicos que você gostaria de usar?
- **resposta**: também não sei responder, me ajuda aí

6. **Cronograma e Recursos**:

- Qual é o prazo desejado para a conclusão deste projeto? Existem marcos importantes ou deadlines que devemos considerar?
- **resposta**: O projeto deve ser entregue em dezembro de 2024. Seria importante ter uma estrutura mínima funcional até inicio de setembro, para que possa ser evoluída até o final do prazo.
- Quais recursos (humanos, tecnológicos, financeiros) estão disponíveis para este projeto? Há alguma limitação que devemos estar cientes?
- **resposta**: por enquanto esse projeto é desenvolvido apenas por uma pessoa, um estudante, como forma de trabalho de conclusão de curso, não possui um orçamento e por isso deve, ao máximo, usar ferramentas open source.

7. **Expectativas de Entregáveis**:

- Quais são as suas expectativas em relação aos entregáveis iniciais do projeto? Há alguma forma específica de documentação ou protótipo que você gostaria de ver?
- **resposta**: não sei responder, me ajuda aí