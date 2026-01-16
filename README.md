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

## ⚙️ Instalación

### 1️⃣ Instalar Ollama
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull mistral
2️⃣ Crear entorno virtual
bash
Copiar código
python3 -m venv venv
source venv/bin/activate
pip install fastapi uvicorn
3️⃣ Backend
bash
Copiar código
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000
4️⃣ Frontend
bash
Copiar código
cd web
python3 -m http.server 80
Abre en el navegador:

cpp
Copiar código
http://IP_DEL_SERVIDOR
📡 Endpoint
POST /ask
json
Copiar código
{
  "question": "Hola, ¿quién eres?"
}
Respuesta:

json
Copiar código
{
  "answer": "..."
}
🛠️ Problemas comunes
Si tarda mucho → comprobar swap

Si no responde → Ollama no está warm

Si hay errores → revisar procesos Ollama

Ver docs/problemas-soluciones.md
