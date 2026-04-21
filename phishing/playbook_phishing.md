# Playbook – Respuesta a Incidentes de Phishing en Endpoints

**SOC MSSP:** Clínica  
**SIEM:** TryHackme 

---

## 1. Escenario del incidente

**Tipo de incidente:** Phishing con compromiso de credenciales

**Descripción:**  
Este incidente ocurre cuando un usuario es engañado mediante un correo electrónico malicioso, lo que puede provocar el robo de credenciales o la ejecución de software malicioso. El phishing puede ser el punto de entrada para ataques más avanzados.

**Indicadores:**
- Correos con enlaces o archivos sospechosos  
- Acceso a enlaces maliciosos  
- Descarga de archivos no autorizados  
- Inicio de sesión desde ubicaciones inusuales  
- Actividad anómala posterior al acceso  

---

## 2. Mapeo con MITRE ATT&CK

- **T1566 – Phishing**  
- **T1078 – Valid Accounts**  
- **T1021 – Remote Services**  

---

## 3. Detección

**Indicadores de Compromiso (IoCs):**
- Acceso a enlaces sospechosos desde el endpoint  
- Inicio de sesión tras interacción con correo  
- Conexiones RDP o SMB inusuales  
- Ejecución de scripts (PowerShell)  
- Acceso a recursos compartidos sensibles  

**Herramientas utilizadas:**
- EDR  
- SIEM (Wazuh)  
- Logs de autenticación  
- Antivirus y firewall de endpoints  

---

## 4. Procedimiento de respuesta

### SOC L1 – Monitoreo inicial
- Detectar alertas de phishing en el SIEM  
- Validar eventos sospechosos  
- Identificar usuario afectado y endpoint  
- Escalar a SOC L2  

**Resultados esperados:**  
Detección temprana del incidente  

---

### SOC L2 – Análisis técnico
- Correlacionar eventos de acceso y ejecución  
- Verificar uso de credenciales comprometidas  
- Identificar posible descarga de malware  
- Evaluar alcance del incidente  

**Resultados esperados:**  
Confirmación del incidente y evaluación del riesgo  

---

## 5. Respuesta ante phishing

**Acciones:**
- Bloquear cuenta comprometida  
- Forzar cambio de credenciales  
- Aislar endpoint afectado  
- Bloquear IP o dominio malicioso  
- Preservar evidencia en SIEM y EDR  

**Resultados esperados:**
- Contener el acceso no autorizado  
- Evitar propagación del ataque  
- Mantener evidencia para auditoría  

---

## 6. Impacto potencial

- Compromiso de cuentas de usuario  
- Acceso no autorizado a información  
- Movimiento lateral dentro de la red  
- Riesgos regulatorios y legales  

---

## 7. Erradicación y recuperación

- Eliminación de malware  
- Reinstalación del sistema si es necesario  
- Restablecimiento de credenciales  
- Validación de integridad del endpoint  
- Reincorporación segura a la red  

---

## 8. Notificación

- SOC MSSP  
- Equipo de TI  
- Gerencia  
- Autoridades regulatorias (si aplica)  

---

## 9. Lecciones aprendidas

- Actualizar reglas de detección  
- Implementar o reforzar MFA  
- Capacitar a usuarios sobre phishing  
- Documentar IoCs y técnicas utilizadas  

---

**Nota:** Este playbook debe actualizarse periódicamente según nuevas amenazas o cambios en la infraestructura.
