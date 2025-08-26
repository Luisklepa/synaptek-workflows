# Synaptek Workflows - Automatizaciones con n8n

Colección de workflows de n8n para automatización de procesos empresariales, generación de contenido y análisis de trading.

## 📋 Descripción General

Este repositorio contiene 4 workflows de n8n diseñados para automatizar diferentes procesos:

1. **Transformación de Podcasts a Clips de TikTok** - Automatización completa de contenido
2. **Pipeline de Datos de Trading** - Procesamiento de datos OHLCV con indicadores técnicos
3. **Generador de Señales de Trading** - Sistema de alertas automáticas
4. **Asistente de WhatsApp (SynapBot)** - CRM y atención automatizada de leads

## 🚀 Workflows Incluidos

### 1. 🎬 Transform Podcasts into Viral TikTok Clips
**Archivo**: `workflows/podcast-to-tiktok.json`

**Función**: Convierte automáticamente podcasts de YouTube en clips virales para TikTok.

**Proceso**:
- Descarga audio desde URL de YouTube
- Transcripción con AssemblyAI/Whisper
- Extracción de mejores momentos con Gemini AI
- Generación de clips con API de edición
- Creación automática de títulos y captions
- Publicación automática en TikTok

**APIs Requeridas**:
- AssemblyAI (transcripción)
- Google Gemini (análisis de contenido)
- OpenAI Whisper (transcripción alternativa)
- Andynocode (edición de video)
- Upload-Post (publicación en TikTok)

**Reducción de trabajo manual**: 80-95%

### 2. 📊 Pipeline de Datos de Trading
**Archivo**: `workflows/trading-pipeline.json`

**Función**: Descarga y enriquece datos OHLCV de Binance con indicadores técnicos.

**Proceso**:
- Descarga datos BTCUSDC (1 minuto) desde Binance
- Cálculo de indicadores técnicos:
  - EMAs (9, 21, 50, 200)
  - RSI Wilder (14)
  - Bandas de Bollinger
  - MACD (12, 26, 9)
  - ADX/DI+/DI- (14)
  - Supertrend (10, 3)
- Exportación como JSON enriquecido

**APIs Requeridas**:
- Binance API (datos OHLCV)

**Reducción de trabajo manual**: 60-80%

### 3. 📈 Generador de Señales de Trading
**Archivo**: `workflows/trading-signals.json`

**Función**: Genera señales de trading automáticas cada 15 minutos.

**Proceso**:
- Análisis de datos BTCUSDC (15 minutos)
- Aplicación de reglas técnicas para LONG/SHORT/NO TRADE
- Generación de explicaciones y ratios SL/TP
- Registro en Google Sheets
- Notificaciones por WhatsApp

**APIs Requeridas**:
- Binance API
- Google Sheets API
- WhatsApp Business API
- OpenAI GPT-4o (interpretación de señales)

**Reducción de trabajo manual**: 60-80%

### 4. 🤖 Asistente de WhatsApp (SynapBot)
**Archivo**: `workflows/whatsapp-assistant.json`

**Función**: Asistente inteligente para atención de leads y gestión de CRM.

**Proceso**:
- Procesamiento de mensajes (texto, audio, imagen)
- Transcripción de audio con OpenAI
- Análisis de imágenes con visión computacional
- Captura de datos de leads (rubro, proceso, contacto)
- Gestión de CRM en Google Sheets
- Envío de emails automáticos
- Módulo de backtesting para trading

**APIs Requeridas**:
- WhatsApp Business API
- OpenAI (Whisper, GPT-4o, Vision)
- Google Sheets API
- Gmail API
- Binance API (para backtesting)

**Reducción de trabajo manual**: 50-70%

## 🛠️ Configuración

### Prerrequisitos
- Cuenta de n8n (cloud o self-hosted)
- Acceso a las APIs mencionadas en cada workflow
- Credenciales configuradas en n8n

### Instalación
1. Clona este repositorio
2. Importa cada archivo JSON en tu instancia de n8n
3. Configura las credenciales necesarias
4. Ajusta los parámetros según tus necesidades

### Configuración de Credenciales
Cada workflow requiere configurar las siguientes credenciales en n8n:

#### APIs Comunes
- **OpenAI API**: Para transcripción, análisis y generación de contenido
- **Google Sheets API**: Para almacenamiento de datos
- **WhatsApp Business API**: Para notificaciones y atención

#### APIs Específicas
- **AssemblyAI**: Transcripción de audio
- **Google Gemini**: Análisis de contenido
- **Binance API**: Datos de trading
- **Andynocode**: Edición de video
- **Upload-Post**: Publicación en TikTok

## 📁 Estructura del Repositorio

```
synaptek-workflows/
├── README.md
├── workflows/
│   ├── podcast-to-tiktok.json
│   ├── trading-pipeline.json
│   ├── trading-signals.json
│   └── whatsapp-assistant.json
├── docs/
│   ├── setup-guide.md
│   ├── api-requirements.md
│   └── troubleshooting.md
└── examples/
    ├── sample-outputs/
    └── configuration-examples/
```

## 🔧 Personalización

### Variables de Entorno
Configura las siguientes variables según tu entorno:

```bash
# APIs de Trading
BINANCE_API_KEY=your_binance_api_key
BINANCE_SECRET_KEY=your_binance_secret

# APIs de IA
OPENAI_API_KEY=your_openai_key
GEMINI_API_KEY=your_gemini_key
ASSEMBLYAI_API_KEY=your_assemblyai_key

# APIs de Redes Sociales
WHATSAPP_TOKEN=your_whatsapp_token
TIKTOK_API_KEY=your_tiktok_key

# Google APIs
GOOGLE_SHEETS_CREDENTIALS=your_google_credentials
GMAIL_CREDENTIALS=your_gmail_credentials
```

### Parámetros Ajustables
- Intervalos de ejecución
- Pares de trading
- Configuración de indicadores técnicos
- Plantillas de mensajes
- Configuración de CRM

## 📊 Métricas de Eficiencia

| Workflow | Reducción Manual | Tiempo Ahorrado | ROI Estimado |
|----------|------------------|-----------------|--------------|
| Podcast → TikTok | 80-95% | 4-6 horas/semana | Alto |
| Pipeline Trading | 60-80% | 2-3 horas/día | Medio |
| Señales Trading | 60-80% | 1-2 horas/día | Alto |
| WhatsApp Assistant | 50-70% | 3-4 horas/día | Medio |

## 🚨 Consideraciones Importantes

### Seguridad
- Nunca compartas credenciales en el código
- Usa variables de entorno para datos sensibles
- Revisa permisos de APIs regularmente

### Mantenimiento
- Monitorea logs de ejecución
- Actualiza credenciales cuando sea necesario
- Revisa límites de APIs

### Compliance
- Cumple con términos de servicio de cada plataforma
- Respeta límites de rate limiting
- Mantén backups de configuraciones

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Fork el repositorio
2. Crea una rama para tu feature
3. Commit tus cambios
4. Push a la rama
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

## 📞 Soporte

Para soporte técnico o preguntas:
- Email: soporte@thesynaptek.com
- Website: https://thesynaptek.com
- LinkedIn: [Synaptek](https://www.linkedin.com/company/synaptek)

## 🔄 Actualizaciones

- **v1.0.0**: Versión inicial con 4 workflows principales
- Próximas actualizaciones incluirán:
  - Workflows adicionales
  - Mejoras en documentación
  - Nuevas integraciones

---

**Desarrollado por Synaptek** - Transformando empresas con automatización inteligente 🤖

