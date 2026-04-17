# AEE.-Bitacora_III_Garcia_Rojas_Pablo
**Fundamentos de Seguridad y Auditoría**
Syslog se utiliza para el registro de mensajes en sistemas tipo Unix y Linux, formalizado principalmente en el RFC 5424. [1] 
Funciona como si fuera un sistema para separar la generacion de mensajes, almacenamiento y analisis.

Clasificacion del mensaje Syslog:
- Facility: Indica quién o qué categoría del sistema está enviando el mensaje.
  - auth / authpriv: Mensajes relacionados con seguridad y autenticación.
  - cron: Mensajes del planificador de tareas.
  - daemon: Procesos de fondo que no tienen una categoría específica.
  - kern: Mensajes del kernel.
  - mail: Sistema de correo.
  - local0 - local7: Reservados para que los administradores o aplicaciones personalizadas los usen.
    
- Severity: indica la gravedad del evento, va del 0 al 7 y contra menor sea el valor mas grave es.
  - 0: emergencia, el sistema es inutilizable.
  - 1: alerta, tienen que tomarse medidas de inmediato.
  - 2: critico, las condiciones son criticas.
  - 3:	Error, las condiciones son de error.
  - 4: Advertencia, las condiciones son de advertencia.
  - 5:	Aviso, afeccion normal pero significativa.
  - 6:	Informativo, mensajes informativos.
  - 7:	Depurar, mensajes nivel depuracion.
 
¿Por qué es una negligencia grave que el archivo /var/log/auth.log tenga permisos de lectura para usuarios no privilegiados?

