# Simplificação da análise forense de logs utilizando Grandes Modelos de Linguagem com a técnica RAG

Este repositório contém os artefatos do artigo "Simplificação da análise forense de logs utilizando Grandes Modelos de Linguagem com a técnica RAG", submetido ao Simpósio Brasileiro de Cibersegurança (SBSeg).

O objetivo deste trabalho é apresentar uma abordagem que utiliza Grandes Modelos de Linguagem (LLMs) combinados com a técnica de Retrieval-Augmented Generation (RAG) para simplificar a análise forense de logs de sistemas e redes. A solução proposta permite a detecção, correlação e interpretação de anomalias por meio de interações em linguagem natural, otimizando o processo de investigação e resposta a incidentes de segurança.

Abstract. In the digital age, the growing complexity of computer systems and the sophistication of cyberattacks significantly increase the volume of logs generated, posing challenges to cybersecurity professionals. Detecting and interpreting attacks or issues in these records are crucial for a swift response to security incidents. In this context, Large Language Models (LLMs) emerge as fundamental tools for understanding and generating natural language. This study presents an approach to analyze system and network logs, aiming to detect, correlate, and interpret anomalies using the Retrieval-Augmented Generation (RAG) technique with LLMs and interactions through targeted questions. The results demonstrate the effectiveness of the proposed approach in generating relevant insights and simplifying forensic analysis for professionals in the field.

Resumo. Na era digital, a crescente complexidade dos sistemas informáticos e a sofisticação dos ataques cibernéticos aumentam significativamente o volume de logs gerados, desafiando os profissionais de cibersegurança. A detecção e interpretação de ataques ou problemas nesses registros são essenciais para uma resposta rápida a incidentes de segurança. Nesse contexto, os Grandes Modelos de Linguagem (LLMs) destacam-se como ferramentas fundamentais na compreensão e geração de linguagem natural. Este estudo apresenta uma abordagem para analisar logs de sistemas e redes, visando detectar, correlacionar e interpretar anomalias, utilizando a técnica de \emph{Retrieval-Augmented Generation} (RAG) com LLMs e interações por meio de perguntas direcionadas. Os resultados comprovam a eficácia da abordagem proposta em gerar informações relevantes e simplificar a análise forense para profissionais da área.

# Estrutura do readme.md

Apresenta a estrutura do readme.md, descrevendo como o repositório está organizado.

# Selos Considerados

Os selos considerados são: Artefatos Disponíveis (SeloD), Artefatos Funcionais (SeloF), Artefatos Sustentáveis (SeloS), Experimentos Reprodutíveis (SeloR).

# Informações básicas

Este repositório contém os artefatos necessários para a execução e replicação dos experimentos descritos no artigo. 
Abaixo estão listados os requisitos mínimos de hardware e software, bem como informações sobre o ambiente de desenvolvimento.

### Ambiente de desenvolvimento
- Sistema Operacional: Ubuntu 20.04 LTS (recomendado)
- Recomenda-se a utilização de um ambiente Linux para melhor compatibilidade.

### Requisitos de hardware mínimos
- Processador: Intel Core i3-9100 ou equivalente AMD
- Memória RAM: 16 GB
- Placa de vídeo: NVIDIA RTX 2060
- Armazenamento: 5 GB de espaço livre em disco
- Conexão com a internet: Banda larga (necessária apenas durante o download e configuração dos modelos e do sistema)

### Observações
- O uso de GPU é recomendado para acelerar o processamento dos modelos de linguagem.
- Os testes e experimentos foram conduzidos utilizando uma configuração com os requisitos acima e apresentaram desempenho satisfatório.

# Dependências
Para a execução correta dos experimentos e reprodutibilidade dos resultados, é necessário instalar as seguintes dependências e configurar os recursos de terceiros conforme descrito abaixo.

### Versão do python
- Python 3 (testado com Python 3.10)

