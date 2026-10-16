
# PRIMERA ENTREGA - RASPBERRY PI Y SSH

**Alumnos:** Candiotto Gino, Joaquin Sverko, Genaro Correa, Facundo Angelelli

**Fecha:** 10 de octubre

**Tema:** Instalación del sistema operativo y configuración de SSH

## 1. INTRODUCCIÓN

El objetivo de esta primera entrega es investigar y realizar la instalación desde cero del sistema operativo de una Raspberry Pi, con la finalidad de utilizarla posteriormente como un servidor para brindar distintos servicios dentro de una red local.

Además de instalar el sistema operativo, se configuró el servicio **SSH** (*Secure Shell*). Este servicio permite conectarse de manera remota a la Raspberry Pi desde otra computadora mediante una conexión segura, sin necesidad de conectar físicamente un monitor, teclado o mouse al dispositivo.

Para esta práctica se utilizó **Raspberry Pi OS Lite (64-bit)**, una versión del sistema operativo que no incluye entorno gráfico de escritorio y que resulta adecuada para utilizar la Raspberry Pi como servidor.

## 2. ¿QUÉ ES UNA RASPBERRY PI?

Una Raspberry Pi es una computadora de pequeñas dimensiones desarrollada originalmente por la *Raspberry Pi Foundation*. A pesar de su tamaño reducido, posee los componentes necesarios para ejecutar un sistema operativo y realizar numerosas tareas informáticas.

Dependiendo del modelo, una Raspberry Pi puede disponer de:

- Procesador
- Memoria RAM
- Puertos USB
- Puerto HDMI
- Conexión Ethernet
- Wi-Fi
- Bluetooth
- GPIO (*General Purpose Input/Output*)
- Ranura para tarjeta microSD

La tarjeta microSD se utiliza habitualmente como medio de almacenamiento donde se instala el sistema operativo.

La Raspberry Pi puede utilizarse para diferentes finalidades, por ejemplo:

- Servidores web
- Servidores de archivos
- Servidores DNS
- Automatización
- Redes
- Domótica
- Proyectos educativos
- Desarrollo de aplicaciones
- Administración de servicios dentro de una red local

En este proyecto se utilizará como base para posteriormente implementar diferentes servicios de red.

## 3. SISTEMA OPERATIVO

Un sistema operativo (SO) es el software principal que permite administrar los recursos de una computadora y proporcionar una interfaz para que el usuario pueda utilizarla.

Entre sus funciones se encuentran:

- Administrar el procesador.
- Administrar la memoria.
- Administrar los dispositivos de almacenamiento.
- Administrar las conexiones de red.
- Gestionar archivos y directorios.
- Ejecutar programas y servicios.
- Controlar dispositivos conectados.

En una Raspberry Pi existen diferentes sistemas operativos compatibles. Uno de los principales es **Raspberry Pi OS**, basado en Debian.

## 4. RASPBERRY PI OS

Raspberry Pi OS es el sistema operativo oficial desarrollado para las computadoras Raspberry Pi.

Existen diferentes variantes del sistema operativo. Para esta práctica se seleccionó:

> **Raspberry Pi OS Lite (64-bit)**

La versión *Lite* se caracteriza por no incluir un entorno gráfico de escritorio. Esto significa que la interacción con el sistema se realiza principalmente mediante una terminal de comandos.

Esta característica es especialmente útil cuando la Raspberry Pi se utiliza como servidor, ya que no es necesario consumir recursos del sistema en una interfaz gráfica que no resulta necesaria para administrar los servicios.

## 5. ¿QUÉ ES UN ENTORNO DE ESCRITORIO?

Un entorno de escritorio es una interfaz gráfica que permite utilizar el sistema operativo mediante ventanas, iconos, menús y otros elementos visuales.

Por ejemplo, un sistema con escritorio permite:

- Abrir ventanas.
- Utilizar un explorador de archivos.
- Ejecutar aplicaciones gráficas.
- Utilizar menús.
- Configurar el sistema mediante interfaces visuales.

En esta práctica el entorno de escritorio **no debe instalarse**, porque la Raspberry Pi será utilizada como servidor. En lugar de utilizar una interfaz gráfica, se administrará mediante una terminal y, posteriormente, mediante SSH.

