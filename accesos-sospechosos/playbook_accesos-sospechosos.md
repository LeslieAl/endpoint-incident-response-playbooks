# Playbook de Respuesta a Accesos Sospechosos en Endpoints
SOC MSSP: Clínica - SIEM: Wazuh
---

# 1. Escenario del incidente
## Tipo de incidente
Acceso sospechoso o no autorizado en endpoints.

## Descripción del incidente

Este incidente se presenta cuando se detectan comportamientos anómalos relacionados con el uso de credenciales o accesos a sistemas clínicos o administrativos.

Ejemplos de comportamiento sospechoso:

- Intentos repetidos de inicio de sesión fallidos.
- Accesos desde ubicaciones geográficas inusuales.
- Uso de credenciales fuera del horario laboral.
- Cambios de privilegios sin autorización.
- Actividad anómala posterior al inicio de sesión.

Este tipo de incidente puede indicar compromiso de credenciales o acceso no autorizado a los sistemas de la clínica.


# 2. Mapeo del incidente con MITRE ATT&CK

El incidente se relaciona con tácticas y técnicas del framework MITRE ATT&CK que describen comportamientos utilizados por atacantes para comprometer credenciales o utilizar cuentas legítimas.


## Táctica: Credential Access

**Técnica:** Brute Force  
**ID:** T1110

### Descripción

El atacante intenta múltiples combinaciones de usuario y contraseña con el objetivo de obtener acceso a cuentas válidas dentro del sistema.

### Indicadores asociados

- Múltiples intentos fallidos de inicio de sesión.
- Inicio de sesión exitoso después de varios intentos fallidos.
- Intentos repetidos desde la misma dirección IP.

### Mitigación dentro del playbook

- Generar alerta automática desde el SIEM.
- Bloquear temporalmente la cuenta sospechosa.
- Forzar cambio de credenciales del usuario afectado.
- Analizar logs de autenticación.

## Táctica: Initial Access

**Técnica:** Valid Accounts  
**ID:** T1078

### Descripción

El atacante utiliza credenciales legítimas comprometidas para acceder al sistema sin generar alertas inmediatas.

### Indicadores asociados

- Accesos desde direcciones IP desconocidas.
- Inicio de sesión fuera del horario laboral habitual.
- Accesos desde ubicaciones geográficas inusuales.

### Mitigación dentro del playbook

- Revocar sesiones activas sospechosas.
- Bloquear temporalmente la cuenta comprometida.
- Verificar el origen del acceso.
- Analizar las acciones realizadas después del inicio de sesión.

## Táctica: Persistence

**Técnica:** Account Manipulation  
**ID:** T1098

### Descripción

El atacante modifica privilegios o configuraciones de cuentas con el objetivo de mantener acceso persistente dentro del sistema.

### Indicadores asociados

- Cambios inesperados de permisos o roles.
- Modificación de privilegios administrativos.

### Mitigación dentro del playbook

- Revisar configuraciones de acceso del usuario.
- Restaurar privilegios correctos.
- Auditar cambios realizados en cuentas.
- Validar la integridad del endpoint afectado.

# 3. Impacto potencial

Si este incidente no se controla de manera oportuna, puede generar:

- Compromiso de cuentas de usuario.
- Acceso no autorizado a información clínica.
- Escalada de privilegios dentro del sistema.
- Riesgos regulatorios y legales relacionados con la protección de datos.

# 4. Detección

## Herramientas utilizadas

- EDR (Endpoint Detection and Response)
- SIEM gestionado por el SOC MSSP mediante Wazuh
- Logs de autenticación del sistema operativo
- Sistemas de gestión de identidades (Active Directory / IAM)
- Antivirus y firewall de endpoints

## Indicadores de Compromiso (IoCs)

- Múltiples intentos fallidos de inicio de sesión.
- Inicio de sesión exitoso tras varios fallos.
- Accesos desde direcciones IP desconocidas.
- Accesos desde ubicaciones geográficas inusuales.
- Inicio de sesión fuera del horario habitual del usuario.
- Cambios inesperados de permisos o roles.
- Ejecución de procesos inmediatamente después del acceso.

# 5. Clasificación del incidente

| Criterio | Valor |
|--------|--------|
| Severidad | Media / Alta |
| Sistemas afectados | Endpoints de usuarios clínicos y administrativos |
| Nivel de exposición | Interno (riesgo de escalamiento y propagación) |

# 6. Estructura del Equipo SOC y Responsabilidades

El SOC MSSP encargado del monitoreo de seguridad de la clínica está conformado por distintos roles especializados.  
Cada miembro del equipo cumple funciones específicas dentro del proceso de monitoreo, detección, análisis y respuesta ante incidentes de seguridad.

## SOC Lead / Project Manager

Responsable de la coordinación general del SOC y de la supervisión del proyecto de seguridad.

**Funciones**

- Diseñar la arquitectura general del SOC.
- Coordinar las actividades del equipo de seguridad.
- Definir procesos de monitoreo, gestión de incidentes y respuesta ante incidentes.
- Supervisar entregables y garantizar la alineación con buenas prácticas de ciberseguridad.
- Elaborar reportes ejecutivos sobre el estado de la seguridad.

