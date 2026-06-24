# ORGANIZADOR DE EXPEDIENTES JURÍDICOS

**Automatización en Google Drive para organizar expedientes legales por materia, caso y etapa procesal**

---

## 📋 ¿Qué hace?

Este script de Google Apps Script mueve **automáticamente** tus archivos de expedientes desde una carpeta desordenada hacia sus carpetas finales clasificadas por:

✅ **Tipo de materia jurídica** (Amparo, Penal, Familiar, Administrativo, etc.)  
✅ **Etapa procesal** (Demanda, Contestación, Apelación, etc.)  
✅ **Caso específico** (Cliente, número de expediente)  

**Ventajas:**
- Cero clics manuales — El script mueve todos los archivos de una vez
- Verificación de errores — Te muestra qué se movió y qué falló
- Recuperación de archivos — Si un archivo no existe, registra el error sin detener la ejecución

---

## 🚀 Instalación Rápida (3 minutos)

### Paso 1: Abre Google Apps Script

```
https://script.google.com
```

### Paso 2: Copia TODO el código

```
- Abre el archivo organizarExpedientes.gs
- Selecciona TODO el contenido (Ctrl+A)
- Cópialo (Ctrl+C)
```

### Paso 3: Pégalo en Apps Script

```
- En https://script.google.com
- Borra el contenido por defecto
- Pega TODO el código
- Guarda (Ctrl+S)
```

### Paso 4: Ejecuta

```
- Haz clic en ▶ (Ejecutar)
- Selecciona la función: organizarExpedientes
- La primera vez pedirá autorización → Acepta
- Espera a que termine (verás checkmarks ✓ en los registros)
```

### Paso 5: Revisa los resultados

```
- Ve a Ver → Registros
- Verás qué archivos se movieron (✓) y cuáles tuvieron error (✗)
```

---

## 🔧 Personalización

### 1. Agregar Más Carpetas

En la sección `var CARPETAS = { ... }`, añade nuevas líneas:

```javascript
"NOMBRE_CARPETA": "ID_DE_CARPETA",
```

**Cómo obtener el ID de una carpeta:**
- Abre la carpeta en Google Drive
- Copia la URL:
  ```
  https://drive.google.com/drive/folders/1ABC123XYZ...
                                         ^^^^^^^^^^^^
                                      Este es el ID
  ```

### 2. Agregar Más Archivos

En la sección `var ARCHIVOS = [ ... ]`, añade nuevas líneas:

```javascript
["ID_DEL_ARCHIVO", "NOMBRE_CARPETA_DESTINO"],
```

**Cómo obtener el ID de un archivo:**
- Haz clic derecho en el archivo → Obtener enlace
- Copia la URL:
  ```
  https://drive.google.com/file/d/1XYZ456ABC...
                               ^^^^^^^^^^
                            Este es el ID
  ```

---

## 📊 Estructura de Carpetas (Predefinida)

```
EXPEDIENTES_JURÍDICOS/
├── AMPARO INDIRECTO          (Amparos contra actos de autoridad)
├── AMPARO DIRECTO            (Amparos contra sentencias)
├── PENAL                     (Asuntos penales ante juez de control)
├── FISCALIA                  (Escritos ante Fiscalía)
├── FAMILIAR ORAL             (Juicios de alimentos, custodia, etc.)
├── FAMILIAR                  (Asuntos familiares contenciosos)
├── ADMINISTRATIVO            (Demandas contra autoridades administrativas)
├── CONTRATOS Y HONORARIOS    (Documentos de servicios profesionales)
└── OTROS                     (Documentos no clasificados)
```

Puedes modificar esta estructura editando la sección `CARPETAS` en el código.

---

## ⚙️ Cómo Funciona Internamente

```
1. Define dos listas:
   - CARPETAS: Mapeo de nombres a IDs de carpeta
   - ARCHIVOS: Pares [fileId, nombreCarpeta destino]

2. Para cada archivo:
   - Obtiene el ID del archivo
   - Busca la carpeta destino en CARPETAS
   - Mueve el archivo usando archivo.moveTo(destino)
   - Registra ✓ o ✗ según resultado
   - Pausa 200ms para evitar saturar la API de Google

3. Al final:
   - Muestra resumen: Archivos movidos + Errores
   - Lista completa en Ver → Registros
```

---

## 🚨 Solución de Problemas

### Error: "File not found"

**Causa:** El ID del archivo no existe o fue eliminado.  
**Solución:** Verifica que el archivo siga en tu Drive y actualiza el ID.

### Error: "Folder not found"

**Causa:** El ID de la carpeta destino no existe o fue eliminado.  
**Solución:** Verifica que la carpeta siga en tu Drive y actualiza el ID.

### Error: "Permission denied"

**Causa:** Google Apps Script no tiene permisos de acceso a Drive.  
**Solución:** Ejecuta de nuevo y autoriza los permisos en la ventana emergente.

### El script se ejecuta pero no mueve archivos

**Causa:** Los IDs en ARCHIVOS no coinciden con los archivos reales.  
**Solución:** Copia directamente los IDs de los archivos desde sus URLs en Drive.

---

## 📝 Ejemplo de Uso Real

Tienes 50 archivos en tu carpeta "Descargas" de expedientes del caso **Chuy 215/2026**:

```
Descargas/
├── PREVENCION.docx
├── Demanda de Amparo.pdf
├── Notificación.pdf
├── Respuesta.docx
└── ... (46 archivos más)
```

**Antes:** Tiendes que mover cada uno manualmente.  
**Después:** El script los mueve automáticamente a:

```
EXPEDIENTES/
└── AMPARO INDIRECTO/
    ├── PREVENCION.docx
    ├── Demanda de Amparo.pdf
    ├── Notificación.pdf
    ├── Respuesta.docx
    └── ... (46 archivos más)
```

**Tiempo ahorrado:** ~30–40 minutos de trabajo manual.

---

## 🔐 Privacidad y Seguridad

- El script **no sube tus archivos a servidores externos**
- Funciona completamente dentro de tu Google Drive
- Requiere autorización explícita la primera vez
- Puedes revocar permisos en cualquier momento: Configuración de Google → Aplicaciones conectadas

---

## 📚 Integración con ARCHITECT-LITIGATOR-PRO MX-NL

Este organizador complementa perfectamente el manual de redacción jurídica:

1. **Organizas tus expedientes** con este script
2. **Redactas escritos** siguiendo ARCHITECT-LITIGATOR-PRO MX-NL
3. **Guardas los nuevos documentos** en las carpetas organizadas

**Flujo de trabajo integrado:**
```
Archivos desordenados
        ↓
Organiador (este script)
        ↓
Expedientes clasificados
        ↓
Redacción de escritos (ARCHITECT-LITIGATOR-PRO)
        ↓
Documentos finales guardados en lugar correcto
```

---

## 📞 Soporte

Si el script no funciona:

1. ✅ Verifica que los IDs sean correctos
2. ✅ Autoriza los permisos de Apps Script
3. ✅ Revisa Ver → Registros para mensajes de error específicos
4. ✅ Prueba con un solo archivo primero (reduce ARCHIVOS a 1 línea)

---

**Versión:** 1.0  
**Última actualización:** 24 de junio de 2026  
**Autor:** Edgar Jair Mireles González  
**Cédula Profesional:** [Tu número]  