## 6. ¿QUÉ ES UN SERVIDOR?

Un servidor es un equipo que proporciona servicios o recursos a otros dispositivos llamados **clientes** dentro de una red.

Por ejemplo, un servidor puede proporcionar:

- Archivos
- Páginas web
- Bases de datos
- Servicios DNS
- Servicios DHCP
- Acceso remoto

En este proyecto la Raspberry Pi funcionará como una computadora destinada a ejecutar servicios para otros dispositivos de la red local.

## 7. ¿QUÉ ES SSH?

**SSH** significa *Secure Shell*. Es un protocolo de red que permite establecer una conexión remota y segura con otro equipo.

Mediante SSH es posible conectarse a la Raspberry Pi desde otra computadora y utilizar su terminal como si se estuviera trabajando directamente sobre ella.

Sintaxis general:

```bash
ssh usuario@direccion_ip
```

Si la Raspberry Pi tiene la dirección IP `192.168.60.211` y el usuario es `grupo7`, la conexión puede realizarse mediante:

```bash
ssh grupo7@192.168.60.211
```

## 8. ¿PARA QUÉ SIRVE SSH?

SSH permite administrar un equipo remotamente. En este proyecto resulta especialmente útil porque permite administrar la Raspberry Pi sin necesidad de conectar:

- Monitor
- Teclado
- Mouse

La Raspberry puede permanecer conectada a la red y nosotros podemos utilizar otra computadora para acceder a ella. Esto es muy habitual en servidores, ya que muchas veces estos equipos funcionan sin una interfaz gráfica y se administran exclusivamente mediante conexiones remotas.

## 9. ¿POR QUÉ SSH ES SEGURO?

SSH utiliza mecanismos de autenticación y cifrado para proteger la comunicación entre el cliente y el servidor.

Cuando un usuario se conecta mediante SSH:

1. El cliente intenta establecer una conexión con el servidor.
2. El servidor se identifica.
3. Se establece una comunicación protegida.
4. El usuario se autentica.
5. Una vez autenticado, puede utilizar la terminal remotamente.

De esta manera, la información que se intercambia durante la sesión está protegida frente a una simple transmisión sin cifrado.

## 10. CLIENTE Y SERVIDOR SSH

En una conexión SSH intervienen dos partes:

- **CLIENTE SSH:** Es el dispositivo desde el cual se realiza la conexión. *(En nuestro caso: PC con Windows)*
- **SERVIDOR SSH:** Es el dispositivo al cual nos conectamos. *(En nuestro caso: Raspberry Pi)*

La comunicación queda representada de la siguiente manera:

```text
PC con Windows (Cliente)
      |
      | SSH (Puerto TCP 22)
      v
Raspberry Pi (Servidor)
```

## 11. DIRECCIÓN IP

Para poder establecer una conexión SSH dentro de una red local necesitamos conocer la dirección IP de la Raspberry Pi.

Una dirección IP identifica un dispositivo dentro de una red (por ejemplo: `192.168.60.211`). La dirección concreta puede variar dependiendo de la configuración de la red y del router.

Una vez conocida la IP, podemos utilizarla para conectarnos mediante SSH.

## 12. RASPBERRY PI IMAGER

Para instalar el sistema operativo utilizamos **Raspberry Pi Imager**. Es una herramienta que permite preparar una tarjeta microSD para utilizarla en una Raspberry Pi.

Entre otras cosas, permite:

- Seleccionar el modelo de Raspberry Pi.
- Seleccionar el sistema operativo.
- Seleccionar el dispositivo de almacenamiento.
- Configurar determinados parámetros del sistema.
- Grabar el sistema operativo en la microSD.

Esto facilita considerablemente la instalación inicial.

## 13. INSTALACIÓN DEL SISTEMA OPERATIVO

### 13.1. Abrir Raspberry Pi Imager

Primero se abrió Raspberry Pi Imager en una computadora con Windows. La tarjeta microSD fue conectada a la computadora mediante un lector de tarjetas.

### 13.2. Seleccionar el Dispositivo

Dentro de Raspberry Pi Imager se seleccionó el modelo correspondiente de Raspberry Pi (Raspberry Pi 3). Esta selección permite que el programa prepare correctamente la instalación para el dispositivo utilizado.