**Alcances**

- Arquitectura de red segura.
- Gestión de incidentes.
- Reportes ejecutivos.
- Coordinación del equipo SOC.

**Comunicación**

- Mantiene comunicación directa con la supervisora del proyecto.

## Analista SOC Nivel 1 (L1)

Responsable del monitoreo continuo de eventos de seguridad y de la detección inicial de amenazas.

**Funciones**

- Monitorear alertas de seguridad en tiempo real mediante dashboards del SIEM.
- Revisar eventos generados por Wazuh.
- Realizar la clasificación inicial de eventos de seguridad.
- Escalar incidentes relevantes al Analista SOC Nivel 2.
- Documentar hallazgos básicos y mantener bitácoras de incidentes.

**Alcances**

- Monitoreo y detección de amenazas.
- Gestión inicial de incidentes.
- Registro de eventos de seguridad.

## Analista SOC Nivel 2 (L2)

Responsable del análisis técnico de incidentes escalados y la coordinación de las acciones de respuesta.

**Funciones**

- Investigar incidentes escalados por el Analista SOC Nivel 1.
- Analizar logs y correlacionar eventos dentro del SIEM.
- Identificar la causa del incidente.
- Proponer medidas de contención y remediación.
- Generar reportes técnicos del incidente.

**Alcances**

- Gestión de incidentes.
- Análisis avanzado de seguridad.
- Reportes técnicos de incidentes.

## Especialista en Redes

Responsable de la arquitectura de red segura y del control del tráfico de red.

**Funciones**

- Diseñar la arquitectura de red segura para el SOC.
- Configurar segmentación de red.
- Implementar controles de seguridad perimetral.
- Apoyar en la integración de herramientas de monitoreo.

**Alcances**

- Arquitectura de red segura.
- Segmentación de red.
- Seguridad perimetral.

## Especialista en Endpoint Security

Responsable de la protección de dispositivos y servidores dentro de la infraestructura.

**Funciones**

- Definir políticas de protección para endpoints.
- Implementar soluciones de antivirus y EDR.
- Gestionar parches de seguridad.
- Monitorear vulnerabilidades en dispositivos.

**Alcances**

- Endpoint Security.
- Detección de amenazas en endpoints.
- Gestión de vulnerabilidades.

## Documentación y Reporting

Responsable de la documentación técnica y la generación de reportes del SOC.

**Funciones**

- Elaborar documentación técnica del SOC.
- Crear diagramas de arquitectura y flujos operativos.
- Generar reportes de incidentes y métricas de seguridad.
- Mantener actualizada la documentación del proyecto.

**Alcances**

- Reportes técnicos.
- Reportes ejecutivos.
- Documentación de arquitectura.

# 7. Respuesta inicial

Cuando se detecta el incidente:

- Generar alerta automática desde el SIEM o EDR.
- Aislar el endpoint afectado si existe actividad maliciosa.
- Bloquear temporalmente la cuenta sospechosa.
- Forzar cambio de credenciales del usuario afectado.
- Preservar evidencia digital (logs y eventos).
- Notificar al equipo de TI.

# 8. Análisis y contención

Durante esta fase se analiza el incidente y se evita su propagación.

Acciones principales:

- Analizar logs de autenticación.
- Verificar el origen del acceso (IP, ubicación y horario).
- Confirmar si el acceso corresponde a actividad legítima o no autorizada.
- Revisar actividades posteriores al inicio de sesión.
- Contener el incidente evitando nuevos accesos.

# 9. Erradicación y recuperación

Acciones:

- Revocar sesiones activas sospechosas.
- Restablecer credenciales comprometidas.
- Revisar configuraciones de acceso y privilegios.
- Validar integridad del endpoint afectado.
- Reincorporar el endpoint a la red tras validación completa.

# 10. Notificación

## Interna

El incidente debe notificarse a:

- SOC MSSP
- Equipo de TI
- Gerencia
- Responsable del área afectada

## Externa (si aplica)

Si existe exposición de datos sensibles, se debe evaluar la notificación a autoridades regulatorias conforme a la normativa de protección de datos.

# 11. Cumplimiento regulatorio

Este playbook considera normativas relacionadas con la protección de datos personales y datos médicos.

## Ley 8968 – Costa Rica

La clínica debe garantizar:

- Protección de la confidencialidad de los datos personales.
- Control de accesos a información sensible.
- Registro de incidentes de seguridad relacionados con datos personales.

## HIPAA

En el contexto de datos médicos se deben aplicar principios como:

- Protección de la información médica protegida (PHI).
- Control de accesos a sistemas clínicos.
- Registro de accesos y auditoría de actividades.


# 12. Lecciones aprendidas

Una vez finalizado el incidente se deben ejecutar las siguientes acciones:

- Documentar la cronología del incidente.
- Identificar fallas en controles de acceso.
- Actualizar reglas de detección en el SIEM.
- Reforzar políticas de contraseñas y autenticación multifactor.
- Capacitar al personal en buenas prácticas de seguridad.

# Nota
Este playbook es un documento sometido a revisión y debe actualizarse periódicamente para adaptarse a nuevos tipos de amenazas o cambios en la infraestructura tecnológica de la Clinica. 

---
