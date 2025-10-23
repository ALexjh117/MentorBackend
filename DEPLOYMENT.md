# MentorIA Backend

Backend API para MentorIA - Sistema de agentes de IA para análisis de argumentos y pensamiento crítico.

## Variables de Entorno Requeridas

Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

```env
# Configuración del Servidor
PORT=4000
NODE_ENV=production

# Proveedor de IA (elegir uno: "openai", "bedrock", o "demo")
PROVIDER=demo

# Configuración OpenAI (si usas OpenAI)
OPENAI_API_KEY=tu_clave_api_openai
OPENAI_BASE_URL=https://api.openai.com/v1
OPENAI_MODEL=gpt-4o-mini
OPENAI_ORG_ID=tu_org_id
OPENAI_PROJECT=tu_project_id

# Configuración AWS Bedrock (si usas Bedrock)
AWS_REGION=us-east-1
BEDROCK_MODEL_ID=anthropic.claude-3-5-sonnet-20241022-v1:0

# Configuración Supabase
SUPABASE_URL=tu_url_supabase
SUPABASE_SERVICE_ROLE=tu_clave_service_role_supabase

# Webhook N8N (opcional)
N8N_WEBHOOK_URL=tu_url_webhook_n8n
```

## Despliegue en Render

1. **Conecta tu repositorio** a Render
2. **Configura las variables de entorno** en el dashboard de Render
3. **Asegúrate de que**:
   - `Build Command`: `npm install`
   - `Start Command`: `npm start`
   - `Node Version`: `18.0.0` o superior

## Problemas Comunes

### El despliegue se queda en "building"

- Verifica que todas las variables de entorno estén configuradas
- Asegúrate de que `PROVIDER=demo` si no tienes claves de API configuradas
- Revisa los logs de Render para errores específicos

### Error de Supabase

- Verifica que `SUPABASE_URL` y `SUPABASE_SERVICE_ROLE` estén configuradas
- Asegúrate de que la clave de servicio tenga los permisos correctos

### Error de OpenAI/Bedrock

- Si usas `PROVIDER=demo`, no necesitas configurar claves de API
- Si usas `PROVIDER=openai`, configura `OPENAI_API_KEY`
- Si usas `PROVIDER=bedrock`, configura las variables de AWS

## Estructura del Proyecto

```
backend/
├── server/
│   ├── index.js          # Servidor principal Express
│   ├── mcp.js            # Protocolo de comunicación entre agentes
│   ├── a2a-agent.js      # Agente de análisis argumentativo
│   └── insightsRepo.ts   # Repositorio de insights (TypeScript)
├── package.json          # Dependencias y scripts
└── supabase-setup.sql    # Scripts de configuración de BD
```

## Endpoints Disponibles

- `POST /api/chat` - Chat con IA
- `POST /api/activity-agent` - Generación de actividades
- `POST /api/analyze-argument` - Análisis de argumentos
- `POST /api/generate-inclusive-activity` - Actividades inclusivas
- `GET /api/health` - Estado del servidor
- `GET /api/tables` - Consulta de tablas Supabase
- `POST /api/simulate-student` - Simulación de interacciones

## Desarrollo Local

```bash
cd backend
npm install
npm run dev
```

El servidor se ejecutará en `http://localhost:4000`