### 13.3. Seleccionar el Sistema Operativo

En la sección de sistemas operativos se seleccionó: `Raspberry Pi OS (other)` -> `Raspberry Pi OS Lite (64-bit)`

La elección de esta versión fue importante porque la consigna solicita instalar el sistema operativo sin entorno de escritorio.

### 13.4. Seleccionar la Tarjeta MicroSD

En la opción de almacenamiento se seleccionó la tarjeta microSD conectada previamente a la computadora. Se tuvo en cuenta que este procedimiento elimina la información existente en la tarjeta.

## 14. CONFIGURACIÓN INICIAL DEL SISTEMA

Antes de grabar el sistema operativo se configuraron diferentes parámetros en el menú de opciones de personalización (*OS Customization*).

### 14.1. Nombre del Equipo

Se configuró un nombre para identificar la Raspberry dentro de la red: `servidor-rpi`

Este nombre permite identificar más fácilmente el dispositivo en la red local.

### 14.2. Usuario

Se creó el usuario: `grupo7`

Este usuario será utilizado posteriormente para iniciar sesión y conectarse mediante SSH.

### 14.3. Contraseña

Se estableció una contraseña para el usuario. Esta contraseña es necesaria para autenticarse cuando se realiza una conexión SSH utilizando autenticación mediante contraseña.

### 14.4. Configuración de Red

No se configuró la red inalámbrica ya que se hará por cable Ethernet. Si la Raspberry se conecta mediante Ethernet, la conexión se realiza directamente utilizando el cable de red local.

## 15. ACTIVACIÓN DE SSH

Uno de los pasos más importantes de la configuración fue habilitar SSH. En las opciones de personalización del sistema de Raspberry Pi Imager se activó la casilla `Enable SSH` seleccionando la autenticación mediante contraseña.

Adicionalmente, dentro del sistema operativo es posible gestionar y verificar este servicio ejecutando el comando de configuración del sistema:

```bash
sudo raspi-config
```

Al ejecutar este comando se accede al menú `3 Interface Options` y posteriormente a `I1 SSH`, donde se confirma la activación del servicio.

## 16. GRABACIÓN DE LA MICROSD

Una vez configurados todos los parámetros:

1. Se guardó la configuración.
2. Se confirmó la selección de la microSD.
3. Raspberry Pi Imager comenzó a escribir el sistema operativo.
4. Se esperó a que finalizara el proceso.
5. Se realizó la verificación correspondiente.
6. Se expulsó la tarjeta de forma segura.

> **Nota:** Durante este proceso no se debe retirar la tarjeta, ya que podría interrumpirse la escritura de bloques y corromperse el sistema de archivos.

## 17. PRIMER INICIO DE LA RASPBERRY PI

Una vez finalizada la preparación de la microSD:

1. Se retiró la microSD de la computadora.
2. Se colocó en la ranura de la Raspberry Pi.
3. Se conectó la Raspberry a la red mediante cable Ethernet.
4. Se conectó el cable micro-USB de alimentación.
5. Se esperó a que iniciara el sistema.

Al utilizar Raspberry Pi OS Lite, el sistema inicia en modo consola de texto puro (CLI) sin interfaz gráfica.

## 18. OBTENER LA DIRECCIÓN IP

Para realizar una conexión SSH es indispensable conocer la dirección IP local de la Raspberry Pi.

Desde la propia terminal de la Raspberry Pi, se pueden ejecutar los siguientes comandos para verificar la red:

### Comando 1:

```bash
hostname -i
```

- **`hostname`:** Programa de Linux que muestra o establece el nombre de red del equipo.
- **`-i` (minúscula):** Opción que indica consultar la dirección IP a la que se resuelve el nombre de host en el archivo local `/etc/hosts` (devuelve habitualmente `127.0.1.1`, que es la IP de loopback local).

### Comando 2:

```bash
hostname -I
```

- **`hostname`:** Comando principal.
- **`-I` (mayúscula):** Opción que examina todas las interfaces de red físicas conectadas (Ethernet/Wi-Fi) y muestra las direcciones IP reales asignadas en la red local LAN (en nuestro caso devolvió `192.168.60.211`).

