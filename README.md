# Vision&Señas-IA - Sistema de Reconocimiento de Lenguaje de Señas

Sistema avanzado de reconocimiento de lenguaje de señas usando MediaPipe, Machine Learning y operaciones matemáticas en tiempo real.

## 🚀 Características

- **Reconocimiento en tiempo real** de vocales, abecedario y números
- **Operaciones matemáticas** con señas (suma, resta, multiplicación, división)
- **Interfaz moderna** con React y Framer Motion
- **API REST** con FastAPI y MediaPipe
- **Diseño responsive** para desktop y móvil

## 📋 Prerrequisitos

- Python 3.10+
- Node.js 16+
- Cámara web
- Git

## 🛠️ Instalación y Uso Local

### Backend (Python / FastAPI)

1. **Abrir PowerShell y navegar a la carpeta backend:**
   ```powershell
   cd wa/backend
   ```

2. **Crear y activar entorno virtual:**
   ```powershell
   python -m venv venv
   # O si tienes otra versión de Python:
   # py -3.11 -m venv venv
   venv\Scripts\activate
   ```

3. **Instalar dependencias:**
   ```powershell
   pip install -r app/requirements.txt
   ```

4. **Ejecutar el servidor:**
   ```powershell
   python -m uvicorn app.main:app --reload
   ```

### Frontend (React)

1. **Abrir otra terminal y navegar a la carpeta frontend:**
   ```powershell
   cd wa/frontend
   ```

2. **Instalar dependencias:**
   ```powershell
   npm install
   ```

3. **Iniciar la aplicación:**
   ```powershell
   npm start
   ```

## 🌐 Uso

- **Aplicación principal**: http://localhost:3000
- **API Documentation**: http://localhost:8000/docs
- **Módulo de Aritmética**: http://localhost:3000/aritmetica

### Funcionalidades:

1. **Reconocimiento de Señas**:
   - Vocales (A, E, I, O, U)
   - Abecedario completo
   - Números del 0-9
   - Operaciones matemáticas

2. **Operaciones Matemáticas**:
   - Suma, resta, multiplicación y división
   - Detección de números del 1-5 con ambas manos
   - Cálculos en tiempo real

3. **Entrenamiento de Modelos**:
   - Captura de muestras de entrenamiento
   - Entrenamiento de modelos personalizados
   - Evaluación de precisión

## 🚀 Despliegue en Producción

### Opción 1: Despliegue Automático

Para desplegar en **Vercel** (frontend) y **Render** (backend):

1. **Sigue la guía completa**: [DEPLOYMENT.md](./DEPLOYMENT.md)

### Opción 2: Despliegue Manual

#### Backend en Render:
- Conecta tu repositorio GitHub
- Configura: `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
- Variables de entorno: `PYTHON_VERSION=3.10.0`

#### Frontend en Vercel:
- Importa proyecto desde GitHub
- Root Directory: `wa/frontend`
- Variable de entorno: `REACT_APP_API_URL=https://tu-backend.onrender.com`

## 🔧 Configuración de Variables de Entorno

### Desarrollo Local
```bash
# Backend: No requiere variables adicionales
# Frontend: Usa http://localhost:8000 por defecto
```

### Producción
```bash
# Backend (Render): PYTHON_VERSION=3.10.0
# Frontend (Vercel): REACT_APP_API_URL=https://tu-backend.onrender.com
```

## 📁 Estructura del Proyecto

```
wa/
├── backend/
│   ├── app/
│   │   ├── main.py              # API principal
│   │   ├── matematicas.py       # Módulo de operaciones matemáticas
│   │   ├── model_utils.py       # Utilidades de ML
│   │   └── requirements.txt     # Dependencias Python
│   ├── models/                  # Modelos entrenados
│   └── render.yaml             # Configuración Render
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Aritmetica/      # Módulo de aritmética
│   │   │   ├── Dashboard/       # Panel de administración
│   │   │   └── UserDashboard/   # Panel de usuario
│   │   └── App.js              # Aplicación principal
│   ├── package.json            # Dependencias Node.js
│   └── vercel.json             # Configuración Vercel
└── DEPLOYMENT.md               # Guía de despliegue
```

## 🐛 Solución de Problemas

### Problemas Comunes:

1. **Cámara no funciona**:
   - Verifica permisos del navegador
   - Asegúrate de que no esté siendo usada por otra aplicación

2. **Error de CORS**:
   - Verifica la configuración en `main.py`
   - Confirma que las URLs estén correctas

3. **Modelo no entrena**:
   - Necesitas al menos 10 muestras por clase
   - Verifica que las manos sean detectadas correctamente

## 📞 Soporte

Para problemas o preguntas:
1. Revisa los logs en la consola del navegador
2. Verifica la documentación de la API en `/docs`
3. Consulta la guía de despliegue en `DEPLOYMENT.md`

## 📄 Licencia

Este proyecto está desarrollado para fines educativos y de investigación.
