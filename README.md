# LLM local con Ollama + FastAPI

Proyecto para ejecutar un LLM local usando **Ollama (Mistral)** con un backend en **FastAPI** y un frontend web sencillo en HTML/JS.

## 🚀 Características
- LLM ejecutándose localmente con Ollama
- Backend FastAPI estable (no bloqueante)
- Frontend web minimalista
- Comunicación vía HTTP
- Pensado para VPS sin GPU

## 🧠 Stack
- Python 3.12
- FastAPI
- Ollama
- Mistral
- HTML + JavaScript

---

## 📦 Requisitos
- Linux (probado en Ubuntu VPS)
- Python 3.10+
- 12 GB RAM recomendado
- Swap habilitado
- Ollama instalado

---

⚙️ Instalación y ejecución (paso a paso)

Esta guía permite replicar el proyecto tal y como está funcionando actualmente, usando Ollama + FastAPI + frontend web simple.

1️⃣ Instalar Ollama y descargar el modelo
curl -fsSL https://ollama.com/install.sh | sh
ollama pull mistral

⚠️ Importante: Ollama debe quedar ejecutándose como servicio.
Si ollama serve ya está activo, no lo lances de nuevo (usa el puerto 11434).

Comprueba que responde:

curl http://localhost:11434/api/tags
2️⃣ Crear entorno virtual de Python

Desde la raíz del proyecto:

python3 -m venv venv
source venv/bin/activate
pip install fastapi uvicorn

✅ Probado con Python 3.12

3️⃣ Ejecutar el backend (FastAPI)

El backend expone un endpoint /ask que envía las preguntas al LLM vía Ollama.

uvicorn main:app --host 0.0.0.0 --port 8000

Comprueba que está activo:

http://IP_DEL_SERVIDOR:8000/docs
4️⃣ Ejecutar el frontend web

En otra terminal, desde la carpeta donde está index.html:

python3 -m http.server 80

Abre en el navegador:

http://IP_DEL_SERVIDOR
📡 Uso de la API
Endpoint

POST /ask

Request
{
  "question": "Hola, ¿quién eres?"
}
Response
{
  "answer": "..."
}
🧠 Notas importantes de funcionamiento

La primera pregunta puede tardar varios segundos (cold start del modelo).

Las siguientes preguntas son más rápidas.

El backend es no bloqueante, pero el modelo consume bastante RAM.

Recomendado activar swap en VPS sin GPU.

🛠️ Problemas comunes

⏳ Tarda mucho en responder
→ El modelo está inicializando o no hay swap suficiente.

❌ Error conectando con el backend
→ FastAPI no está levantado o el puerto 8000 no es accesible.

❌ Ollama no responde
→ Verifica que el servicio está activo y escuchando en 127.0.0.1:11434.

Consulta más detalles en docs/problemas-soluciones.md
