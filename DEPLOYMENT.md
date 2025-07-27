# 🚀 DEPLOYMENT EN VERCEL - PRESTAPP

## 📋 **Pasos para deployar en Vercel**

### 1. **Preparación del proyecto**
```bash
# Asegúrate de que todas las dependencias estén instaladas
npm install
cd cliente && npm install
```

### 2. **Configurar Vercel CLI (opcional)**
```bash
npm i -g vercel
vercel login
```

### 3. **Deploy desde GitHub (Recomendado)**

1. **Sube tu código a GitHub:**
   ```bash
   git add .
   git commit -m "Preparado para deployment en Vercel"
   git push origin main
   ```

2. **En Vercel Dashboard:**
   - Conecta tu repositorio de GitHub
   - Vercel detectará automáticamente la configuración

### 4. **Configurar Variables de Entorno en Vercel**

En el dashboard de Vercel, ve a Settings → Environment Variables y agrega:

```
MONGO_URL = tu_mongodb_atlas_connection_string
JWT_SECRET = tu_jwt_secret_super_seguro
NODE_ENV = production
```

### 5. **Deploy Manual (alternativo)**
```bash
vercel --prod
```

## 🔧 **Configuración incluida**

### ✅ **Archivos creados/modificados:**

- `vercel.json` - Configuración principal de Vercel
- `api/index.js` - Punto de entrada para serverless functions
- `server/index.js` - Modificado para compatibilidad con Vercel
- `cliente/src/services/ApiService.js` - URLs dinámicas para prod/dev
- `cliente/vite.config.js` - Configuración optimizada para build
- `.vercelignore` - Archivos a ignorar en deploy
- `.env.example` - Plantilla de variables de entorno

### 🌐 **Rutas configuradas:**

- `/api/*` → Backend serverless functions
- `/*` → Frontend React (SPA)

### 📦 **Build process:**

1. **Backend:** Se ejecuta como serverless functions en `/api`
2. **Frontend:** Build estático servido desde la raíz

## 🔍 **Verificación del deployment**

1. **Backend API:** `https://tu-app.vercel.app/api/auth/login`
2. **Frontend:** `https://tu-app.vercel.app`

## 🛠️ **Troubleshooting**

### Error: "Module not found"
- Verifica que todas las dependencias estén en `package.json`
- Asegúrate de que las rutas de importación sean correctas

### Error: "Environment variables not loaded"
- Configura las variables en Vercel Dashboard
- No incluyas el archivo `.env` en el repositorio

### Error: "Database connection failed"
- Verifica tu string de conexión MongoDB Atlas
- Asegúrate de que tu IP esté en la whitelist de MongoDB

## 📱 **URLs después del deployment**

- **Frontend:** `https://tu-proyecto.vercel.app`
- **API:** `https://tu-proyecto.vercel.app/api`
- **Login:** `https://tu-proyecto.vercel.app/api/auth/login`

## 🔄 **Desarrollo local**

Para seguir desarrollando localmente:

```bash
# Backend
npm run dev

# Frontend (en otra terminal)
cd cliente && npm run dev
```

El proyecto está configurado para usar:
- **Desarrollo:** `localhost:5000` para API
- **Producción:** URLs relativas `/api`
