# Arquitectura del sistema

Navegador
↓
Frontend HTML/JS (HTTP)
↓
FastAPI (async + executor)
↓
Ollama CLI
↓
Modelo Mistral

cpp
Copiar código

FastAPI ejecuta Ollama en un thread separado para evitar bloqueo.
