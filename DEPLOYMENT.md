# Guía de Despliegue - Vision&Señas-IA

Esta guía te ayudará a desplegar el proyecto en Vercel (frontend) y Render (backend).

## 📋 Prerrequisitos

- Cuenta en [Vercel](https://vercel.com)
- Cuenta en [Render](https://render.com)
- Git configurado
- Proyecto en GitHub

## 🚀 Despliegue del Backend en Render

### 1. Preparar el repositorio
```bash
# Asegúrate de que todos los archivos estén en GitHub
git add .
git commit -m "Preparar para despliegue"
git push origin main
```

### 2. Crear servicio en Render
1. Ve a [Render Dashboard](https://dashboard.render.com)
2. Haz clic en "New +" → "Web Service"
3. Conecta tu repositorio de GitHub
4. Configura el servicio:
   - **Name**: `vision-senas-backend`
   - **Environment**: `Python 3`
   - **Build Command**: `pip install -r app/requirements.txt`
   - **Start Command**: `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
   - **Plan**: Free

### 3. Variables de entorno
En Render, ve a "Environment" y agrega:
- `PYTHON_VERSION=3.10.0`

### 4. Desplegar
- Haz clic en "Create Web Service"
- Render construirá y desplegará automáticamente
- Copia la URL del servicio (ej: `https://vision-senas-backend.onrender.com`)

## 🌐 Despliegue del Frontend en Vercel

### 1. Preparar variables de entorno
1. Ve a [Vercel Dashboard](https://vercel.com/dashboard)
2. Importa tu proyecto desde GitHub
3. En "Settings" → "Environment Variables", agrega:
   - **Name**: `REACT_APP_API_URL`
   - **Value**: `https://tu-backend-url.onrender.com` (URL de tu backend en Render)

### 2. Configurar Vercel
- **Framework Preset**: Create React App
- **Root Directory**: `wa/frontend`
- **Build Command**: `npm run build`
- **Output Directory**: `build`

### 3. Desplegar
- Haz clic en "Deploy"
- Vercel construirá y desplegará automáticamente

## 🔧 Configuración Local

### Backend
```bash
cd wa/backend
python -m uvicorn app.main:app --reload
```

### Frontend
```bash
cd wa/frontend
npm start
```

## 📝 URLs de Producción

- **Frontend**: `https://tu-proyecto.vercel.app`
- **Backend**: `https://tu-backend.onrender.com`

## 🔍 Verificación

### Backend
- Visita: `https://tu-backend.onrender.com/docs`
- Deberías ver la documentación de la API

### Frontend
- Visita: `https://tu-proyecto.vercel.app`
- Navega a `/aritmetica` y prueba la funcionalidad

## ⚠️ Notas Importantes

### Render (Backend)
- El plan gratuito tiene limitaciones de CPU
- El servicio se "duerme" después de 15 minutos de inactividad
- La primera solicitud después de dormir puede tardar ~30 segundos

### Vercel (Frontend)
- El plan gratuito es suficiente para este proyecto
- Las builds automáticas se ejecutan en cada push a main

### CORS
- El backend está configurado para aceptar requests desde localhost y Vercel
- Si cambias el dominio de Vercel, actualiza `allowed_origins` en `main.py`

## 🐛 Solución de Problemas

### Backend no responde
1. Verifica que el servicio esté "Live" en Render
2. Revisa los logs en Render Dashboard
3. Asegúrate de que el puerto sea `$PORT`

### Frontend no conecta con backend
1. Verifica la variable `REACT_APP_API_URL` en Vercel
2. Revisa la consola del navegador para errores de CORS
3. Confirma que la URL del backend sea correcta

### Cámara no funciona en producción
- La cámara web no está disponible en servidores
- Esta funcionalidad solo funciona en desarrollo local
- Considera usar WebRTC para streaming en producción

## 📞 Soporte

Si tienes problemas:
1. Revisa los logs en Render/Vercel
2. Verifica las variables de entorno
3. Confirma que las URLs sean correctas
4. Revisa la configuración de CORS
