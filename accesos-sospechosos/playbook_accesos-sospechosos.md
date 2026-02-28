# Playbook de Respuesta a Accesos Sospechosos en Endpoints

## Escenario o tipo de incidente
**Tipo:** Acceso sospechoso o no autorizado en endpoints.  
**Descripción del incidente:**
- Intentos de inicio de sesión fallidos repetitivos.
- Accesos desde ubicaciones geográficas inusuales.
- Uso de credenciales fuera del horario laboral.
- Cambios de privilegios sin autorización.
- Comportamiento anómalo posterior al inicio de sesión.

**Impacto potencial:**
- Compromiso de cuentas de usuario.
- Acceso no autorizado a información clínica.
- Escalada de privilegios.
- Riesgos regulatorios y legales.

## Detección
**Herramientas:**
- EDR (Endpoint Detection & Response)
- SIEM gestionado por SOC MSSP
- Logs de autenticación del sistema operativo
- Sistemas de gestión de identidades (Active Directory / IAM)
- Antivirus y firewall de endpoints

**Indicadores de compromiso (IoCs):**
- Múltiples intentos fallidos de inicio de sesión.
- Inicio de sesión exitoso tras varios fallos.
- Accesos desde direcciones IP o ubicaciones inusuales.
- Inicio de sesión fuera del horario habitual del usuario.
- Cambios inesperados de permisos o roles.
- Ejecución de procesos inmediatamente después del acceso.

## Clasificación del Incidente

| Criterio             | Valor                                         |
|----------------------|-----------------------------------------------|
| Severidad            | Media / Alta                                  |
| Sistemas afectados   | Endpoints de usuarios clínicos y administrativos |
| Nivel de exposición  | Interna (riesgo de escalamiento y propagación) |

## Respuesta Inicial
1. Generar alerta automática desde EDR o SIEM.
2. Aislar el endpoint afectado si se detecta actividad anómala activa.
3. Bloquear temporalmente la cuenta sospechosa.
4. Forzar cambio de credenciales del usuario afectado.
5. Preservar evidencia (logs de autenticación, eventos de sistema).
6. Notificar al SOC MSSP para coordinación de respuesta.

## Análisis y Contención
1. Analizar logs de autenticación y eventos de seguridad.
2. Verificar origen del acceso (IP, ubicación, horario).
3. Confirmar si el acceso corresponde a actividad legítima o no autorizada.
4. Revisar acciones realizadas después del acceso.
5. Contener el incidente evitando accesos adicionales.
6. Informar al equipo interno de TI sobre el estado del incidente.

## Erradicación y Recuperación
1. Revocar sesiones activas sospechosas.
2. Restablecer credenciales y reforzar políticas de autenticación.
3. Revisar configuraciones de acceso y privilegios del usuario.
4. Validar integridad del endpoint afectado.
5. Reincorporar el endpoint a la red solo tras validación completa.

## Notificación
**Interna:** SOC MSSP, equipo de TI, gerencia, responsable del área afectada.  
**Externa (si aplica):** Autoridades regulatorias o responsables de cumplimiento, según normativa de protección de datos.

## Lecciones Aprendidas
1. Documentar cronología del incidente y acciones realizadas.
2. Identificar fallas en controles de acceso.
3. Actualizar reglas de detección en SIEM y EDR.
4. Reforzar políticas de contraseñas y autenticación multifactor.
5. Capacitar al personal sobre buenas prácticas de acceso seguro.

## Cómo detectar y responder a los eventos
**Detección:**
- Correlación de eventos de autenticación en el SIEM.
- Alertas del EDR por comportamiento anómalo.
- Monitoreo de patrones de acceso fuera de lo normal.

**Respuesta:**
- Aislamiento del endpoint.
- Bloqueo inmediato de credenciales.
- Análisis forense básico.
- Recuperación segura del sistema.
- Documentación completa del evento.

> **Nota:** Este playbook es un documento vivo. Debe actualizarse ante nuevos tipos de incidentes o cambios en la infraestructura.
