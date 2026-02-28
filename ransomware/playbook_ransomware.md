# Playbook de Respuesta a Incidentes de Ransomware

## Escenario o Tipo de Incidente
**Tipo:** Ransomware dirigido a endpoints y servidores internos de la clínica.  
**Descripción:**
- Ataque que cifra archivos críticos en PCs, laptops y servidores internos.
- Nivel de seguridad bajo, personal poco capacitado y dispositivos médicos conectados sin control.
- Impacto: interrupción de atención a pacientes, pérdida de datos sensibles, riesgos legales.

## Detección
**Herramientas:**
- EDR (Endpoint Detection & Response)
- SIEM corporativo gestionado por SOC MSSP
- Antivirus y firewall de endpoints
- Monitoreo de logs de dispositivos médicos y servidores de EMR

**Indicadores de Compromiso (IoCs):**
- Archivos cifrados con extensión desconocida
- Mensajes de rescate en pantalla
- Procesos sospechosos ejecutándose en PCs/laptops
- Conexiones a IPs o dominios maliciosos
- Actividad anómala en servidores internos o dispositivos médicos conectados

## Clasificación del Incidente

| Criterio               | Valor                                                        |
|------------------------|-------------------------------------------------------------|
| Severidad              | Alta                                                        |
| Sistemas o datos afectados | EMR, estaciones de trabajo de médicos y administración, servidores internos |
| Nivel de exposición     | Interna (riesgo de propagación a backups y otros sistemas) |

## Respuesta Inicial
1. Aislar endpoints y servidores comprometidos.
2. Bloquear IPs y dominios maliciosos.
3. Revocar credenciales comprometidas.
4. Activar preservación de evidencia (logs, volcados de memoria, capturas de red).
5. Notificar al SOC MSSP para coordinar la respuesta.

## Análisis y Contención
1. SOC MSSP realiza análisis forense en endpoints y servidores.
2. Determinar vector de ataque y cronología del incidente.
3. Contener sistemas afectados en cuarentena.
4. Validar que no haya propagación a otros dispositivos.
5. Actualizar al equipo interno de TI sobre hallazgos.

## Erradicación y Recuperación
1. Eliminar malware y cerrar posibles backdoors.
2. Restaurar datos desde backups verificados.
3. Aplicar parches y reforzar configuraciones de seguridad.
4. Validar integridad de sistemas clínicos y dispositivos conectados.
5. Revisión final antes de reconectar los dispositivos a la red.

## Notificación
**Interna:** SOC MSSP, gerencia, médicos responsables, RRHH.  
**Externa:** Autoridades sanitarias y pacientes afectados según normativa de privacidad.

## Lecciones Aprendidas
1. Documentar el incidente completo: cronología, sistemas afectados, impacto, acciones y resultados.
2. Reunión post-mortem con SOC MSSP y personal interno.
3. Actualizar playbook y políticas internas según hallazgos.
4. Capacitar al personal sobre ciberseguridad.

> **Nota:** Este playbook es un documento vivo. Debe actualizarse ante nuevos ataques de ransomware o cambios en la infraestructura.

## 8. Lecciones Aprendidas
1. Documentar incidente completo: cronología, sistemas afectados, impacto, acciones y resultados.
2. Reunión post-mortem con SOC MSSP y personal interno.
3. Actualizar playbook y políticas internas según hallazgos.
4. Capacitar al personal sobre ciberseguridad. Capacitar personal en ciberseguridad
