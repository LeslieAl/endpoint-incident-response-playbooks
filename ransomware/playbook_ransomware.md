# Playbook – Respuesta a Incidentes de Ransomware
**SOC MSSP:** Clínica  
**SIEM:** Wazuh

## 1. Escenario del incidente
**Tipo de incidente:** Ransomware dirigido a endpoints y servidores internos

**Descripción:**  
Ataque que simula el comportamiento de ransomware mediante la ejecución de procesos sospechosos que generan modificaciones masivas de archivos en el sistema. Este tipo de actividad puede provocar la indisponibilidad de información crítica, afectando la operación de los servicios de la clínica.

**Impacto:** interrupción de atención a pacientes, pérdida de datos sensibles y riesgos legales.

**Indicadores:**
- Modificación masiva de archivos en el sistema.
- Ejecución de procesos sospechosos.
- Conexiones a IPs o dominios maliciosos.
- Actividad anómala registrada en los logs del sistema.
- Actividad anómala en servidores internos o dispositivos médicos conectados.


## 2. Mapeo del incidente con MITRE ATT&CK
Técnicas relevantes para ransomware:

- **T1485 – Data Destruction**  
  Eliminación de archivos o datos del sistema para afectar la disponibilidad de la información. 

- **T1070.004 – Indicator Removal: File Deletion**  
  Eliminación de archivos con el objetivo de ocultar evidencias de la actividad maliciosa en el sistema.
- **T1565.001 – Data Manipulation: Stored Data Manipulation**  
  Modificación de archivos almacenados en el sistema, afectando la integridad de la información.


## 3. Detección
**Indicadores de Compromiso (IoCs):**
- Archivos cifrados con extensiones desconocidas.
- Eliminación de archivos.
- Procesos sospechosos en ejecución.
- Modificación de archivos.
- Actividad anómala en servidores internos o dispositivos médicos.

**Herramientas utilizadas:**
- EDR (Endpoint Detection and Response)  
- SIEM gestionado por SOC MSSP (Wazuh)  
- Antivirus y firewall de endpoints  
- Monitoreo de logs de servidores y dispositivos médicos  

> Estas herramientas permiten identificar y alertar sobre actividades de ransomware.


## 4. Procedimiento de respuesta

**SOC L1 – Monitoreo inicial**
- Revisar alertas generadas por el SIEM relacionadas con ransomware.  
- Validar logs del SIEM para identificar actividad anómala.
- Validar que las alertas NO sean falsos positivos.  
- Escalar incidentes confirmados al SOC L2 para análisis profundo.

**Resultados esperados:**  
Detección temprana de ransomware y clasificación del incidente para su contención.


**SOC L2 – Análisis técnico y contención**
- Analizar los eventos generados en el SIEM.
- Correlacionar alertar generadas.  
- Determinar vector de ataque y cronología del incidente.  
- Contener sistemas comprometidos en cuarentena.  
- Validar que no haya propagación a otros dispositivos o backups.  

**Resultados esperados:**  
Confirmación de incidentes, evaluación del riesgo y planificación de contención.


## 5. Respuesta ante ransomware
**Acciones:**
- **Aislamiento del sistema comprometido:** evitar la propagación del incidente a otros sistemas.
- **Detención del proceso sospechoso:** evitar que continúe modificando o eliminando archivos.
' **Bloqueo de conexiones sospechosas:** prevenir posibles accesos no autorizados.
- **Preservación de evidencia digital:** registrar eventos y logs generados por Wazuh para análisis posterior.
- **Coordinación con el equipo de TI:** comunicar el incidente y ejecutar acciones de mitigación.

**Resultados esperados:**  
- Contenención del incidente.  
- Minimizar impacto en operaciones clínicas.  
- Mantener evidencia para auditoría y análisis posterior.  

> **Nota:** SOC Lead y Especialistas de Redes o Endpoint Security solo supervisan; no ejecutan acciones directas salvo incidentes complejos o escalados.


## 6. Erradicación y Recuperación
- Eliminación de procesos maliciosos detectados en el sistema.
- Revisión del sistema para verificar que no existan actividades persistentes.
- Restauración de archivos afectados mediante copias de seguridad verificadas.
- Aplicación de actualizaciones y refuerzo de configuraciones de seguridad.
- Validación de la integridad del sistema antes de reconectarlo a la red.


## 7. Notificación
**Interna:** SOC MSSP, gerencia, médicos responsables, RRHH.  
**Externa (si aplica):** Autoridades sanitarias y pacientes afectados según normativa de privacidad.
> Canales:  llamadas telefónicas, intranet corporativa, mensajes seguros y encuentros en sala de mando según criticidad.


## 8. Lecciones Aprendidas
- Documentar cronología completa del incidente.  
- Identificar fallas en controles de seguridad.  
- Actualizar reglas de Wazuh.  
- Reforzar políticas de contraseñas, backups y autenticación multifactor.  
- Capacitar al personal en ciberseguridad y manejo de ransomware.


> **Nota:** Este playbook es un documento que debe actualizarse ante nuevos ataques de ransomware o cambios en la infraestructura tecnológica de la clínica.
