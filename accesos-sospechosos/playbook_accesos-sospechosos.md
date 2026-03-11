# Playbook de Respuesta a Accesos Sospechosos en Endpoints
SOC MSSP – Clínica  
SIEM: Wazuh

---

## Escenario o tipo de incidente

**Tipo:**  
Acceso sospechoso o no autorizado en endpoints.

**Descripción del incidente**

- Intentos de inicio de sesión fallidos repetitivos.
- Accesos desde ubicaciones geográficas inusuales.
- Uso de credenciales fuera del horario laboral.
- Cambios de privilegios sin autorización.
- Comportamiento anómalo posterior al inicio de sesión.

---

# Mapeo del incidente con MITRE ATT&CK

El incidente se relaciona con tácticas y técnicas del framework MITRE ATT&CK que describen comportamientos comunes utilizados por atacantes para comprometer credenciales o acceder a sistemas mediante cuentas legítimas.

---

## Táctica: Credential Access

**Técnica:** Brute Force  
**ID:** T1110  

### Descripción

El atacante intenta múltiples combinaciones de usuario y contraseña para obtener acceso a cuentas válidas dentro del sistema.

### Indicadores asociados

- Múltiples intentos fallidos de inicio de sesión.
- Inicio de sesión exitoso después de varios intentos fallidos.
- Intentos repetidos desde la misma dirección IP.

### Mitigación dentro del playbook

- Generar alerta automática desde el SIEM.
- Bloquear temporalmente la cuenta sospechosa.
- Forzar cambio de credenciales del usuario afectado.
- Analizar logs de autenticación.

---

## Táctica: Initial Access

**Técnica:** Valid Accounts  
**ID:** T1078  

### Descripción

El atacante utiliza credenciales legítimas comprometidas para acceder al sistema sin ser detectado inicialmente.

### Indicadores asociados

- Accesos desde direcciones IP desconocidas.
- Inicio de sesión fuera del horario laboral.
- Accesos desde ubicaciones geográficas inusuales.

### Mitigación dentro del playbook

- Revocar sesiones activas sospechosas.
- Bloquear temporalmente la cuenta comprometida.
- Verificar el origen del acceso.
- Analizar las acciones realizadas después del inicio de sesión.

---

## Táctica: Persistence

**Técnica:** Account Manipulation  
**ID:** T1098  

### Descripción

El atacante modifica privilegios o configuraciones de cuentas para mantener acceso persistente dentro del sistema.

### Indicadores asociados

- Cambios inesperados de permisos o roles.
- Modificación de privilegios administrativos.

### Mitigación dentro del playbook

- Revisar configuraciones de acceso del usuario.
- Restaurar privilegios correctos.
- Auditar cambios realizados en cuentas.
- Validar la integridad del endpoint afectado.

---

# Impacto potencial

- Compromiso de cuentas de usuario.
- Acceso no autorizado a información clínica.
- Escalada de privilegios.
- Riesgos regulatorios y legales.

---

# Detección

## Herramientas

- EDR (Endpoint Detection & Response)
- SIEM gestionado por SOC MSSP mediante Wazuh
- Logs de autenticación del sistema operativo
- Sistemas de gestión de identidades (Active Directory / IAM)
- Antivirus y firewall de endpoints

## Indicadores de Compromiso (IoCs)

- Múltiples intentos fallidos de inicio de sesión.
- Inicio de sesión exitoso tras varios fallos.
- Accesos desde direcciones IP o ubicaciones inusuales.
- Inicio de sesión fuera del horario habitual del usuario.
- Cambios inesperados de permisos o roles.
- Ejecución de procesos inmediatamente después del acceso.

---

# Clasificación del Incidente

| Criterio | Valor |
|---|---|
| Severidad | Media / Alta |
| Sistemas afectados | Endpoints de usuarios clínicos y administrativos |
| Nivel de exposición | Interna (riesgo de escalamiento y propagación) |

---

# Respuesta Inicial

- Generar alerta automática desde EDR o SIEM.
- Aislar el endpoint afectado si se detecta actividad anómala activa.
- Bloquear temporalmente la cuenta sospechosa.
- Forzar cambio de credenciales del usuario afectado.
- Preservar evidencia (logs de autenticación, eventos de sistema).
- Notificar al SOC MSSP para coordinación de respuesta.

---

# Análisis y Contención

- Analizar logs de autenticación y eventos de seguridad.
- Verificar origen del acceso (IP, ubicación, horario).
- Confirmar si el acceso corresponde a actividad legítima o no autorizada.
- Revisar acciones realizadas después del acceso.
- Contener el incidente evitando accesos adicionales.
- Informar al equipo interno de TI sobre el estado del incidente.

---

# Erradicación y Recuperación

- Revocar sesiones activas sospechosas.
- Restablecer credenciales y reforzar políticas de autenticación.
- Revisar configuraciones de acceso y privilegios del usuario.
- Validar integridad del endpoint afectado.
- Reincorporar el endpoint a la red solo tras validación completa.

---

# Notificación

## Interna

- SOC MSSP
- Equipo de TI
- Gerencia
- Responsable del área afectada

## Externa (si aplica)

- Autoridades regulatorias o responsables de cumplimiento según normativa de protección de datos.

---

# Lecciones Aprendidas

- Documentar cronología del incidente y acciones realizadas.
- Identificar fallas en controles de acceso.
- Actualizar reglas de detección en SIEM y EDR.
- Reforzar políticas de contraseñas y autenticación multifactor.
- Capacitar al personal sobre buenas prácticas de acceso seguro.

---

# Cómo detectar y responder a los eventos

## Detección

- Correlación de eventos de autenticación en el SIEM.
- Alertas del EDR por comportamiento anómalo.
- Monitoreo de patrones de acceso fuera de lo normal.

## Respuesta

- Aislamiento del endpoint.
- Bloqueo inmediato de credenciales.
- Análisis forense básico.
- Recuperación segura del sistema.
- Documentación completa del evento.

---

**Nota:**  
Este playbook es un documento vivo y debe actualizarse ante nuevos tipos de incidentes o cambios en la infraestructura.
