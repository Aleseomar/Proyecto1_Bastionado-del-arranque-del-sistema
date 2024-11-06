author: Alejandro Seoane Martínez
summary: Proyecto1
id: docs
categories: codelab,markdown
environments: Web
status: Published


# Bastionamiento de una BIOS/UEFI


## Introducción y preparación del proyecto

**Realizado por:** Alejandro Seoane Martínez  
**Asigantura:** Bastionado de redes y sistemas  
**Curso:** 2024/25  
**Grado:** G.E.C.E.G.S.

![Portada](docs/img/portada.png)

### Introducción
En este proyecto se nos encarga elaborar una guía para bastionar la BIOS/UEFI de un ordenador.

La BIOS es lo primero que se ejecuta en un ordenador cuando lo encendemos. En ella se guarda la información básica del dispositivo.   
Es por ello que tendremos que implementar unos controles de seguridad, debido a que puede haber alteraciones en el arranque de dispositivos o cambiar configuraciones importantes de la BIOS.

### Preparación

Para este proyecto necesitaremos configurar una BIOS. Para no tener que usar una BIOS real utilizaremos un emulador de BIOS que simula las mismas funciones que una BIOS real. [Enlace del emulador](https://download.lenovo.com/bsco/index.html#/).   

![imagen](docs/img/image.png)

Escogeremos un modelo de ordenador de los que nos ofrece el emulador y entraremos en la interfaz de texto, aunque hay algunos modelos que nos permiten seleccionar interfaz gráfica. 

![imagen1](docs/img/image1.png)

Una vez vista esta pequeña introducción vamos a realizar los distintos niveles de seguridad que podemos tener en la BIOS.



## Contraseñas

Nos dirigiremos a la pestaña de *Security* para empezar con la configuración. 
> **Nota:** Hay configuraciones en el emulador que nos saldrá el mensaje "*Emulator No Support*". Esto quiere decir que el emulador no puede ejecutar la acción pero nosotros hemos enseñado cómo se haría cada acción.

### Contraseña de administrador
Es la que limita el acceso a la configuración de la BIOS. 
Al entrar en la pestaña de seguridad encontraremos como primer parámetro "Set Supervisor Password". Con esta opción introduciremos una contraseña de administrador. 

![imagen2](docs/img/image2.png)

Nos saldrá el menú para implementar la contraseña de administrador. Nos pedirá la contraseñá y otra vez la confirmación de la contraseña. 

![imagen3](docs/img/image3.png)


### Contraseña de usuario
Funciona como contraseña de inicio. Se solicitará al arrancar el sistema o entrar en la BIOS.   
Esta contraseña también se puede referir a la **contraseña de arranque del dispositivo** (contraseña Power-On).

Como en el apartado anterior localizamos el apartado que se llama "Set Power-On Password".

![imagen4](docs/img/image4.png)

Nos aparecerá un menú donde ingresar la contraseña. 

![imagen5](docs/img/image5.png)

## Secure Boot
Es una característica de seguridad que la implementó Windows y algunas distribuciones de Linux se han adaptado para permitir la ejecución de este.   
Secure Boot permite denegar la ejecución de software no firmado durante el arranque.

![imagen6](docs/img/image6.png)

Una vez entramos en el menú nos aparece los siguientes parámetros: 

![imagen7](docs/img/image7.png)

Nosotros nos fijaremos en activar la opción que nos dice Secure Boot. 

![imagen8](docs/img/image8.png)

## Configuración de arranque

### Orden de arranque
Definiremos la secuencia en la que el sistema buscará el dispositivo de arranque. Deberemos de configurarlo para priorizar el disco duro principal donde esté instalado el sistema operativo.  
Para ellos tendremos que irnos al apartado de "Startup" y entraremos en "Boot Priority Order". 

![imagen9](docs/img/image9.png)

Nosotros en este menú ordenaremos los distintos dispositivos de mayor a menor prioridad y lo guardaremos. 

![imagen10](docs/img/image10.png)

La opción de "First Boot Device" seleccionaremos "Boot Order" para que ejecute el orden que hemos definido anteriormente. 

![image11](/docs/img/image11.png)

### Permiso para el arranque desde dispositivos USB

Tener esta opción deshabilitada previene el arranque desde unidades extraíbles, reduciendo el riesgo de posibles arranques no autorizados. Esta opción nos aparece en la pestaña de Security como "Smart USB Protection".

![image12](/docs/img/image12.png)

Nos saldrá un menú con 3 opciones: 
- Deshabilitado
- Solo lectura (el usuario podrá copiar cosas del USB pero al revés no).
- Sin acceso (el usuario no podrá utilizar lo que tenga el USB).

![image13](/docs/img/image13.png)

Esta última opción es la que escogeremos. 

![image14](/docs/img/image14.png)


## Otras configuraciones de seguridad

Una vez explicados los puntos importantes que se nos pedían en el proyecto procederemos a explicar otras opciones de configuración de seguridad de la BIOS. 

### Hard Disk Password

Esta opción es una función de seguridad que permite establecer contraseñas para proteger el acceso a las unidades de almacenamiento.

![image15](/docs/img/image15.png)

Al entrar en la opción nos saldrá un menú de opciones:
- M.2 Drive 1 Password: Opción que nos dejará insertar una contraseña al M.2
- SATA Drive 1/2: Contraseña para las 2 unidades SATA que hay conectadas en el sistema. 
- Require HDP on System Boot: Opción que nos determinará si se solicitará la contraseña del disco duro al iniciar el sistema.

![image16](/docs/img/image16..png)

### Password Policies

Esta opción es un conjunto de reglas  y opciones que determinan cómo se manejan y aplican contraseñas en algunos parámetros.

![image17](/docs/img/image17.png)

Podemos ver opciones interesantes como: 
- BIOS Password At Reboot: determinará si pedirá la contraseña de la BIOS cuando se reinicie el sistema.
- BIOS Password At Boot Device List: controla si se quiere la contraseña de la BIOS para acceder a la lista de dispositivos de arranque cuando inicias el equipo. 

![image18](/docs/img/image18.png)