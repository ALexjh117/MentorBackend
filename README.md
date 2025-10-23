# MentorIA Backend

Backend de la plataforma educativa MentorIA con Express.js, agentes de IA y Supabase.

## 🚀 Despliegue en Render

### Configuración:
- **Build Command**: `npm install`
- **Start Command**: `npm start`
- **Environment**: `Web Service`
- **Node Version**: `18`

### Variables de entorno:
```bash
PORT=4000
NODE_ENV=production
SUPABASE_URL=https://catccvmyffumdnqcymxk.supabase.co
SUPABASE_SERVICE_ROLE=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
PROVIDER=bedrock
AWS_REGION=us-east-1
BEDROCK_MODEL_ID=amazon.titan-text-lite-v1
```

### Health Check:
- **Path**: `/api/health`

## 🔧 Desarrollo local:

```bash
npm install
npm run dev
```

## 📁 Estructura:
```
backend/
├── server/
│   ├── index.js      # Servidor principal
│   ├── mcp.js        # Model Context Protocol
│   └── a2a-agent.js  # Agent-to-Agent
└── package.json
```

## 🔗 Endpoints:
- `GET /api/health` - Health check
- `GET /api/tables` - Consultar tablas Supabase
- `POST /api/chat` - Chat con IA
- `POST /api/simulate-student` - Simular estudiante
- `GET /api/progress-metrics/:sessionId` - Métricas de progreso
