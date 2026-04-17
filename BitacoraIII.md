# Fundamentos de Seguridad y Auditoría

## ***Anatomía de Syslog***

Syslog se utiliza para el registro de mensajes en sistemas tipo Unix y Linux, formalizado principalmente en el RFC 5424. [1] 
Funciona como si fuera un sistema para separar la generacion de mensajes, almacenamiento y analisis.

Clasificacion del mensaje Syslog:
- Facility: Indica quién o qué categoría del sistema está enviando el mensaje.
  - auth / authpriv: Mensajes relacionados con seguridad y autenticación.
  - cron: Mensajes del planificador de tareas.
  - daemon: Procesos de fondo que no tienen una categoría específica.
  - kern: Mensajes del kernel.
  - mail: Sistema de correo.
  - local0 - local7: Reservados para que los administradores o aplicaciones personalizadas los usen.[2]
    
- Severity: indica la gravedad del evento, va del 0 al 7 y contra menor sea el valor mas grave es.
  - 0: emergencia, el sistema es inutilizable.
  - 1: alerta, tienen que tomarse medidas de inmediato.
  - 2: critico, las condiciones son criticas.
  - 3:	Error, las condiciones son de error.
  - 4: Advertencia, las condiciones son de advertencia.
  - 5:	Aviso, afeccion normal pero significativa.
  - 6:	Informativo, mensajes informativos.
  - 7:	Depurar, mensajes nivel depuracion. [3]
 
**¿Por qué es una negligencia grave que el archivo /var/log/auth.log tenga permisos de lectura para usuarios no privilegiados?**
Porque tendría una gran vulnerabilidad ya que este archivo guarda todos los intentos de autenticación, por lo que deben de ser los usuarios privilegiados quienes tengan los permisos para leer este archivo tan importante, ya que si no son estos, cualquiera puede atacar este archivo y al servidor.

**¿Qué información específica (como PIDs, nombres de usuario o direcciones IP) diferencia un intento fallido de conexión remota SSH de un simple fallo de contraseña de un usuario local frente a la pantalla?**
Diferencia el formato de línea y las palabras clave que utiliza el PAM que es lo que se usa para la autenticacion y el servicio SSH.
- Intento remoto:
  - Proceso: sshd
  - Origen: Siempre verás una dirección IP y un puerto.
  - Ejemplo: sshd[PID]: Failed password for user from 192.168.1.50.

- Intento local:
  - Proceso: login o getty.
  - Origen: Verás una terminal física (tty). No hay ninguna IP.
  - Ejemplo: login[PID]: FAILED LOGIN on **'/dev/tty1'** FOR 'user'.

## ***Gestión Centralizada de Logs y Cumplimiento Legal***
Ventajas de la Centralización:
  - Inalterabilidad: el atacante puede ser root y borrarlo todo en la máquina, pero no puede borrar lo que ya se envió fuera.
  - Vision en tiempo real: si el servidor se rompe o tiene un ataque Dos, los ultimos registros antes del fallo se quedan fuera para que se sepa que es lo que ocurrió.
  - Correlacion de eventos: ves lo que pasa en 100 máquinas desde un solo panel, detectando ataques globales en lugar de mirar 100 archivos distintos. 



