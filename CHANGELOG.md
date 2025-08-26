# 📋 Changelog

Todos los cambios notables en este proyecto serán documentados en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
y este proyecto adhiere a [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Nuevos workflows de automatización
- Mejoras en documentación
- Nuevas integraciones de APIs

## [1.0.0] - 2025-01-XX

### Added
- **Transformación de Podcasts a Clips de TikTok**
  - Descarga automática de audio desde YouTube
  - Transcripción con AssemblyAI/Whisper
  - Extracción de mejores momentos con Gemini AI
  - Generación automática de clips
  - Publicación automática en TikTok
  - Reducción de trabajo manual: 80-95%

- **Pipeline de Datos de Trading**
  - Descarga de datos OHLCV desde Binance
  - Cálculo de indicadores técnicos (EMAs, RSI, Bollinger, MACD, ADX, Supertrend)
  - Exportación como JSON enriquecido
  - Reducción de trabajo manual: 60-80%

- **Generador de Señales de Trading**
  - Análisis automático cada 15 minutos
  - Generación de señales LONG/SHORT/NO TRADE
  - Registro en Google Sheets
  - Notificaciones por WhatsApp
  - Reducción de trabajo manual: 60-80%

- **Asistente de WhatsApp (SynapBot)**
  - Procesamiento de mensajes (texto, audio, imagen)
  - Transcripción de audio con OpenAI
  - Análisis de imágenes con visión computacional
  - Captura de datos de leads
  - Gestión de CRM en Google Sheets
  - Envío de emails automáticos
  - Módulo de backtesting para trading
  - Reducción de trabajo manual: 50-70%

### Documentation
- README.md completo con descripción de todos los workflows
- Guías de configuración detalladas
- Documentación de APIs requeridas
- Guía de troubleshooting
- Ejemplos de configuración

### Infrastructure
- Estructura de repositorio organizada
- Archivos de configuración (.gitignore, LICENSE)
- Documentación técnica completa

---

## Tipos de Cambios

- **Added** para nuevas funcionalidades
- **Changed** para cambios en funcionalidades existentes
- **Deprecated** para funcionalidades que serán removidas
- **Removed** para funcionalidades removidas
- **Fixed** para correcciones de bugs
- **Security** para vulnerabilidades de seguridad
