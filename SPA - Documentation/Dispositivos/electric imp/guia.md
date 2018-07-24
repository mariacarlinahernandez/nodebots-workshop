# Requerimientos

* Electric [Imp 001](https://store.electricimp.com/products/imp001?variant=31635697938) + [April Development Board](https://developer.electricimp.com/hardware/resources/reference-designs/april)
* Cuenta en impCentral - Electric Imp
* Cuenta en Twitter
* Twitter App
* (1) Sensor de ultrasonido (HC-SR04)
* (1) LED
* (1) Resistencia de 330k ohm
* Cables para conexiones
* Cable USB

# Paso a Paso

1. Configuración de Hardware
2. Configuración de Software
2.1. impCentral
2.2. Twitter App
3. Mundo físico con el mundo digital
4. Resultados

# 1. Configuración de Hardware

1. Inserta el [**imp 001**](https://store.electricimp.com/products/imp001?variant=31635697938) en la board [**April**](https://developer.electricimp.com/hardware/resources/reference-designs/april).

Una vez el módulo se encuentre conectado al board de desarrollo, se deben realizar las conexiones con el sensor. En esta guía utilizaremos un [**sensor de ultrasonido**](https://es.wikipedia.org/wiki/Sensor_ultras%C3%B3nico), pero eso no quiere decir que en caso de tener otro sensor no puedas llevar a cabo el desarrollo de la esta guia. En este caso, tan solo debes asignar las configuraciones necesarias para el sensor a utilizar y enviar la lectura tomada del mismo.

2. Usando los cables para conexiones, establece las conexiones entre el **sensor de ultrasonido** y la **board** de desarrollo. Para establecer las conexiones sigue la tabla a continuación:

| Imp Devp Board|    HC-SR04  |
| ------------- |-------------|
|      VIN      |      VCC    |
|     PIN9      |     Trig    |
|     PIN8      |     Echo    |
|      GND      |      GND    |


3. Connecta uno de los extremos del cable USB a la board, y el otro extremo a el computador para energizar la placa.



# 2. Configuración de Software

La mejor manera de familiarizarse con el Entorno de Electric Imp (Hardware & Software) es siguiendo su [**Guía de Inicio**](https://developer.electricimp.com/gettingstarted/generic). De todos modos, a continuación detallaremos los pasos básicos para construir y desplegar tu primera aplicacion utilizando Electric Imp & Twitter.

Para comenzar, crea una [cuenta gratis en Electric Imp](https://impcentral.electricimp.com/login).

## 2.1. impCentral

### Activa y Conecta el Imp Dev Board

1. Para programar el dispositivo de Electric Imp, necesitas registrarlo en una cuenta de Electric Imp. Para registrar el dispositivo en tu cuenta de Electric Imp debes hacer uso de la herramienta **BlinkUp**.

El proceso de **BlinkUp** se puede llevar a cabo en dos maneras, 1) Utilizando el **impCentral** o 2) Utilizando la **App de Electric Imp**:

#### BlinkUp desde impCentral

1. Desde el impCentral, selecciona el tercer icono ubicado en la parte izquierda de la plataforma para ingresar a **"Account Development Devices"**.

![account development devices](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/account-development-devices.png?raw=true)

2. Selecciona **"BlinkUp"** desde el centro de la página:

![blinkup](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/blinkup.png?raw=true)

3. La siguiente ventana es la encargada the conectar la tarjeta de Electric Imp a la red deseada. Asigna las credenciales de la red deseada a conectarse (**SSID y Contraseña**) para establecer la conexión con el dispositivo.

![setup wifi](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/setup-wifi.png?raw=true)

Para terminar, presiona **"BlinkUp"**.

4. En este punto, la ventana a continuación aparecerá. Para activar la tarjeta, posiciona la parte frontal de la Electric Imp board sobre la pantalla del computador.

**NOTA**: Este proceso tomará un poco de minutos, así que sea paciente 💻💛

![impCentral BlinkUp](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/ElectricImp-BlinkUp.gif?raw=true)

Una vez la conexión se haya establecido correctamente debería recibir un mensaje satisfactorio **"Device is connected"**

![blinkup](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/blinkup-connected.png?raw=true)

#### BlinkUp desde Electric Imp App

1. Dependiendo del sistema operativo de tu teléfono móvil, descarga la **aplicación de Electric Imp**:

* [Google Play](https://play.google.com/store/apps/details?id=com.electricimp.electricimp)
* [Apple Store](https://itunes.apple.com/co/app/electric-imp/id547133856?mt=8)

2. Luego de finalizar la instalación, sigue cuidadosamente los pasos proporcionados en la aplicación. El video a continuación muestra un ejemplo de cómo llevar a cabo el **BlinkUp** desde la aplicación móvil:

[![BlinkUp Video](http://img.youtube.com/vi/0lW0_MfBtU/0.jpg)](https://www.youtube.com/watch?v=-0lW0_MfBtU)

Ahora tu dispositivo de Electric Imp se encuentra activado correctamente, y conectado a la red asignada durante en proceso de activación.

### Programando el Electric Imp

Con el dispositivo conectado y activado, es momento de asignarlo a un grupo para así poder desarrollar nuestras aplicaciones en el.

En primer momento el dispositivo debería estar como **"unassigned"**, es decir que el dispositivo no se encuentra asociado a ningún **Grupo de Dispositivos**. Para asignar el dispositivo a un grupo de dispositivos sigue los pasos a continuación:

**NOTA IMPORTANTE**: Para una explicacion mas detallada de como funciona el impCentral para desarrollos a grande escala, haga referencia a el paso "Programming Your Imp Kit" de esta [guia](https://developer.electricimp.com/gettingstarted/generic)

1. Para comenzar, crea un **producto**; el producto es el primer nivel para el contendor del proyecto. Para crearlo, solo presiona **"Create Product"**:

![save product](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/save-product.png?raw=true)

2. Luego, en la siguiente ventana asigna el **nombre** deseado para el **producto**. También, debes asignar el **nombre** del **"Development Device Group"** para crearlo.

¿Cómo funciona **"Device Groups"**? Bueno, todos los dispositivos que se encuentran asignados a un mismo Device Group correrán el mismo código asignado al respectivo grupo. Esto es de gran utilidad cuando se desea hacer despliegue de múltiple de dispositivos.

Para esta guia asignaremos **"NodeBots"** como nombre de producto, y **"enviar tweet"** cómo Development Device Group. Tal cual se muestra a continuación:

![product creation](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/product-creation.png?raw=true)


Para guardar los cambios realizados, presione el botón azul "Create". Una vez presionado, recibirás un mensaje satisfactorio.

4. Ahora con el producto ya creado y configurado es hora de asignar los dispositivos deseados al producto. Para asignar el dispositivo, presiona el botón azul **"Assign Devices"** ubicado en la parte baja de la página:

![assign device](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/assign-device.png?raw=true)


Selecciona el dispositivo(s) deseado a desplegar:

![assign device 1](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/assign-device-1.png?raw=true)

Luego, los dispositivo(s) asignados deberán aparecer en la parte baja izquierda de la página

![assign device 2](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/assign-device-2.png?raw=true)

7. Ahora, todo se encuentra configurado para comenzar a programar el dispositivo Electric Imp para hablar con otros servicios. Antes de comenzar verifiquemos el workflow del impCentral:

* **Agent code**: Este se ejecuta en el imp cloud, no en el dispositivo. Los agentes se ejecutan continuamente, permitiendo que los dispositivos sean accesibles incluso si están durmiendo para ahorrar energía. El agente puede verificar el estado del dispositivo y retener cualquier dato recibido hasta que el dispositivo esté nuevamente despierto.

* **Device code**: Este código se ejecutará en su dispositivo. Aquí es donde normalmente administra los pines de entradas / salidas que conectan el kit imp al mundo real.

* **Log window**: Le proporciona los registros en tiempo real del comportamiento presentado en el imp kit utilizado.

![imp central](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/impcentral.png?raw=true)

Para obtener una explicación detallada de impCentral, visite la página de [documentación de Electric Imp](https://developer.electricimp.com/gettingstarted/explorer/agents).

## 2.2. Twitter App

1. Para poder realizar el envío de tweets a una cuenta en especifica, se necesita crear una **"Twitter App"**. Para crear la aplicacion, selecciona el siguiente [link](https://apps.twitter.com/).

2. Selecciona **"Create New App"**

3. Luego, en la ventana a continuación completa los campos vacíos con la información requerida:

![twitter app creation](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/twitter-app-creation.png?raw=true)

Una vez la aplicación se cree correctamente, deberás tener acceso a la siguiente ventana:

![twitter app](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/twitterapp.png?raw=true)

4. Ahora con la aplicación creada, debes tener acceso a las llaves necesarias para poder establecer la comunicación desde nuestro dispositivo. Para verificar que tienes el acceso, dirígete a la pestaña "**Keys and Access Tokens**".

![twitter keys](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/twitter-keys.png?raw=true)

Estas credenciales deben ser asignadas posteriormente en el código a cargar en el dispositivo.

# 3. Mundo físico con el mundo digital

En este punto es donde programaremos nuestro dispositivo el cual se encargará de tomar los valores de las variables deseas en el mundo físico para luego guardar esas lecturas y enviarlas a un servicio en la nube, como lo es en este caso twitter.

1. Copia el codigo a continuacion, luego pegalo en la sección del **Agent code**:

```javascript
#require "Twitter.agent.lib.nut:2.0.0"

const API_KEY = "Assign_Twitter_API_KEY";
const API_SECRET = "Assign_Twitter_API_SECRET";
const AUTH_TOKEN = "Assign_Twitter_AUTH_TOKEN";
const TOKEN_SECRET = "Assign_Twitter_TOKEN_SECRET";

twitter <- Twitter(API_KEY, API_SECRET, AUTH_TOKEN, TOKEN_SECRET);

device.on("distance", function(value){
   // add logic to send tweets
   if (value < 10) {
       //server.log("Mi gato esta cerca del comedero! value: " +  value);       
       //twitter.tweet("Mi gato esta cerca del comedero! value: " +  value);
   } else {
       //server.log("Tweet posted - out: " +  value);       
       //twitter.tweet("...");
   }
});
```

2. Copia el codigo a continuacion, luego pegalo en la sección del **Device code**:

```javascript
// Ultrasonic Range Sensor HC-SR04
// https://docs.google.com/document/d/1Y-yZnNhMYy7rwhAgyL_pfa39RsB-x2qR4vP8saG73rE/edit
class HCSR04 {
   // consts
   static TO = 500; // timeout in ms
  
   // pins
   _trig   = null;
   _echo   = null;

   // aliased methods
   _tw     = null;
   _er     = null;
   _hu     = null;
   _hm     = null;

   // vars
   _es     = null; // echo start time
   _ee     = null; // echo end time

   constructor(trig, echo) {
       _trig = trig;
       _echo = echo;

       _hu   = hardware.micros.bindenv(hardware);
       _hm   = hardware.millis.bindenv(hardware);
       _tw   = _trig.write.bindenv(_trig);
       _er   = _trig.read.bindenv(_echo);
   }

   function read_cm() {
       local st = _hm(); // start time for timeout
       // Quickly pulse the trig pin
       _tw(0); _tw(1); _tw(0);

       // Wait for the rising edge on echo
       while (_er() == 0 && (_hm() - st) < TO);
       _es = _hu();

       // Time to the falling edge on echo
       while (_er() == 1 && (_hm() - st) < TO);
       _ee = _hu();

       //if ((_hm() - st) >= TO) return -1;
       return (_ee - _es)/58.0;
   }
}

// Ex Usage
trig <- hardware.pin9;
echo <- hardware.pin8;

trig.configure(DIGITAL_OUT,0);
echo.configure(DIGITAL_IN);

range <- HCSR04(trig, echo);

function mainLoop() {
   local distance = range.read_cm();
   agent.send("distance", distance);
   imp.wakeup(1.0, mainLoop);
}

mainLoop();
```

3. Una vez los códigos se encuentren en el impCentral, debes actualizar los **keys** y **tokens** relacionadas a la **Twitter App** previamente creada. Teniendo como resultado algo parecido a:

* **Antes de ser actualizado:**

```javascript
const API_KEY = "Assign_Twitter_API_KEY";
const API_SECRET = "Assign_Twitter_API_SECRET";
const AUTH_TOKEN = "Assign_Twitter_AUTH_TOKEN";
const TOKEN_SECRET = "Assign_Twitter_TOKEN_SECRET";
```

* **Después de ser actualizados:**

```javascript
const API_KEY = "Tox8rt0In8Tox8rt0In8t0In8";
const API_SECRET = "zHL9IH8N0LzHL9IH8N0LKO9kGhgCAL8GRzHL9IH8N0L7yH0L7";
const AUTH_TOKEN = "99622622-IiTF8qgrrTIiTF8qgrBJ9YNSNDde1QmDPlRr1ioa5";
const TOKEN_SECRET = "rrTIiTF8qgdwS7FQfYf9t2XSSKFwVjS7FQfYf9t2X0WQ";
```

4. Con las credenciales actualizadas, debe verificar si los códigos incluidos están en el formato correcto. Para verificar el código, simplemente presione el botón **"Check"**.

![check code imp](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/check-code.png?raw=true)

5. Con el código verificado, es hora de correr el código en el dispositivo Electric Imp. Para correr y descargar el código, debes presionar el botón "Build and Force Reset"

![build code imp](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/build-save-code.png?raw=true)

6. Una vez el código se haya subido correctamente podrás observar los registros con el valor actual del sensor junto al registro del tweet a enviar.

8. Accede en la cuenta de twitter en la cual fue creada la **Twitter App** y observa los tweets recientemente enviados.

Como pudieron observar, luego de seguir los pasos mencionados anteriormente fuimos capaces de conectar el mundo físico con el mundo digital. El sensor de ultrasonido se encarga de tomar lecturas del mundo físico (las cuales son  útiles distintos casos de uso) mientras que el dispositivo de Electric Imp analiza las lecturas del sensor, y realiza el envío de la misma a Twitter por medio de una API.

![tweet](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/tweet.png?raw=true)

# Resultados

En mi caso, decidí hacer uso del sensor para saber cuando mi gata se encuentra cerca del comedero. Esto me ayudará a monitorear las veces que se acerca a el comedero y para cerciorarme que se está alimentando correctamente. Para hacer una aplicación de otra escala con el mismo fin, se deberían agregar más sensores que me permitan saber no tan solo si el gato se acerco a el comedero, si no que también nos permita conocer la cantidad exacta de comida que comió o hasta la cantidad de agua.


![comedero](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/comedero.jpeg?raw=true)

![comedero y bagheera](https://github.com/mariacarlinahernandez/nodebots-workshop/blob/master/Images/comedero-bagheera.jpeg?raw=true)


