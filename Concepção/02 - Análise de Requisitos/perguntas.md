# Questionário de Análise de Requisitos

## Sobre os Requisitos Funcionais

1. **Upload e Armazenamento de Documentos**

- Quais formatos de documentos você deseja suportar para upload (ex.: PDF, DOCX, imagens)?
- **Resposta**: Inicialmente, documentos de texto no formato pdf ou txt, imagens no formato png ou jpeg.

- Há alguma restrição de tamanho ou tipo de documento que devemos considerar?
-- **Resposta**: Eu não sei como calcular um tamanho especifico, mas se um arquivo de pdf possuir muitas páginas, ele demorará mais tempo para transformar todas as páginas em imagens para então extrair o texto, logo ele precisará ser dividido em partes iguais, ou arbitrárias (escolhidas pelo usuário) para que seja carregado, mas não seria um impedimento de arquivos grandes, mas uma regra que faria essa divisão por questões de performance. Documentos que não se encaixem nos formatos válidos devem retornar mensagem de erro e um tratamento solicitando documentos nos formatos válidos. Caso a entrada seja um diretório, deverão ser listados para serem carregados e armazenados apenas aqueles que atendam aos requisitos de formato. 

- Como você visualiza a organização e recuperação dos documentos armazenados (ex.: tags, categorias, metadados)?
-- **resposta**: Quando um documento for carregado, algumas informações deverão ser fornecidas pelo usuário, como titulo do documento, autor, data de escrita, o próprio path do arquivo, o idioma (que caso seja deixado em branco poderá ser detectado pela aplicação). Outros dados como quantidade de páginas, formato do arquivo, quantidade de linhas, de caracteres, de sentenças, de paragrafos, deverão ser coletados pelo sistema.

Quando um usuário listar os documentos já cadastrados, ele poderá ter acesso a esses dados e poderão ser realizadas pesquisas para encontrar documentos de um determinado autor ou idioma, por exemplo. Os documentos poderão ser classificados quanto ao seu tipo e para isso podem ser atribuídas tags que facilitem na recuperação dos dados desejados.

2. **Extração de Texto com OCR**

- Qual é o nível de precisão esperado para a extração de texto (ex.: percentual mínimo de acurácia)?
-- **resposta**: É dificil eu dizer porque preciso estudar mais sobre o assunto, mas acredito que o usuário deva ser capaz de, quando for extrair o texto de uma imagem (que pode ser uma página de pdf convertida em imagem para extração de texto ou ter sido carregado como imagem) ele possa analisar o resultado e se preciso, realizar manipulação da imagem (thresholding, por exemplo) ou ajustar os parâmetros do ocr até que visualize um resultado que considere satisfatório para persistir. Essa avaliação do resultado do ocr deve incluir tecnicas de preprocessamento de texto afim de eliminar ruídos, isnerir pontuação e quebras de linhas e espaços.

- Há algum tipo específico de documento ou idioma que pode exigir tratamento especial?
-- **resposta**: é importante especial atenção aos documentos de alfabetos cirilicos, porque pode ser preciso fazer transliteração ou porque não necessáriamente o usuário terá um teclado no alfabeto cirilico para performar edições.

- Você tem alguma preferência por serviços de OCR ou bibliotecas específicas para utilizar?
-- **resposta**:  Só conheço o tesseract-ocr e a biblioteca pytesseract, mas estou aberto a sugestões. Também estou aberto a sugestões de bibliotecas para a normalização(preprocessamento) dos textos extraídos.

3. **Tradução Automática**

- Quais idiomas devem ser suportados para a tradução automática?
- **resposta**: incialmente, portugues, ingles, espanhol e russo, incluindo alfabeto cirilico (potencialmente traduzirei documentos de toda a urss)

- Há algum limite de caracteres ou requisitos específicos para a tradução que devemos considerar?
- **resposta**: cada api tem a sua limitação, mas eu nunca pesquisei a fundo e talvez você possa me ajudar. Eu tenho usado até agora a biblioteca deep_translator do python porque ela me oferece suporte a:

Support for google translate
Support for the microsoft translator (version >= 1.3.5)
Support for Pons translator
Support for the Linguee translator
Support for the Mymemory translator
Support for the Yandex translator (version >= 1.2.1)
Support for the QcriTranslator translator (version >= 1.2.4)
Support for the DeeplTranslator translator (version >= 1.2.5)
Support for the Papago translator (version >= 1.4.4)
Support for the Libre translator

o que me parece um bom ponto de partida, mas eu preciso pesquisar essas limitações e inclusive escolher algumas dentre estas. Talvez 3 ou 4.


- Você prefere alguma API de tradução específica (ex.: Google Translate, DeepL)? 
- **resposta**: Eu usava o TextBlob para traduzir no passado, mas esse módulo de tradução está deprecado e eles mesmo sugerem usar a api do google translate. Mas eu quero escolher dentre as apis que eu consigo usar com o deep_translator, que eu mencionei acima e aceito sugestões suas.

## Sobre os Requisitos Não Funcionais

1. **Desempenho**

