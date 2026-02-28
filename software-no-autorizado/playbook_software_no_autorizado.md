# Playbook de Respuesta a Incidentes de Ejecución de Software No Autorizado

## Escenario o Tipo de Incidente
**Tipo:** Ejecución de software no autorizado en sistemas de la clínica.  
**Descripción:**
- Software no registrado ejecutándose en endpoints o servidores internos.
- Riesgo de pérdida de datos, malware y afectación de atención clínica.

**Impacto:**
- Interrupción de servicios clínicos.
- Riesgo de exposición de datos de pacientes.
- Vulnerabilidad a malware y brechas regulatorias.

## Detección
**Herramientas:**
- EDR (Endpoint Detection & Response)
- SIEM corporativo gestionado por SOC MSSP
- Antivirus y firewall de endpoints
- Logs de servidores y dispositivos médicos

**Indicadores de Compromiso (IoCs):**
- Ejecución de software no registrado
- Conexiones externas sospechosas
- Modificaciones de archivos críticos
- Comportamiento anómalo detectado por EDR

## Clasificación del Incidente

| Criterio               | Valor                                           |
|------------------------|------------------------------------------------|
| Severidad              | Media/Alta                                     |
| Sistemas afectados     | Endpoints, servidores internos, dispositivos médicos |
| Nivel de exposición    | Interna (posible propagación a otros sistemas) |

## Respuesta Inicial
1. Aislar el endpoint o servidor afectado.
2. Bloquear ejecución del software no autorizado.
3. Revocar credenciales si hay sospecha de escalamiento.
4. Activar preservación de evidencia (logs, volcados de memoria, capturas de red).
5. Notificar al SOC MSSP para coordinación de respuesta remota.

## Análisis y Contención
1. SOC MSSP realiza análisis forense del endpoint/servidor afectado.
2. Determinar origen, vector de ataque y cronología.
3. Contener temporalmente los sistemas afectados.
4. Validar que no haya propagación a otros endpoints o servidores.
5. Mantener actualizado al equipo interno de TI sobre hallazgos.

## Erradicación y Recuperación
1. Desinstalar software no autorizado.
2. Restaurar configuraciones seguras.
3. Aplicar parches y reforzar políticas de software permitido.
4. Validar integridad de sistemas y dispositivos conectados.
5. Revisar y reconectar sistemas solo tras validación completa.

## Notificación
**Interna:** SOC MSSP, personal afectado.  
**Externa:** Socios tecnológicos o proveedores según corresponda.

## Lecciones Aprendidas
1. Documentar cronología, sistemas afectados, impacto y acciones.
2. Reunión post-mortem con SOC MSSP y personal interno.
3. Actualizar políticas, procedimientos y playbook.
4. Capacitar al personal sobre ejecución segura de software autorizado.

> **Nota:** Este playbook es un documento vivo. Debe actualizarse ante nuevos incidentes de software no autorizado o cambios en la infraestructura.
