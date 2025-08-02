# Sistema de Consulta de Clima por CEP com OTEL e Zipkin

Este projeto consiste em dois serviços que trabalham em conjunto para consultar a temperatura atual com base em um CEP fornecido, com suporte a tracing distribuído usando OpenTelemetry e Zipkin.

## Serviços

1. **Serviço A**: Recebe o CEP via POST, valida e encaminha para o Serviço B
   - Porta: 8080
   - Endpoint: `/cep` (POST)
   - curl -X POST http://localhost:8080/cep \
     -H "Content-Type: application/json" \
     -d '{"cep": "69041010"}'

2. **Serviço B**: Consulta o CEP, obtém a cidade e retorna as temperaturas
   - Porta: 8081
   - Endpoint: `/weather` (POST)

3. **Zipkin**: UI para visualização dos traces (Teste OK)
   - Porta: 9411
   - http://localhost:9411/

## Requisitos

- Docker
- Docker Compose
- Chave de API para WeatherAPI (opcional, há um valor padrão)

## Como Executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/mourasjames/otel-zipkin-api.git
   ```