- Qual é o tempo máximo aceitável para o processamento de documentos (ex.: tempo máximo de extração e tradução)?
- **resposta**: Eu não sei dizer, porque não tenho base de comparação, mas acho importante que os processos não sejam bloqueantes no sentido de que eu consiga navegar pela aplicação enquanto algum processo demorado esteja sendo feito, e que haja uma fila, por exemplo, no caso de um documento pdf com 10 páginas, para que ele seja considerado extraído e armazenado apenas quando todas as páginas tiverem sido convertidas, terem tido o texto extraído e armazenado. Embora não sejam bloqueantes, como a extração com ocr envolve a verificação da extração, deve ser possivel acompanhar o status do processo e ir até a view que permite analisar o resultado da extração do ocr. Eu não sei para isso eu precisarei de um cache, mas é preciso salvar o estado dos processos em caso de aplicação ser encerrada com arquivos na fila. Enfim, essa parte eu preciso da sua ajuda.


- Quantos documentos você espera processar simultaneamente ou em um período específico (ex.: por hora, por dia)?
- **resposta**:  não tenho ideia, mas normalmente um documento por vez, embora esse documento possa demandar diversas ações (um pdf de várias páginas precisará de ações em cada uma das páginas). 

2. **Segurança**

- Quais são os requisitos de segurança específicos para os dados armazenados e o acesso ao sistema?
- **resposta**: uma aplicação tui, cada usuário teria seu próprio banco de dados, e por isso os requistos de segurança seriam os básicos para garantir a integridade de transações e segurança do banco. mas quando se tratar de aplicação o web será preciso garantir a privacidade de cada usuário.

- Você tem alguma política de segurança ou padrões específicos que precisam ser seguidos (ex.: GDPR, HIPAA)?
- **respostas**: não sei anda sobre as políticas de seguranças relativas a um projeto destes, mas com certeza existe uma preocupação com respeito a direitos autorais, no sentido de isentar o desenvolvedor da plataforma sobre mau-uso neste sentido.


3. **Escalabilidade**

- Quais são suas expectativas quanto à escalabilidade do sistema?
- **resposta**: Importante frisar que a aplicação, num primeiro momento será feita como uma TUI e posteriormente será portada para aplicação web com flask. Além disso, pode ser usada para criação de diversos corpora de dados e/ou coleções de documentos com base em tags ou outro critéiros.

- Há algum plano para expansão futura que deve ser considerado na arquitetura (ex.: aumento de usuários, volume de documentos)?
- **resposta**: Estou começando com o mongodb, mas no futuro posso querer usar, intercambiavelmente um banco de dados relacional, como o sqlite. Na versão aplicação web, certamente haverão maior volume de usuários, de documentos, e diferenciação de papéis, além da questão da privacidade ou não da coleção de documentos dos usuários.

## Sobre a Arquitetura e Integrações

1. **Integração com OCR**

- Qual é a expectativa de integração com o serviço OCR?
- **resposta** que a integração seja fácil e feita de tal forma que possa ser possível plugar outras ferramentas de ocr e variar entre elas.

- Há algum requisito especial para a configuração e uso do OCR (ex.: pré-processamento de imagens)?
- **resposta** como ja dito em outros trechos do documento, sim, o preprocessamento da imagem é importante e pode ser realizado após uma execução preliminar do ocr para testar. Também será preciso preprocessar o texto extraído antes de persistir

2. **Integração com API de Tradução**

- Como você pretende utilizar a API de tradução no fluxo de trabalho (ex.: tradução em tempo real, tradução em lote)?
- **resposta**: no fluxo de trabalho na aplicação, um usuário pode escolher setenças ou paragrafos especificos do documento que estiver trabalhando para traduzir e daí cada trecho selecionado seria traduzido à medida que solicitado, ou o usuário pode escolher traduzir o documento inteiro, que no caso precisará ser segmentado para a tradução e a tradução feita através de uma fila para garantir que todos os trechos sejam traduzidos. Se a tradução for feita assim em lote, será preciso revisar a tradução antes de persistir, assim como se o usuário escolher a tradução de um trecho especifico, poderá aprovar ou não a tardução para salvamento.

quando uma tradução for feita, deverá ser registrado api/engine de tradução e o documento deverá conter a referência de que algum trecho dele foi traduzido, de modo que consultar um documento permita saber quanto dele já foi traduzido e de quais e para quais linguas, além da api usada na tradução.

importante o estabelecimento de um sistema de versionamento do docuemnto, para registrar as diferentes edições, para controle.

- Você tem alguma consideração para a gestão de custos com a API de tradução (ex.: limite de requisições)?
- **resposta**: é preciso garantir que se uma requisição não for atendida, que ela seja refeita sem estourar os limites da api, de modo a garntir que todos na fila sejam traduzidos.

3. **Arquitetura e Escalabilidade**

- Há alguma preferência por padrões de arquitetura ou design que devem ser seguidos?
- **resposta**: Não há preferência, mas gosto dos principios solid, de inversão de dependências, design patterns, repository pattern, composição sobre herança e etc...

- Você tem planos para futuras funcionalidades que devem ser consideradas agora para garantir a escalabilidade?
- **resposta** no futuro a aplicação pode evoluir para mais funcionalidades relacionadas ao processamento de linguagem natural e ao treinamento de modelos. 