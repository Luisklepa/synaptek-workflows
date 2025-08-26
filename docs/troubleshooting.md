# Solución de Problemas - Synaptek Workflows

## 🚨 Problemas Comunes y Soluciones

### 1. Errores de Credenciales

#### Problema: "Invalid API Key"
**Síntomas:**
- Error 401 Unauthorized
- Mensaje "Invalid API key" o "Authentication failed"

**Soluciones:**
1. Verifica que la API key sea correcta
2. Asegúrate de que no haya espacios extra
3. Revisa que la key no haya expirado
4. Verifica los permisos de la API key

**Prevención:**
- Usa variables de entorno para las keys
- Rota las keys regularmente
- Monitorea el uso de APIs

#### Problema: "Rate Limit Exceeded"
**Síntomas:**
- Error 429 Too Many Requests
- Mensaje "Rate limit exceeded"

**Soluciones:**
1. Reduce la frecuencia de ejecución
2. Implementa retry logic con exponential backoff
3. Usa múltiples API keys
4. Optimiza las requests

**Ejemplo de retry logic:**
```javascript
// En un Code node
const maxRetries = 3;
const baseDelay = 1000;

for (let attempt = 1; attempt <= maxRetries; attempt++) {
  try {
    // Tu request aquí
    break;
  } catch (error) {
    if (error.status === 429 && attempt < maxRetries) {
      const delay = baseDelay * Math.pow(2, attempt - 1);
      await new Promise(resolve => setTimeout(resolve, delay));
    } else {
      throw error;
    }
  }
}
```

### 2. Errores de Webhooks

#### Problema: "Webhook not receiving data"
**Síntomas:**
- Los webhooks no se activan
- No se reciben mensajes de WhatsApp

**Soluciones:**
1. Verifica que la URL del webhook sea accesible
2. Asegúrate de que el webhook esté verificado
3. Revisa los logs de n8n
4. Verifica la configuración en WhatsApp Business

**Verificación de webhook:**
```bash
# Prueba la URL del webhook
curl -X POST https://tu-n8n-instance.com/webhook/whatsapp-trigger \
  -H "Content-Type: application/json" \
  -d '{"test": "data"}'
```

#### Problema: "Webhook verification failed"
**Síntomas:**
- Error al verificar webhook
- No se puede activar el webhook

**Soluciones:**
1. Asegúrate de que la URL sea HTTPS
2. Verifica que el puerto sea correcto
3. Revisa que no haya firewall bloqueando
4. Verifica la configuración de SSL

### 3. Errores de Google Sheets

#### Problema: "Permission denied"
**Síntomas:**
- Error 403 Forbidden
- No se puede escribir en Google Sheets

**Soluciones:**
1. Verifica los permisos de la cuenta de servicio
2. Asegúrate de que la hoja sea editable
3. Revisa que las credenciales OAuth2 tengan los scopes correctos
4. Verifica que la hoja no esté protegida

**Scopes requeridos:**
```
https://www.googleapis.com/auth/spreadsheets
https://www.googleapis.com/auth/drive
```

#### Problema: "Sheet not found"
**Síntomas:**
- Error 404 Not Found
- No se encuentra la hoja especificada

**Soluciones:**
1. Verifica el ID de la hoja
2. Asegúrate de que la hoja exista
3. Verifica que tengas acceso a la hoja
4. Revisa el nombre de la hoja

### 4. Errores de Trading

#### Problema: "Invalid symbol"
**Síntomas:**
- Error al obtener datos de Binance
- Símbolo no encontrado

**Soluciones:**
1. Verifica que el símbolo sea correcto (ej: BTCUSDC)
2. Asegúrate de que el par esté activo
3. Revisa la documentación de Binance
4. Prueba con un símbolo diferente

#### Problema: "Data not available"
**Síntomas:**
- No se obtienen datos OHLCV
- Arrays vacíos en los indicadores

**Soluciones:**
1. Verifica el intervalo de tiempo
2. Asegúrate de que haya datos para el período
3. Revisa los límites de la API
4. Prueba con un período más corto

