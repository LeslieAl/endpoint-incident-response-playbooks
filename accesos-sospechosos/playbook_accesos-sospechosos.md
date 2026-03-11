# Playbook – Respuesta a Accesos Sospechosos en Endpoints

**SOC MSSP:** Clínica  
**SIEM:** Wazuh  

## 1. Escenario del incidente
**Tipo de incidente:** Acceso sospechoso o no autorizado en endpoints

**Descripción:**  
Este incidente ocurre cuando se detectan comportamientos anómalos en el uso de credenciales o accesos a sistemas clínicos o administrativos. Su detección temprana es crítica para prevenir el compromiso de cuentas y la exposición de información sensible.

**Indicadores:**

- Intentos repetidos de inicio de sesión fallidos (posible fuerza bruta).
- Accesos desde ubicaciones geográficas inusuales.  
- Uso de credenciales fuera del horario laboral.  
- Cambios de privilegios sin autorización.
- Actividad anómala posterior al inicio de sesión.  

> Este tipo de incidentes puede indicar compromiso de credenciales o accesos no autorizados dentro de los sistemas de la clínica.

---

## 2. Mapeo del incidente con MITRE ATT&CK
Las técnicas más relevantes para este incidente son:

- **T1110 – Brute Force**  
  Repetidos intentos de autenticación para obtener acceso a cuentas válidas.  

- **T1078 – Valid Accounts**  
  Uso de credenciales legítimas comprometidas para acceder sin alertas inmediatas.  

- **T1098 – Account Manipulation**  
  Modificación de privilegios o configuraciones de cuentas para mantener acceso persistente.  

---

## 3. Detección

**Indicadores de Compromiso (IoCs):**

- Múltiples intentos fallidos de inicio de sesión.  
- Inicio de sesión exitoso tras varios intentos fallidos.  
- Accesos desde IP o ubicaciones geográficas inusuales.  
- Cambios inesperados de permisos o roles.  
- Ejecución de procesos inmediatamente después del acceso.  

**Herramientas utilizadas:**

- EDR (Endpoint Detection and Response)  
- SIEM gestionado por SOC MSSP (Wazuh)  
- Logs de autenticación del sistema operativo  
- Sistemas de gestión de identidades (Active Directory / IAM)  
- Antivirus y firewall de endpoints  

> Estas herramientas permiten identificar patrones sospechosos y generar alertas automáticas.

---

## 4. Procedimiento de respuesta

**SOC L1 – Monitoreo inicial**

- Revisar alertas generadas por el SIEM relacionadas con intentos de acceso sospechosos.  
- Validar logs de autenticación para identificar patrones anómalos de inicio de sesión.  
- Determinar la IP, ubicación geográfica y horario del acceso sospechoso.  
- Escalar incidentes confirmados o de alto riesgo al SOC L2 para análisis profundo.

**Resultados esperados:**  
Detección temprana de accesos anómalos y clasificación de incidentes relevantes para su análisis y contención.

---

**SOC L2 – Análisis técnico y contención**

- Analizar los accesos exitosos detectados por L1.  
- Revisar actividad posterior al inicio de sesión para identificar posibles compromisos.  
- Correlacionar eventos en el SIEM y en los logs de autenticación para determinar el alcance del incidente.  
- Recomendar acciones de contención específicas según la gravedad del acceso sospechoso.

**Resultados esperados:**  
Confirmación de incidentes reales, evaluación del riesgo y planificación de acciones para contener el compromiso de cuentas.

---

## Respuesta ante accesos sospechosos

**Acciones:**

- **Bloquear cuenta o IP sospechosa:** SOC MSSP ejecuta el bloqueo temporal desde sus herramientas.  
- **Forzar cambio de credenciales:** SOC MSSP coordina que el usuario afectado actualice su contraseña mediante el sistema IAM.  
- **Preservar evidencia digital:** SOC MSSP registra logs y eventos en SIEM (Wazuh) y EDR para auditoría.  
- **Coordinar con TI interna:** SOC MSSP notifica al equipo de TI para estar preparados ante medidas adicionales.  

**Resultados esperados:**  
- Contener el acceso no autorizado.  
- Minimizar riesgos de compromiso de cuentas.  
- Mantener evidencia para seguimiento y auditoría.


> **Nota:** En este tipo de incidente, el SOC Lead y los Especialistas de Redes o Endpoint Security no ejecutan acciones directas; su rol se limita a supervisión general y soporte en infraestructura solo en escenarios de incidentes complejos o escalados.

---

## 5. Impacto potencial

- Compromiso de cuentas de usuario.  
- Acceso no autorizado a información clínica.  
- Escalada de privilegios dentro del sistema.  
- Riesgos regulatorios y legales relacionados con la protección de datos.

---

## 6. Erradicación y recuperación

- Revocar sesiones activas sospechosas.  
- Restablecer credenciales comprometidas.  
- Revisar configuraciones de acceso y privilegios.  
- Validar integridad del endpoint afectado.  
- Reincorporar el endpoint a la red tras validación completa.

---

## 7. Notificación

**Interna:** SOC MSSP, Equipo de TI, Gerencia, Responsable del área afectada.  
**Externa (si aplica)**: Autoridades regulatorias si hay exposición de datos sensibles (Ley 8968 / HIPAA).
> Canales: llamadas telefónicas, intranet corporativa, mensajes seguros y encuentros en sala de mando según criticidad.

---

## 8. Lecciones aprendidas

- Documentar la cronología del incidente.  
- Identificar fallas en controles de acceso.  
- Actualizar reglas de detección en SIEM y EDR.  
- Reforzar políticas de contraseñas y autenticación multifactor.  
- Capacitar al personal en buenas prácticas de seguridad.

---

> **Nota:** Este playbook es un documento que actualizarse periódicamente ante nuevos tipos de incidentes o cambios en la infraestructura tecnológica de la clínica.
