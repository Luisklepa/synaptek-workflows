# Requisitos de APIs - Synaptek Workflows

## 📋 Resumen de APIs Requeridas

| API | Propósito | Plan Gratuito | Costo Estimado |
|-----|-----------|---------------|----------------|
| OpenAI | Transcripción, análisis, generación | $5 crédito | $0.01-0.10 por uso |
| Google Gemini | Análisis de contenido | Gratuito | $0.001-0.01 por uso |
| AssemblyAI | Transcripción de audio | 3 horas/mes | $0.25/hora |
| Binance | Datos de trading | Gratuito | Gratuito |
| WhatsApp Business | Mensajería | $0.005/mensaje | $0.005/mensaje |
| Google Sheets | Almacenamiento | Gratuito | Gratuito |
| Gmail | Envío de emails | Gratuito | Gratuito |
| Upload-Post | Publicación TikTok | $9.99/mes | $9.99/mes |
| Andynocode | Edición de video | $29/mes | $29/mes |

## 🔧 Configuración Detallada por API

### 1. OpenAI API

#### Propósito
- Transcripción de audio (Whisper)
- Análisis de texto (GPT-4o)
- Análisis de imágenes (Vision)
- Generación de contenido

#### Configuración
1. Ve a [https://platform.openai.com](https://platform.openai.com)
2. Crea una cuenta o inicia sesión
3. Ve a **API Keys**
4. Crea una nueva API key
5. Copia la key (formato: `sk-...`)

#### Límites y Costos
- **Rate Limit**: 3,000 requests/minuto
- **Whisper**: $0.006/minuto de audio
- **GPT-4o**: $0.0025/1K tokens input, $0.01/1K tokens output
- **Vision**: $0.01/1K tokens

#### Uso en Workflows
```json
{
  "credential": "OpenAI API",
  "apiKey": "sk-...",
  "model": "gpt-4o-mini"
}
```

### 2. Google Gemini API

#### Propósito
- Análisis de contenido de podcasts
- Extracción de mejores momentos
- Generación de títulos y captions

#### Configuración
1. Ve a [https://aistudio.google.com](https://aistudio.google.com)
2. Crea una cuenta de Google AI Studio
3. Ve a **API Keys**
4. Crea una nueva API key
5. Copia la key

#### Límites y Costos
- **Rate Limit**: 15 requests/segundo
- **Gemini 2.0 Flash**: $0.000075/1K tokens input, $0.0003/1K tokens output
- **Plan gratuito**: 15 requests/segundo

#### Uso en Workflows
```json
{
  "credential": "Google Gemini API",
  "apiKey": "AIza...",
  "model": "models/gemini-2.0-flash"
}
```

### 3. AssemblyAI API

#### Propósito
- Transcripción de audio de alta calidad
- Análisis de sentimiento
- Detección de entidades

#### Configuración
1. Ve a [https://www.assemblyai.com](https://www.assemblyai.com)
2. Crea una cuenta
3. Ve a **API Keys**
4. Copia tu API key

#### Límites y Costos
- **Plan gratuito**: 3 horas de transcripción/mes
- **Plan pago**: $0.25/hora de audio
- **Rate Limit**: 10 requests/segundo

#### Uso en Workflows
```json
{
  "credential": "HTTP Header Auth",
  "name": "Authorization",
  "value": "tu_api_key"
}
```

### 4. Binance API

#### Propósito
- Datos OHLCV de trading
- Información de mercado en tiempo real

#### Configuración
1. Ve a [https://www.binance.com](https://www.binance.com)
2. Crea una cuenta o inicia sesión
3. Ve a **API Management**
4. Crea una nueva API key
5. Configura permisos de lectura

#### Límites y Costos
- **Rate Limit**: 1,200 requests/minuto
- **Costo**: Gratuito para datos públicos
- **Permisos**: Solo lectura (no trading)

#### Uso en Workflows
```json
{
  "credential": "HTTP Header Auth",
  "name": "X-MBX-APIKEY",
  "value": "tu_api_key"
}
```

### 5. WhatsApp Business API

#### Propósito
- Envío y recepción de mensajes
- Notificaciones automáticas
- Atención al cliente

#### Configuración
1. Ve a [https://developers.facebook.com](https://developers.facebook.com)
2. Crea una app de Facebook
3. Configura WhatsApp Business API
4. Obtén el Access Token
5. Configura webhooks

#### Límites y Costos
- **Rate Limit**: 1,000 requests/segundo
- **Costo**: $0.005 por mensaje
- **Webhook**: Requerido para recepción

#### Uso en Workflows
```json
{
  "credential": "WhatsApp API",
  "accessToken": "tu_access_token",
  "phoneNumberId": "tu_phone_number_id"
}
```

### 6. Google Sheets API

#### Propósito
- Almacenamiento de datos de CRM
- Logs de trading
- Datos de backtesting

#### Configuración
1. Ve a [https://console.cloud.google.com](https://console.cloud.google.com)
2. Crea un proyecto
3. Habilita Google Sheets API
4. Crea credenciales OAuth2
5. Descarga el archivo JSON

#### Límites y Costos
- **Rate Limit**: 300 requests/minuto
- **Costo**: Gratuito hasta 10M requests/mes
- **Quotas**: 300 requests/minuto por usuario

#### Uso en Workflows
```json
{
  "credential": "Google Sheets OAuth2 API",
  "clientId": "tu_client_id",
  "clientSecret": "tu_client_secret"
}
```

### 7. Gmail API

#### Propósito
- Envío de emails automáticos
- Respuestas automáticas
- Notificaciones por email

#### Configuración
1. Ve a [https://console.cloud.google.com](https://console.cloud.google.com)
2. Habilita Gmail API
3. Crea credenciales OAuth2
4. Configura scopes de Gmail

#### Límites y Costos
- **Rate Limit**: 250 requests/segundo
- **Costo**: Gratuito
- **Quotas**: 1B requests/día

### 8. Upload-Post API

#### Propósito
- Publicación automática en TikTok
- Gestión de contenido social

#### Configuración
1. Ve a [https://www.upload-post.com](https://www.upload-post.com)
2. Crea una cuenta
3. Obtén tu API key
4. Configura las plataformas

#### Límites y Costos
- **Plan**: $9.99/mes
- **Límites**: Según el plan
- **Plataformas**: TikTok, Instagram, YouTube

### 9. Andynocode API

#### Propósito
- Edición automática de video
- Generación de clips
- Efectos y transiciones

#### Configuración
1. Ve a [https://www.andynocode.com](https://www.andynocode.com)
2. Crea una cuenta
3. Obtén tu API key
4. Configura los templates

#### Límites y Costos
- **Plan**: $29/mes
- **Límites**: Según el plan
- **Funciones**: Edición de video, efectos, exportación

## 🔒 Seguridad y Mejores Prácticas

### Protección de Credenciales
- Nunca compartas API keys en el código
- Usa variables de entorno
- Rota las keys regularmente
- Usa permisos mínimos necesarios

### Rate Limiting
- Implementa retry logic
- Usa exponential backoff
- Monitorea el uso de APIs
- Considera usar múltiples keys

### Monitoreo
- Configura alertas de uso
- Revisa logs regularmente
- Monitorea costos
- Verifica límites de APIs

## 📊 Estimación de Costos Mensuales

### Escenario Básico (1 usuario)
- OpenAI: $5-15/mes
- Google Gemini: $1-5/mes
- AssemblyAI: $0-10/mes
- WhatsApp: $5-20/mes
- Upload-Post: $9.99/mes
- Andynocode: $29/mes
- **Total**: $50-90/mes

### Escenario Empresarial (10 usuarios)
- OpenAI: $50-150/mes
- Google Gemini: $10-50/mes
- AssemblyAI: $50-200/mes
- WhatsApp: $50-200/mes
- Upload-Post: $9.99/mes
- Andynocode: $29/mes
- **Total**: $200-650/mes

## 🚨 Consideraciones Importantes

### Compliance
- Cumple con términos de servicio
- Respeta límites de rate limiting
- Mantén backups de configuraciones
- Documenta cambios en APIs

### Mantenimiento
- Actualiza credenciales regularmente
- Monitorea cambios en APIs
- Prueba workflows regularmente
- Mantén documentación actualizada

---

**Nota**: Los costos y límites pueden cambiar. Verifica siempre la documentación oficial de cada API.