También se puede buscar la IP desde una PC cliente en Windows ejecutando:

```powershell
ping servidor-rpi.local
```

- **`ping`:** Utilidad de red que envía paquetes ICMP para verificar si un equipo está accesible.
- **`servidor-rpi.local`:** Nombre de red asignado a la Raspberry Pi resuelto mediante el protocolo mDNS.

## 19. CONEXIÓN MEDIANTE SSH

Una vez conocida la dirección IP, se abrió la consola (PowerShell o CMD) en la computadora cliente con Windows y se ejecutó el comando de conexión SSH.

```bash
ssh grupo7@192.168.60.211
```

### Desglose detallado del comando:

- **`ssh`:** Llama al cliente del protocolo *Secure Shell* instalado en el sistema operativo.
- **`grupo7`:** Especifica el nombre de la cuenta de usuario con la que deseamos autenticarnos en el sistema remoto.
- **`@`:** Símbolo separador obligatorio que conecta el nombre de usuario con la dirección del host de destino.
- **`192.168.60.211`:** Dirección IPv4 privada que identifica unívocamente a la Raspberry Pi dentro de la red local.

## 20. PRIMERA CONEXIÓN

Al conectarse por primera vez a un nuevo servidor SSH, el cliente detecta que no tiene guardada la huella digital (*fingerprint*) de la clave pública del servidor. El sistema muestra un mensaje de advertencia para confirmar la autenticidad del equipo.

Para continuar se debe escribir:

```text
yes
```

Esto almacena la clave en el archivo `known_hosts` de la computadora cliente.

Posteriormente, el servidor solicita la clave del usuario. Se ingresa la contraseña configurada durante la instalación.

> **Nota de seguridad:** Por diseño de seguridad en Linux, mientras se digita la contraseña no se muestran caracteres, asteriscos ni espacios en la pantalla.

## 21. COMPROBACIÓN DEL SERVICIO SSH

Una vez iniciada la sesión remota en la Raspberry Pi, se verificó que el demonio del servidor SSH se estuviera ejecutando correctamente con el siguiente comando:

```bash
sudo systemctl status ssh
```

### Desglose detallado del comando:

- **`sudo`:** (*Superuser Do*) Otorga privilegios temporales de superusuario (root) para consultar registros del sistema e información administrativa sensible.
- **`systemctl`:** Herramienta central de control en Linux para administrar el sistema de inicio y el gestor de servicios `systemd`.
- **`status`:** Subcomando de `systemctl` que solicita el estado operativo instantáneo de un servicio.
- **`ssh`:** Nombre específico de la unidad de servicio (`ssh.service`) sobre la cual se realiza la consulta.

### Análisis del resultado obtenido en pantalla:

- **`Loaded: loaded (...; enabled; ...)`:** Confirma que el servicio está instalado y configurado para **iniciarse automáticamente** con cada encendido de la máquina.
- **`Active: active (running)`:** Certifica que el servicio está **activo y ejecutándose en la memoria RAM**.
- **`Main PID: 2043 (sshd)`:** Muestra el número identificador único de proceso que el núcleo de Linux le asignó al programa `sshd`.
- **`Server listening on 0.0.0.0 port 22`:** Informa que el servidor SSH está a la escucha de solicitudes de red entrantes en el puerto **TCP 22**.
- **`Accepted password for grupo7 from 192.168.60.147`:** Registro de auditoría que demuestra que una computadora cliente con la IP `192.168.60.147` logró autenticarse e iniciar sesión exitosamente en la Raspberry Pi.

## 22. COMANDOS UTILIZADOS Y DESGLOSE TÉCNICO

A continuación se detalla cada comando ejecutado en la terminal durante la práctica, desglosando sus componentes, opciones y funcionamiento.

### 1. Consultar la versión del sistema operativo

```bash
cat /etc/os-release
```

- **`cat`:** (*Concatenate*) Comando utilizado para leer y desplegar el contenido completo de un archivo de texto en la consola.
- **`/etc/os-release`:** Ruta absoluta al archivo que almacena la información oficial de la distribución Linux instalada. Muestra datos como `NAME="Debian GNU/Linux"` y `VERSION="13 (trixie)"`.

### 2. Consultar el nombre del equipo

