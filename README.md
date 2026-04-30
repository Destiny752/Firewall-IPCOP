Implementación de Firewall Perimetral en Infraestructura de Red
Este repositorio contiene la documentación y los esquemas de configuración para el despliegue de un firewall (basado en IPCop) dentro de una infraestructura de red profesional. El objetivo es centralizar la seguridad perimetral y gestionar el tráfico entre diferentes segmentos de red.

🏗️ Arquitectura de la Infraestructura
El diseño se basa en un modelo de segmentación por zonas para aislar el tráfico sensible del tráfico público, siguiendo el estándar de colores:

Zona Roja (Internet): Conexión WAN externa. Es el punto de entrada desde el router del ISP hacia nuestra infraestructura.

Zona Verde (LAN Privada): Segmento de red local donde se encuentran los equipos internos (PCs de trabajo, impresoras). Esta zona tiene acceso total a las demás, pero es inaccesible desde el exterior.

Zona Naranja (DMZ): Zona Desmilitarizada. Aquí se ubican los servidores que deben ser accesibles desde Internet (Web, Mail) sin poner en riesgo la red interna verde.

Zona Azul (WLAN): Segmento dedicado a la red inalámbrica, aislado de la red cableada principal para mejorar la seguridad de los dispositivos móviles.

🛠️ Componentes y Configuración
Requisitos de Hardware / Entorno
Interfaces de Red: Se requieren al menos 2 NICs (Tarjetas de Red) físicas o virtuales, aunque lo ideal son 3 o 4 para cubrir todas las zonas.

Plataforma: Montaje sobre hardware dedicado o entorno virtualizado (VirtualBox / VMware / Proxmox).

Servicios Gestionados por el Firewall
Filtrado de Paquetes (SPI): Inspección activa de todo el tráfico entrante y saliente.

Servidor DHCP: Gestión automática de direccionamiento IP para las zonas Verde y Azul.

Proxy Web: Cacheo de contenido y filtrado de URLs para optimizar el ancho de banda.

Gestión de Logs: Monitorización en tiempo real de intentos de intrusión y uso de la red.

🚀 Proceso de Despliegue
Preparación de la Red: Configuración de los adaptadores de red en modo puente o red interna según la topología.

Instalación del Sistema: Despliegue del binario de IPCop y asignación de las interfaces de red a sus respectivos colores.

Configuración de Reglas:

Bloqueo por defecto de todo el tráfico entrante a la zona Verde.

Configuración de Port Forwarding (NAT) para servicios específicos en la zona Naranja.

Verificación: Pruebas de conectividad entre zonas y validación del bloqueo de tráfico no autorizado.

📂 Estructura del Repositorio
/docs: Guías paso a paso de la configuración.

/img: Diagramas de red y capturas de la interfaz de administración.

/config: Archivos de respaldo o scripts de configuración aplicados.

Nota Técnica: Este proyecto ha sido desarrollado como parte del módulo de seguridad y redes en el grado de SMR, demostrando la capacidad de fortificar una infraestructura de red corporativa mediante soluciones de código abierto.
