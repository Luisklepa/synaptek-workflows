# Guía de Configuración - Synaptek Workflows

## 📋 Prerrequisitos

### 1. Cuenta de n8n
- **n8n Cloud**: [https://cloud.n8n.io](https://cloud.n8n.io)
- **n8n Self-hosted**: [https://docs.n8n.io/hosting/](https://docs.n8n.io/hosting/)

### 2. APIs Requeridas

#### APIs de IA
- **OpenAI**: [https://platform.openai.com](https://platform.openai.com)
  - Whisper (transcripción)
  - GPT-4o (análisis y generación)
  - Vision (análisis de imágenes)
- **Google Gemini**: [https://aistudio.google.com](https://aistudio.google.com)
- **AssemblyAI**: [https://www.assemblyai.com](https://www.assemblyai.com)

#### APIs de Trading
- **Binance**: [https://www.binance.com](https://www.binance.com)
  - API Key y Secret Key
  - Permisos de lectura para datos OHLCV

#### APIs de Redes Sociales
- **WhatsApp Business**: [https://developers.facebook.com/docs/whatsapp](https://developers.facebook.com/docs/whatsapp)
- **Upload-Post**: [https://www.upload-post.com](https://www.upload-post.com)

#### APIs de Google
- **Google Sheets**: [https://console.cloud.google.com](https://console.cloud.google.com)
- **Gmail**: [https://console.cloud.google.com](https://console.cloud.google.com)

#### APIs de Edición
- **Andynocode**: [https://www.andynocode.com](https://www.andynocode.com)

## 🚀 Instalación Paso a Paso

### Paso 1: Clonar el Repositorio
```bash
git clone https://github.com/tu-usuario/synaptek-workflows.git
cd synaptek-workflows
```

### Paso 2: Configurar Credenciales en n8n

#### OpenAI
1. Ve a **Settings > Credentials** en n8n
2. Haz clic en **Add Credential**
3. Selecciona **OpenAI API**
4. Ingresa tu API Key
5. Guarda como "OpenAI Account"

#### Google Sheets
1. Ve a **Settings > Credentials**
2. Haz clic en **Add Credential**
3. Selecciona **Google Sheets OAuth2 API**
4. Sigue el flujo de autorización OAuth2
5. Guarda como "Google Sheets Account"

#### WhatsApp Business
1. Ve a **Settings > Credentials**
2. Haz clic en **Add Credential**
3. Selecciona **WhatsApp API**
4. Ingresa tu Access Token
5. Guarda como "WhatsApp Account"

#### Binance
1. Ve a **Settings > Credentials**
2. Haz clic en **Add Credential**
3. Selecciona **HTTP Header Auth**
4. Configura:
   - Name: `X-MBX-APIKEY`
   - Value: Tu API Key de Binance
5. Guarda como "Binance API"

### Paso 3: Importar Workflows

#### 1. Podcast to TikTok
1. Ve a **Workflows** en n8n
2. Haz clic en **Import from File**
3. Selecciona `workflows/podcast-to-tiktok.json`
4. Configura las credenciales necesarias
5. Activa el workflow

#### 2. Trading Pipeline
1. Importa `workflows/trading-pipeline.json`
2. Configura la credencial de Binance
3. Ajusta el par de trading si es necesario
4. Activa el workflow

#### 3. Trading Signals
1. Importa `workflows/trading-signals.json`
2. Configura todas las credenciales requeridas
3. Ajusta el intervalo de ejecución (15 minutos por defecto)
4. Activa el workflow

#### 4. WhatsApp Assistant
1. Importa `workflows/whatsapp-assistant.json`
2. Configura todas las credenciales
3. Configura los webhooks de WhatsApp
4. Activa el workflow

## ⚙️ Configuración Avanzada

### Variables de Entorno
Crea un archivo `.env` en tu proyecto:

```env
# APIs de Trading
BINANCE_API_KEY=tu_api_key
BINANCE_SECRET_KEY=tu_secret_key

# APIs de IA
OPENAI_API_KEY=tu_openai_key
GEMINI_API_KEY=tu_gemini_key
ASSEMBLYAI_API_KEY=tu_assemblyai_key

# APIs de Redes Sociales
WHATSAPP_TOKEN=tu_whatsapp_token
TIKTOK_API_KEY=tu_tiktok_key

# Google APIs
GOOGLE_SHEETS_CREDENTIALS=tu_google_credentials
GMAIL_CREDENTIALS=tu_gmail_credentials
```

### Configuración de Webhooks
Para el WhatsApp Assistant, necesitas configurar webhooks:

1. Ve a tu app de WhatsApp Business
2. Configura el webhook URL: `https://tu-n8n-instance.com/webhook/whatsapp-trigger`
3. Verifica el webhook

### Configuración de Google Sheets
Crea las siguientes hojas en Google Sheets:

1. **CRM**: Para datos de leads
2. **Trading Log**: Para señales de trading
3. **Backtest**: Para datos de backtesting

## 🔧 Personalización

### Ajustar Intervalos de Ejecución
- **Trading Pipeline**: 1 minuto (configurable)
- **Trading Signals**: 15 minutos (configurable)
- **WhatsApp Assistant**: En tiempo real

### Configurar Pares de Trading
Edita los workflows de trading para cambiar el par:
- Cambia `BTCUSDC` por el par deseado
- Ajusta los límites de datos según necesites

### Personalizar Prompts
En el WhatsApp Assistant, puedes editar los prompts:
- Busca los nodos de AI Agent
- Modifica los system messages según tu negocio

## 🚨 Solución de Problemas

### Error de Credenciales
- Verifica que las API keys sean válidas
- Revisa los permisos de las APIs
- Asegúrate de que las credenciales estén correctamente configuradas

### Error de Rate Limiting
- Ajusta los intervalos de ejecución
- Implementa retry logic en los nodos HTTP
- Considera usar diferentes API keys

### Error de Webhooks
- Verifica que la URL del webhook sea accesible
- Revisa los logs de n8n para errores
- Asegúrate de que el webhook esté activo

## 📞 Soporte

Si encuentras problemas:
1. Revisa los logs de n8n
2. Verifica la documentación de las APIs
3. Contacta soporte@thesynaptek.com

---

**Nota**: Esta guía asume que tienes conocimientos básicos de n8n. Si necesitas ayuda adicional, consulta la [documentación oficial de n8n](https://docs.n8n.io/).