### Principais bibliotecas
As bibliotecas essenciais utilizadas no projeto incluem:
- langchain==0.2.16
- langchain-core==0.2.39
- langchain-community==0.2.16
- langchain-ollama==0.1.3
- pandas==2.2.3
Outras dependências estão listadas no arquivo `requirements_lang_chain.txt`, que pode ser instalado com o comando:
```bash
pip install -r requirements_lang_chain.txt
```

### Modelo LLM utilizado
Este projeto utiliza o <b>LLaMA 3.22</b> com <b>3 bilhões de parâmetros</b>, instalado por meio da ferramenta Ollama. O Ollama é necessário para hospedar e interagir localmente com o modelo de linguagem.

Como instalar e rodar o modelo com Ollama:
Instale o Ollama conforme a documentação oficial: https://ollama.com/download

Após a instalação, execute o seguinte comando para baixar o modelo:
```bash
ollama run llama3
```
<b>Nota:</b> A instalação do modelo pode levar alguns minutos e requer conexão com a internet.

# Preocupações com segurança

Não há preocupações conhecidas que possam prejudicar o ambiente dos avaliadores

# Instalação
A seguir, apresentamos o passo a passo necessário para instalar e executar a aplicação localmente.

### 1. Instalar o Python 3
Certifique-se de que o Python 3 esteja instalado. Recomenda-se a versão 3.10.
No Ubuntu, você pode instalar com:
```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip
```

### 2. Criar e ativar o ambiente virtual
```bash
# Criar ambiente virtual
python3 -m venv forense-rag-logs-venv
cd forense-rag-logs-venv

# Ativar ambiente virtual
source bin/activate
```

### 3. Clonar o repositório
```bash
git clone https://github.com/CGabriel22/forense-rag-logs
cd forense-rag-logs
```

### 4. Instalar as dependências
```bash
pip3 install -r requirements/requirements_lang_chain.txt
```

### 5. Instalar e configurar o Ollama
Para utilizar o modelo LLaMA localmente, é necessário instalar o Ollama:
Acesse https://ollama.com/download e siga as instruções para seu sistema

Após instalado, execute o comando abaixo para baixar o modelo LLaMA 3 com 3B de parâmetros:
```bash
ollama run llama3
```
<b>Importante:</b> A primeira execução fará o download do modelo e pode levar alguns minutos.

# Teste mínimo

Para facilitar a avaliação do artefato, disponibilizamos um notebook Jupyter com toda a estrutura de execução e um exemplo funcional ao final do arquivo.

### Passo a passo para execução:
1. Ative o ambiente virtual, caso ainda não esteja ativo:
```bash
source forense-rag-logs/bin/activate
```

2. Acesse o diretório do projeto:
```bash
cd forense-rag-logs
```

3. Execute o Jupyter Notebook:
```bash
jupyter notebook
```

4. Execute as células sequencialmente.
Ao final do notebook, há uma célula com um exemplo completo, utilizando os dados disponíveis no repositório para demonstrar o funcionamento do pipeline de análise com RAG.

### Observações:
- Todos os datasets utilizados nos testes estão incluídos no repositório(eventlog.csv = 158k logs).
- A execução mínima permite visualizar o fluxo completo: indexação, recuperação, geração de resposta e análise.
- Caso ocorra algum erro, revise a instalação das dependências ou verifique se o modelo via Ollama está em execução.

# Experimentos

Esta seção deve descrever um passo a passo para a execução e obtenção dos resultados do artigo. Permitindo que os revisores consigam alcançar as reivindicações apresentadas no artigo.
Cada reivindicações deve ser apresentada em uma subseção, com detalhes de arquivos de configurações a serem alterados, comandos a serem executados, flags a serem utilizadas, tempo esperado de execução, expectativa de recursos a serem utilizados como 1GB RAM/Disk e resultado esperado.

Caso o processo para a reprodução de todos os experimentos não seja possível em tempo viável. Os autores devem escolher as principais reivindicações apresentadas no artigo e apresentar o respectivo processo para reprodução.

## Reivindicações #X

## Reivindicações #Y

# LICENSE

Apresente a licença.