```bash
hostname
```

- **`hostname`:** Muestra en pantalla el nombre asignado al equipo en la red (ejemplo: `servidor-rpi` o `grupo7`).

### 3. Mapear la dirección IP local de red

```bash
hostname -I
```

- **`hostname`:** Comando para gestionar nombres e IPs del equipo.
- **`-I`:** Flag en mayúscula que escanea las tarjetas de red y devuelve todas las direcciones IP asignadas en la red física LAN (ejemplo: `192.168.60.211`).

### 4. Verificar el estado del servicio SSH

```bash
sudo systemctl status ssh
```

- **`sudo`:** Ejecuta el comando con permisos de administrador (root).
- **`systemctl`:** Programa de administración de `systemd`.
- **`status`:** Opción para pedir el diagnóstico de ejecución.
- **`ssh`:** Nombre de la unidad de servicio objetivo.

### 5. Actualizar la lista de repositorios

```bash
sudo apt update
```

- **`sudo`:** Ejecuta con permisos del superusuario root.
- **`apt`:** (*Advanced Package Tool*) Gestor oficial de paquetes de software en sistemas Debian y Raspberry Pi OS.
- **`update`:** Subcomando que descarga la lista actualizada de paquetes y versiones disponibles desde los repositorios en Internet (no instala ni actualiza programas aún, solo actualiza la base de datos local).

### 6. Actualizar las aplicaciones e instalación de paquetes

```bash
sudo apt upgrade -y
```

- **`sudo`:** Privilegios de administrador.
- **`apt`:** Gestor de paquetes.
- **`upgrade`:** Subcomando que descarga e instala las versiones más recientes de todos los paquetes instalados previamente en el sistema.
- **`-y`:** (*Yes*) Parámetro opcional que responde automáticamente "sí" a todas las confirmaciones de descarga e instalación, evitando que el proceso se detenga a pedir interacción del usuario.

### 7. Iniciar conexión SSH desde la computadora cliente

```powershell
ssh grupo7@192.168.60.211
```

- **`ssh`:** Cliente del protocolo SSH.
- **`grupo7`:** Usuario remoto registrado en la Raspberry Pi.
- **`@`:** Carácter separador entre usuario y host.
- **`192.168.60.211`:** Dirección IP del servidor de destino.

## 23. RESULTADO FINAL

Al finalizar la práctica se obtuvo una Raspberry Pi configurada como un sistema preparado para funcionar como servidor.

Las características principales de la instalación fueron:

- Sistema operativo Raspberry Pi OS Lite (64-bit) basado en Debian 13 "trixie".
- Sin entorno gráfico de escritorio.
- Usuario `grupo7` configurado.
- Contraseña de acceso configurada.
- Conexión a la red local mediante interfaz Ethernet.
- Servicio SSH habilitado y funcionando en el puerto 22.
- Posibilidad de administrar la Raspberry remotamente desde una computadora.

**Esquema final de funcionamiento:**

```text
PC CON WINDOWS (Cliente)
      |
      | Conexión SSH (Puerto TCP 22 / Cifrada)
      v
RASPBERRY PI (Servidor - IP 192.168.60.211)
      |
      | Raspberry Pi OS Lite (Sin GUI)
      v
SERVICIOS DE RED LOCAL
```

## 24. CONCLUSIÓN

En esta primera entrega se investigó el funcionamiento básico de una Raspberry Pi y se realizó la instalación de un sistema operativo orientado a su utilización como servidor.

Se seleccionó **Raspberry Pi OS Lite (64-bit)** debido a que la consigna requiere trabajar sin entorno de escritorio. Esto permite utilizar la Raspberry Pi principalmente mediante la terminal y reservar los recursos del equipo para los servicios que se instalarán posteriormente.

Además, se configuró el servicio **SSH**, que permite acceder remotamente a la Raspberry Pi desde otra computadora dentro de la red. Gracias a este protocolo, es posible administrar el servidor sin necesidad de utilizar un monitor, teclado o mouse conectados directamente a la Raspberry.

De esta manera, la Raspberry Pi queda preparada para las siguientes etapas del proyecto, en las cuales podrá utilizarse como servidor para implementar diferentes servicios dentro de la red local.
