# Laboratorio: Subnetting VLSM y Enrutamiento Estático Multi-Router (Clase C)

## Descripción del Proyecto
Este laboratorio demuestra el diseño e implementación de una infraestructura de red corporativa multi-router de Clase C (`192.168.1.0/24`) aplicando **VLSM (Variable Length Subnet Mask)** para maximizar la eficiencia del direccionamiento IP y eliminar el desperdicio de hosts. 

La topología conecta 4 LANs independientes a través de una malla redundante de 4 routers interconectados mediante enlaces punto a punto enrutados de manera estática.

## Topología
![Topología de la red](topologia.png)

## Tabla de Direccionamiento IP (Esquema VLSM)

| Subred / Área | Hosts Req. | Dirección de Red | Máscara de Red | Prefijo | Rango Útil de IPs | Broadcast |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Red 4 (Rosa)** | 80 | `192.168.1.0` | `255.255.255.128` | `/25` | `192.168.1.1 - 192.168.1.126` | `192.168.1.127` |
| **Red 2 (Amarilla)** | 55 | `192.168.1.128` | `255.255.255.192` | `/26` | `192.168.1.129 - 192.168.1.190` | `192.168.1.191` |
| **Red 3 (Naranja)** | 16 | `192.168.1.192` | `255.255.255.224` | `/27` | `192.168.1.193 - 192.168.1.222` | `192.168.1.223` |
| **Red 1 (Azul)** | 10 | `192.168.1.224` | `255.255.255.240` | `/28` | `192.168.1.225 - 192.168.1.238` | `192.168.1.239` |
| **Enlace P2P (Morado)** | 2 | `192.168.1.240` | `255.255.255.252` | `/30` | `192.168.1.241 - 192.168.1.242` | `192.168.1.243` |
| **Enlace P2P (Verde)** | 2 | `192.168.1.244` | `255.255.255.252` | `/30` | `192.168.1.245 - 192.168.1.246` | `192.168.1.247` |
| **Enlace P2P (Rojo)** | 2 | `192.168.1.248` | `255.255.255.252` | `/30` | `192.168.1.249 - 192.168.1.250` | `192.168.1.251` |
| **Enlace P2P (Azul C.)** | 2 | `192.168.1.252` | `255.255.255.252` | `/30` | `192.168.1.253 - 192.168.1.254` | `192.168.1.255` |

---

## Objetivos del Laboratorio
1. Calcular y asignar subredes de tamaño variable partiendo del bloque `192.168.1.0/24` ordenando por requerimiento de mayor a menor número de hosts.
2. Configurar direcciones IP en interfaces LAN (FastEthernet/GigabitEthernet) y enlaces WAN punto a punto entre routers.
3. Establecer conectividad total (*End-to-End*) configurando rutas estáticas manuales (`ip route`) en cada uno de los 4 routers.
4. Validar tablas de enrutamiento y realizar pruebas de ICMP (`ping` y `traceroute`) entre hosts ubicados en distintas subredes extremas.
