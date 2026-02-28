# Playbook – Accesos sospechosos en endpoints

## Descripción
Playbook para incidentes de accesos sospechosos o no autorizados en endpoints.  
Incluye pasos de detección, contención, erradicación y recuperación, integrado con Wazuh SIEM.

## Evento detonante
Alerta de Wazuh detectando:  
- Múltiples intentos fallidos de inicio de sesión  
- Acceso desde ubicaciones inusuales  
- Uso de credenciales fuera del horario laboral  
- Cambios de privilegios no autorizados  

## Respuesta inicial
1. Generar alerta automática en Wazuh o SIEM  
2. Aislar endpoint afectado  
3. Bloquear temporalmente la cuenta sospechosa  
4. Forzar cambio de credenciales  
5. Preservar logs  
6. Notificar SOC MSSP  

## Análisis y contención
1. Revisar logs de autenticación y eventos  
2. Verificar origen del acceso (IP, ubicación, horario)  
3. Confirmar actividad legítima o maliciosa  
4. Contener accesos adicionales  

## Erradicación y recuperación
1. Revocar sesiones activas sospechosas  
2. Restablecer credenciales y reforzar políticas  
3. Revisar privilegios del usuario  
4. Validar integridad del endpoint  
5. Reincorporar endpoint tras validación  

## Notificación
- Interna: SOC MSSP, equipo TI, gerencia  
- Externa: autoridades regulatorias si aplica  

## Lecciones aprendidas
1. Documentar cronología y acciones  
2. Identificar fallas en controles de acceso  
3. Ajustar reglas de detección en Wazuh  
4. Capacitar al personal sobre acceso seguro
