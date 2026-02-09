## 🎙️ Speechify - API de Transcrição de Áudio com Spring Boot + OpenAI

Este projeto é uma **API REST em Spring Boot** que recebe um arquivo de áudio (`.wav`, `.mp3`, `.m4a`) e retorna a transcrição do conteúdo utilizando o **Spring AI + OpenAI Audio Transcription (Whisper)**.

---

# 🚀 Funcionalidades

* Upload de arquivos de áudio via HTTP POST
* Transcrição automática usando OpenAI
* Configuração via `application.properties`
* Suporte a WAV, MP3, M4A (e outros formatos suportados pela OpenAI)

---

# 🧪 Como Testar (Gerar Áudio de Exemplo)

Você pode gerar um áudio facilmente usando o site abaixo:

👉 [https://ttsmp3.com/](https://ttsmp3.com/)

## Passos:

1. Digite um texto em inglês ou português
2. Escolha uma voz
3. Clique em **Convert to MP3**
4. Baixe o arquivo `.mp3`
5. Envie o arquivo para a API

---

# ⚙️ Configuração do Projeto

## 1️⃣ application.properties

Crie o arquivo `src/main/resources/application.properties`:

```properties
spring.ai.openai.api-key=SUA_API_KEY_AQUI
spring.ai.openai.base-url=https://api.openai.com
```

---

## 2️⃣ Dependência Maven

No `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.ai</groupId>
    <artifactId>spring-ai-openai-spring-boot-starter</artifactId>
</dependency>
```

---

# 📡 Endpoint da API

## 🔹 Transcrever Áudio

**POST**

```
http://localhost:8081/api/speechify
```

### Body (form-data)

| Key  | Type | Value         |
| ---- | ---- | ------------- |
| file | File | seu_audio.mp3 |

---

# 🧪 Testando com Postman

1. Método: **POST**
2. Body → **form-data**
3. Key: `file`
4. Type: File
5. Envie o arquivo de áudio

---

# ⚠️ Problema Comum: Erro de Cota de Token

Se você enviar um áudio e receber um erro HTTP 400, 401, 429 ou 500, pode ser **porque sua cota de tokens acabou**.

## 🧨 Por que isso acontece?

A OpenAI cobra por:

* Tamanho do áudio
* Tempo de áudio (segundos)
* Número de requisições

Quando o limite gratuito acaba, a API retorna erro.

---

## Como Resolver

1. Verifique sua conta OpenAI
2. Adicione um cartão de crédito
3. Gere uma nova API Key
4. Atualize no `application.properties`

---

# 🧠 Tecnologias Usadas

* Java 17+
* Spring Boot
* Spring AI
* OpenAI Whisper API
* Maven

---

# ⭐ Dica

Se a transcrição demorar ou der erro, tente:

* Reduzir o tamanho do áudio
* Converter para WAV
* Usar inglês (Whisper funciona melhor)
