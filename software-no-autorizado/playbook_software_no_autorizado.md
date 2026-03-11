# Playbook – Respuesta a Ejecución de Software No Autorizado
**SOC MSSP:** Clínica  
**SIEM:** Wazuh

## 1. Escenario del incidente
**Tipo de incidente:** Ejecución de software no autorizado en endpoints o servidores internos.

**Descripción:**  
Este incidente ocurre cuando se detecta software que no está registrado ni autorizado ejecutándose en los sistemas de la clínica. Su detección temprana es fundamental para evitar pérdida de datos, propagación de malware y afectación de la atención clínica.

**Indicadores:**
- Software no autorizado ejecutándose en endpoints o servidores.  
- Conexiones externas sospechosas generadas por el software.  
- Modificaciones no autorizadas en archivos críticos.  
- Alertas de comportamiento anómalo detectadas por EDR o antivirus.  

> Este tipo de incidentes puede indicar riesgo de malware, fuga de información o brechas de seguridad por uso de software no controlado.

---

## 2. Mapeo del incidente con MITRE ATT&CK
Las técnicas más relevantes para este incidente son:

- **T1036 – Masquerading**: Software disfrazado o con nombres falsos para evitar detección.  
- **T1071 – Application Layer Protocol**: Comunicación maliciosa a través de protocolos comunes de aplicación.  
- **T1083 – File and Directory Discovery**: Exploración de archivos o directorios que puede indicar actividad sospechosa del software.  

---

## 3. Detección
**Indicadores de Compromiso (IoCs):**  
- Ejecución de software no registrado o no autorizado.  
- Conexiones externas sospechosas hacia IPs o dominios desconocidos.  
- Modificaciones inesperadas en archivos críticos del sistema.  
- Alertas de comportamiento anómalo en EDR o antivirus.  

**Herramientas utilizadas:**  
- EDR (Endpoint Detection & Response)  
- SIEM gestionado por SOC MSSP (Wazuh)  
- Logs de autenticación y eventos del sistema operativo  
- Antivirus y firewall de endpoints  
- Monitoreo de servidores y dispositivos médicos  

> Estas herramientas permiten detectar la ejecución de software no autorizado y generar alertas automáticas para análisis.

---

## 4. Procedimiento de respuesta
**SOC L1 – Monitoreo inicial**
- Revisar alertas generadas por SIEM y EDR sobre ejecución de software no autorizado.  
- Validar logs de endpoints y servidores para identificar comportamiento anómalo.  
- Determinar origen del software, IP y usuario asociado.  
- Escalar incidentes confirmados o de alto riesgo al SOC L2 para análisis profundo.

**Resultados esperados:**  
Detección temprana de software no autorizado y clasificación del incidente para su contención.

---

**SOC L2 – Análisis técnico y contención**
- Analizar los sistemas afectados identificados por L1.  
- Revisar actividad del software ejecutado para evaluar riesgos y posible compromiso.  
- Correlacionar eventos en SIEM y logs de sistemas para determinar alcance.  
- Recomendar acciones de contención según criticidad del incidente.

**Resultados esperados:**  
Confirmación de incidentes reales, evaluación de riesgo y planificación de acciones para contener el software no autorizado.

---

## 5. Respuesta ante ejecución de software no autorizado
**Acciones:**
- **Aislamiento del sistema afectado:** SOC MSSP ejecuta cuarentena remota del endpoint o servidor comprometido.  
- **Bloqueo del software:** SOC MSSP detiene o bloquea la ejecución del software desde herramientas de gestión.  
- **Preservación de evidencia digital:** SOC MSSP registra logs y eventos críticos en SIEM (Wazuh) y EDR para auditoría.  
- **Coordinación con TI interna:** SOC MSSP notifica al equipo de TI para apoyo y seguimiento.  

**Resultados esperados:**  
- Contención efectiva del software no autorizado.  
- Minimización de riesgos de malware o pérdida de datos.  
- Mantener evidencia para seguimiento y auditoría.

> **Nota:** SOC Lead y Especialistas de Redes o Endpoint Security no ejecutan acciones directas; su rol es supervisión y soporte solo en escenarios complejos o escalados.

---

## 6. Impacto potencial
- Riesgo de malware y ejecución de código no autorizado.  
- Interrupción de servicios clínicos.  
- Posible exposición de datos de pacientes.  
- Vulnerabilidad ante brechas regulatorias.

---

## 7. Erradicación y recuperación
- Desinstalar software no autorizado y cerrar posibles backdoors.  
- Restaurar configuraciones seguras y aplicar parches.  
- Validar integridad de endpoints, servidores y dispositivos conectados.  
- Reincorporar sistemas a la red solo tras validación completa.

---

## 8. Notificación
**Interna:** SOC MSSP, personal afectado, TI, gerencia.  
**Externa:** Socios tecnológicos o proveedores según corresponda.

**Canales:** llamadas telefónicas, intranet corporativa, mensajes seguros y reuniones en sala de mando según criticidad.

---

## 9. Lecciones Aprendidas
- Documentar cronología, sistemas afectados, impacto y acciones ejecutadas.  
- Reunión post-mortem con SOC MSSP y personal interno.  
- Actualizar playbook y políticas internas según hallazgos.  
- Capacitar al personal en ejecución segura de software autorizado.

> **Nota:** Este playbook es un documento vivo que debe actualizarse periódicamente ante nuevos incidentes o cambios en la infraestructura tecnológica de la clínica.
