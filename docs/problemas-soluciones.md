# Problemas encontrados y soluciones

## ❌ FastAPI bloqueado
Causa: llamada síncrona a Ollama  
Solución: `run_in_executor`

## ❌ Respuestas lentas
Causa: sin swap  
Solución: añadir swap de 8GB

## ❌ Segunda pregunta falla
Causa: navegador corta conexión  
Solución: backend no bloqueante
