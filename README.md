# gerencia_fluxo_pacientes_ubs

# Sistema de Gestão de Fluxo de Pacientes para UBS

Este projeto implementa um sistema de fluxo de pacientes que abrange as etapas de recepção, triagem e atendimento clínico, com validação de dados e integração com a API da OpenAI para suporte dinâmico durante o atendimento.

## Funcionalidades
### 1. Administrativo (Recepção)

    Coleta dados pessoais do paciente, como:
        Nome, data de nascimento, sexo, CPF, telefone e número do cartão SUS.
    Anonimização: O CPF é anonimizado antes de ser armazenado, garantindo privacidade.
    Exemplo de anonimização:

anonimizar_cpf("123.456.789-00")  # Saída: anon-12345

### 2. Triagem

    Registra informações de saúde, incluindo:
        Queixa principal.
        Validação dos sinais vitais com o Pydantic, garantindo que os valores estejam dentro dos parâmetros clínicos aceitáveis:
            Pressão arterial (80 a 200 mmHg).
            Temperatura corporal (35 a 42 °C).
            Oxigenação (85% a 100%).
            Escala de dor (1 a 5).
    Integração com o modelo GPT-3.5-Turbo para análise da triagem e sugestões de conduta baseadas nos sinais vitais e informações do paciente.

### 3. Especialista

    Registra as observações do especialista, incluindo:
        Sinais observados.
        Sintomas relatados.
        Medicamentos prescritos.
        Exames solicitados.

### 4. Resumo do Atendimento

    Exibe um resumo completo das etapas realizadas, consolidando os dados de administrativo, triagem e especialista.


# Como Executar

    ## Clone o repositório:

git clone https://github.com/elaranjeiras/sistema-fluxo-pacientes.git
cd sistema-fluxo-pacientes

# Instale as dependências:

pip install -r requirements.txt

# Configure a chave da API da OpenAI:

Adicione sua chave de API como variável de ambiente:

export OPENAI_API_KEY="sua_chave_api"

# Ou substitua diretamente no código na linha:

openai.api_key = "sua_chave_api"

# Execute o sistema:

python main.py
