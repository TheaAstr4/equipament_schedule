Este projeto consiste em um script Python que gera um Termo de Compromisso para retirada de equipamentos de laboratório em formato PDF, utilizando as bibliotecas ReportLab e LangChain. O sistema é capaz de extrair informações de e-mails, identificar os equipamentos necessários para alocação, e gerar um documento formatado, incluindo tabelas com detalhes dos equipamentos e campos para assinatura.
Funcionalidades principais:

* Processamento de e-mails: Utiliza um modelo de linguagem para extrair informações de e-mails e gerar um JSON com dados sobre equipamentos.
* Geração de PDF: Gera um PDF com informações como nome do equipamento, quantidade, status e patrimônio, além de incluir campos para assinaturas e datas.
* Customização do documento: O layout do PDF inclui cabeçalho, rodapé e tabelas estilizadas, permitindo que os dados sejam apresentados de forma clara e organizada.

# Requisitos

Para executar o código, você precisará instalar as seguintes dependências:

* Python 3
* reportlab
* langchain
* langchain_community
* langchain_groq

# Você pode instalar as dependências com o comando:


 ```bash
pip install reportlab langchain langchain_community langchain_groq
 ```
# Como usar

* Configuração do modelo: O código utiliza o modelo llama3-groq-70b-8192-tool-use-preview via Groq. Certifique-se de alterar api_key .

* Definição do Prompt: O prompt do modelo é definido para extrair os seguintes itens dos e-mails:
    * Nome do equipamento
    * Quantidade

* Geração do PDF: O código lê as informações extraídas e as organiza em uma tabela no documento PDF. Para gerar o PDF com os dados dos equipamentos, execute o seguinte trecho do código:

    ```python

    criar_pdf_alocacao("alocacao_equipamentos.pdf", data['Equipamentos de laboratório necessários'])
    ```

    Isso criará um arquivo PDF nomeado alocacao_equipamentos.pdf com os dados extraídos.

    Rodapé personalizado: O documento inclui um rodapé com informações personalizadas em todas as páginas. O rodapé pode ser modificado na função rodape.

Estrutura do Código

* Função rodape: Adiciona um rodapé padrão em todas as páginas do PDF.
* Função criar_pdf_alocacao: Gera o PDF com base nos dados fornecidos, utilizando a biblioteca ReportLab para formatar o documento e criar a tabela com os equipamentos.
* Modelo de linguagem: Usa o ChatGroq para processar e-mails e extrair informações de equipamentos necessários em JSON.

# Exemplo de Saída:

O PDF gerado terá o seguinte formato:

* Título: TERMO DE COMPROMISSO PARA RETIRADA DE EQUIPAMENTOS
* Parágrafo introdutório com campos de preenchimento.
* Tabela de equipamentos contendo colunas para Equipamento, Quantidade, Patrimônio e Status.
* Campos para assinaturas e datas.