### 5. Errores de IA

#### Problema: "Model not available"
**Síntomas:**
- Error al usar modelos de OpenAI/Gemini
- Modelo no encontrado

**Soluciones:**
1. Verifica que el modelo esté disponible
2. Asegúrate de que tengas acceso al modelo
3. Revisa la documentación de la API
4. Usa un modelo alternativo

#### Problema: "Token limit exceeded"
**Síntomas:**
- Error al procesar texto muy largo
- Límite de tokens superado

**Soluciones:**
1. Reduce el tamaño del texto de entrada
2. Implementa chunking del texto
3. Usa un modelo con mayor capacidad
4. Optimiza los prompts

### 6. Errores de Video/Audio

#### Problema: "File too large"
**Síntomas:**
- Error al procesar archivos grandes
- Límite de tamaño superado

**Soluciones:**
1. Reduce la calidad del audio/video
2. Divide el archivo en partes más pequeñas
3. Usa compresión
4. Verifica los límites de la API

#### Problema: "Unsupported format"
**Síntomas:**
- Error al procesar archivos
- Formato no soportado

**Soluciones:**
1. Convierte el archivo a un formato soportado
2. Verifica la lista de formatos soportados
3. Usa herramientas de conversión
4. Revisa la documentación de la API

## 🔧 Herramientas de Diagnóstico

### 1. Logs de n8n
```bash
# Ver logs en tiempo real
docker logs -f n8n

# Ver logs específicos
docker logs n8n | grep "ERROR"
```

### 2. Testing de APIs
```bash
# Probar OpenAI
curl -X POST https://api.openai.com/v1/chat/completions \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model": "gpt-4o-mini", "messages": [{"role": "user", "content": "Hello"}]}'

# Probar Binance
curl -X GET "https://api.binance.com/api/v3/klines?symbol=BTCUSDC&interval=1m&limit=10"
```

### 3. Monitoreo de Workflows
```javascript
// En un Code node para debugging
console.log('Input data:', JSON.stringify($input.all(), null, 2));
console.log('Node parameters:', JSON.stringify($node.parameters, null, 2));
```

## 📊 Métricas de Monitoreo

### KPIs Importantes
- **Tasa de éxito**: % de ejecuciones exitosas
- **Tiempo de respuesta**: Latencia promedio
- **Uso de APIs**: Requests por minuto/hora
- **Costos**: Gasto mensual por API
- **Errores**: Número y tipo de errores

### Alertas Recomendadas
- Tasa de éxito < 95%
- Tiempo de respuesta > 30 segundos
- Rate limit alcanzado
- Costos superan el presupuesto
- Errores consecutivos > 3

## 🛠️ Mantenimiento Preventivo

### Tareas Diarias
- Revisar logs de errores
- Verificar estado de APIs
- Monitorear uso de recursos
- Revisar métricas de performance

### Tareas Semanales
- Actualizar documentación
- Revisar costos de APIs
- Verificar backups
- Actualizar dependencias

### Tareas Mensuales
- Rotar credenciales
- Revisar permisos de APIs
- Actualizar workflows
- Optimizar performance

## 📞 Soporte Adicional

### Recursos Útiles
- [Documentación oficial de n8n](https://docs.n8n.io/)
- [Foro de la comunidad n8n](https://community.n8n.io/)
- [GitHub de n8n](https://github.com/n8n-io/n8n)

### Contacto de Soporte
- **Email**: soporte@thesynaptek.com
- **Website**: https://thesynaptek.com
- **Horario**: Lunes a Viernes, 9:00-18:00 GMT-5

### Información para Soporte
Cuando contactes soporte, incluye:
1. Descripción detallada del problema
2. Logs de error completos
3. Configuración del workflow
4. Pasos para reproducir el error
5. Información del entorno (n8n version, OS, etc.)

---

**Nota**: Esta guía se actualiza regularmente. Para la versión más reciente, consulta el repositorio de GitHub.

