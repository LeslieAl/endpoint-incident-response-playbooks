# Playbook – Respuesta a Incidentes de Ransomware
**SOC MSSP:** Clínica  
**SIEM:** Wazuh

## 1. Escenario del incidente
**Tipo de incidente:** Ransomware dirigido a endpoints y servidores internos

**Descripción:**  
Ataque que cifra archivos críticos en PCs, laptops y servidores internos.  
Se observa un nivel de seguridad bajo, personal poco capacitado y dispositivos médicos conectados sin control.  
Impacto: interrupción de atención a pacientes, pérdida de datos sensibles y riesgos legales.

**Indicadores:**
- Archivos cifrados con extensiones desconocidas.
- Mensajes de rescate en pantalla.
- Procesos sospechosos ejecutándose en endpoints.
- Conexiones a IPs o dominios maliciosos.
- Actividad anómala en servidores internos o dispositivos médicos conectados.


## 2. Mapeo del incidente con MITRE ATT&CK
Técnicas relevantes para ransomware:

- **T1486 – Data Encrypted for Impact**  
  Cifrado de archivos críticos para interrumpir operaciones.  

- **T1490 – Inhibit System Recovery**  
  Eliminación de backups o puntos de restauración para evitar recuperación.  

- **T1078 – Valid Accounts**  
  Uso de credenciales legítimas para propagarse o mantener acceso.


## 3. Detección
**Indicadores de Compromiso (IoCs):**
- Archivos cifrados con extensiones desconocidas.
- Mensajes de rescate visibles en los endpoints.
- Procesos sospechosos en ejecución.
- Conexiones a IPs o dominios maliciosos.
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
- Validar logs de EDR y sistemas para identificar actividad anómala.  
- Escalar incidentes confirmados al SOC L2 para análisis profundo.

**Resultados esperados:**  
Detección temprana de ransomware y clasificación del incidente para su contención.


**SOC L2 – Análisis técnico y contención**
- Analizar endpoints y servidores afectados.  
- Determinar vector de ataque y cronología del incidente.  
- Contener sistemas comprometidos en cuarentena.  
- Validar que no haya propagación a otros dispositivos o backups.  

**Resultados esperados:**  
Confirmación de incidentes, evaluación del riesgo y planificación de contención.


## 5. Respuesta ante ransomware
**Acciones:**
- **Aislamiento de endpoints y servidores comprometidos:** SOC MSSP ejecuta cuarentena remota.  
- **Bloqueo de IPs y dominios maliciosos:** SOC MSSP bloquea acceso desde herramientas de gestión.  
- **Preservación de evidencia digital:** SOC MSSP registra logs y eventos críticos en SIEM (Wazuh) y EDR para auditoría.  
- **Coordinación con TI interna:** SOC MSSP notifica al equipo interno de TI para apoyo y seguimiento.  

**Resultados esperados:**  
- Contener propagación del ransomware.  
- Minimizar impacto en operaciones clínicas.  
- Mantener evidencia para seguimiento y auditoría.  

> **Nota:** SOC Lead y Especialistas de Redes o Endpoint Security solo supervisan; no ejecutan acciones directas salvo incidentes complejos o escalados.


## 6. Erradicación y Recuperación
- Eliminar malware y cerrar posibles backdoors.  
- Restaurar datos desde backups verificados.  
- Aplicar parches y reforzar configuraciones de seguridad.  
- Validar integridad de sistemas clínicos y dispositivos conectados.  
- Revisión final antes de reconectar dispositivos a la red.


## 7. Notificación
**Interna:** SOC MSSP, gerencia, médicos responsables, RRHH.  
**Externa (si aplica):** Autoridades sanitarias y pacientes afectados según normativa de privacidad.
> Canales:  llamadas telefónicas, intranet corporativa, mensajes seguros y encuentros en sala de mando según criticidad.


## 8. Lecciones Aprendidas
- Documentar cronología completa del incidente.  
- Identificar fallas en controles de seguridad.  
- Actualizar reglas de detección en SIEM y EDR.  
- Reforzar políticas de contraseñas, backups y autenticación multifactor.  
- Capacitar al personal en ciberseguridad y manejo de ransomware.


> **Nota:** Este playbook es un documento que debe actualizarse ante nuevos ataques de ransomware o cambios en la infraestructura tecnológica de la clínica.
