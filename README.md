# Projeto-Integrador-Blaze-Machine-BMZ

# Projeto Integrador — Competição de Carrinhos

## Equipe

**Nome da equipe: Blaze Machine (Sigla: BMZ)**
**Turma: Mecatrônica 3º ano vespertino (Integrado)** 
**Professor técnico: Gustavo Lima**

### Integrantes e áreas de atuação

| Integrante | Área principal | Responsabilidades |
|---|---|---|
| Elias Da Silva Araújo Correia | Piloto e calibração | Testes de dirigibilidade, calibração e operação |
| Geovana Natália Albuquerque De Lima | Mecânica | Chassi, direção, transmissão e montagem |
| Rúbia Evellyn Alves Da Silva | Projeto e documentação | Arquitetura, desenhos, organização da documentação |
| João Pedro De Lima Félix | Eletrônica e integração elétrica | Alimentação, drivers, motores, sensores e conexões |
| Jair Alberti Da Silva Filho | Software e controle | Comunicação, controle, sensores e automação |

> As áreas acima indicam a responsabilidade principal de cada integrante, mas o trabalho pode ser compartilhado entre a equipe.

---

## 1. Objetivo do projeto

Desenvolver um veículo terrestre em pequena escala para participação na Competição de Carrinhos do Projeto Integrador. O veículo deverá percorrer a pista definida pela organização, respeitando os requisitos do regulamento e utilizando a interface de controle disponibilizada.

---

## 2. Conceito da solução

Descrever, de forma objetiva, a solução escolhida pela equipe.

Exemplo:

- arquitetura de tração: Dois Motores DC;
- direção: ____________________;
- controlador principal: ____________________;
- driver de motores: L298N;
- câmera embarcada: Telefone;
- estratégia de alimentação: Bateria;
- sensores adicionais, se houver: ____________________;
- recursos de automação, se houver: ____________________.

---

## 3. Arquitetura geral

Inserir aqui um diagrama da arquitetura do sistema ou um link para o arquivo correspondente em `docs/arquitetura/`.

Exemplo de organização:

```text
Volante da organização
        |
        | UDP
        v
      ESP32
        |
        +--> controle dos motores
        +--> sensores
        +--> atuadores
        |
        +--> MQTT --> telemetria

Celular embarcado --> transmissão de vídeo
```

### Subsistemas

- **Mecânica:** descrever resumidamente.
- **Eletrônica:** descrever resumidamente.
- **Software:** descrever resumidamente.
- **Comunicação:** descrever resumidamente.
- **Alimentação:** descrever resumidamente.

---

## 4. Estado atual do desenvolvimento

Atualizar esta seção ao longo do projeto.

### Concluído

- [ ] Definição da arquitetura geral
- [ ] Projeto mecânico inicial
- [ ] Diagrama elétrico inicial
- [ ] Comunicação com o sistema da organização
- [ ] Controle dos motores em bancada
- [ ] Integração mecânica
- [ ] Integração eletroeletrônica
- [ ] Teste do veículo em movimento
- [ ] Integração da câmera
- [ ] Outros: ____________________

### Em desenvolvimento

Descrever as atividades em andamento.

### Pendências principais

Descrever os principais pontos ainda não resolvidos.

---

## 5. Planejamento

O planejamento semanal da equipe está disponível em:

[`PLANEJAMENTO`](PLANEJAMENTO.md)

O registro semanal de atividades está disponível em:

[`PROGRESSO`](PROGRESSO.md)

---

## 6. Documentação técnica

Organização da documentação técnica, nas seguintes pastas:

```text
docs/
├── Registro de testes
```

### Documentos disponíveis

[`Registro de testes`](https://github.com/PJ132/Projeto-Integrador-Blaze-Machine-BMZ/blob/main/docs/testes/Registros%20de%20testes.md)

---

## 7. Materiais e componentes

| Item | Quantidade | Origem | Situação |
|---|---:|---|---|
| ESP32 | 1 | Kit da organização | Disponível |
| Cabo USB pra esp32 | 1 | Kit da organização | Disponível |
| Motor DC | 2 | Kit da organização | Disponível |
| Suportes de Motor | 4 |Kit da organização | Disponível |
| Driver de motor: L298N | 1 | Kit da organização | Disponível |
| Roda boba | 1 | Kit da organização | Disponível |
| Base de acrílico | 1 |Kit da organização | Disponível |
| Parafusos | 4 | Kit da organização | Disponível |
| Porcas | 4 | Kit da organização | Disponível |

---

## 8. Comunicação com a organização

### Comandos

- Protocolo: UDP unicast
- Porta: 5000
- Formato: JSON em UTF-8
- Frequência nominal: 60 Hz

Formato esperado:

```json
{
  "sequencia": 123,
  "volante": 0,
  "aceleracao": 0,
  "habilitado": true
}
```

### Telemetria

- Protocolo: MQTT 3.1.1 sobre TCP
- Porta: 1883
- Tópico previsto: `carrinhos/<equipe>/telemetria`

Os campos definitivos de telemetria serão definidos pela equipe em conjunto com os professores.

---

## 9. Testes realizados

[`Registro dos testes`](https://github.com/PJ132/Projeto-Integrador-Blaze-Machine-BMZ/blob/main/docs/testes/Registros%20de%20testes.md)

---

## 10. Observações

Registrar aqui informações importantes que não se encaixem nas demais seções.
