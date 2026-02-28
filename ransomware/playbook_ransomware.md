# Playbook – Ransomware en endpoints

## Descripción
Playbook para respuesta a incidentes de ransomware en endpoints y servidores internos.  
Incluye pasos de detección, contención, erradicación y recuperación, adaptado a un entorno clínico con Wazuh SIEM.

## Evento detonante
Alerta de Wazuh relacionada con ransomware:  
- Archivos cifrados con extensión desconocida  
- Mensajes de rescate en pantalla  
- Procesos sospechosos  
- Conexiones a IPs o dominios maliciosos  

## Respuesta inicial
1. Aislar endpoints y servidores afectados  
2. Bloquear IPs y dominios maliciosos  
3. Revocar credenciales comprometidas  
4. Preservar evidencia  
5. Notificar al SOC MSSP  

## Análisis y contención
1. Revisar logs de Wazuh y endpoints afectados  
2. Determinar vector de ataque y cronología  
3. Contener sistemas en cuarentena  
4. Validar que no haya propagación  

## Erradicación y recuperación
1. Eliminar malware y backdoors  
2. Restaurar datos desde backups verificados  
3. Aplicar parches y reforzar configuraciones  
4. Validar integridad de historiales clínicos y dispositivos médicos  

## Notificación
- Interna: SOC MSSP, gerencia, médicos, RRHH  
- Externa: autoridades sanitarias y pacientes según normativa  

## Lecciones aprendidas
1. Documentar cronología y acciones tomadas  
2. Actualizar playbook y políticas internas  
3. Capacitar personal en ciberseguridad
