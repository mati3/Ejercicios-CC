# Desarrollo basado en pruebas

### 1º Ejercicio:

***Instalar alguno de los entornos virtuales de node.js (o de cualquier otro lenguaje con el que se esté familiarizado) y, con ellos, instalar la última versión existente, la versión minor más actual de la 4.x y lo mismo para la 0.11 o alguna impar (de desarrollo).***

Para este ejercicio vamos a usar una máquina virtual con Ubuntu-16, hemos generado un script:

![img](/img/Desarrollo_basado_en_pruebas/ejer1_script.png)

    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
Descarga el script de instalación de nvm desde github.       

    export NVM_DIR="${HOME}/.nvm"                            
Carga la función nvm en nuestro shell.

    [ -s "${NVM_DIR}/nvm.sh" ] && . "${NVM_DIR}/nvm.sh"                        
Configura nuestra versión por defecto de node a la última release.

    [ -s "${NVM_DIR}/bash_completion" ] && . "${NVM_DIR}/bash_completion" 
Ajusta las variables de entorno a nuestro perfil bash.

    nvm install 0.11.0 
Instalar la release determinada.

    nvm use 0.11.0 
Usar la version determinada.


Despues de haberlo ejecutado hay que reiniciar el sistema para poder usar nvm.

Nosotros vamos a instalar el entorno virtual para ruby "RVM", para ello seguimos los [siguientes pasos](https://github.com/rvm/ubuntu_rvm):

    sudo apt-get install software-properties-common
    sudo apt-add-repository -y ppa:rael-gc/rvm
    sudo apt-get update
    sudo apt-get install rvm
    reboot
    rvm install ruby

### 2º Ejercicio:

***Crear una descripción del módulo usando package.json. En caso de que se trate de otro lenguaje, usar el método correspondiente.***

Vamos a usar ruby, Bundle es un manejador de dependencias para este lenguaje. En ruby a las librerías se les conoce como gemas, Bundle nos ayuda a agrupar cada una de las gemas que necesitamos para nuestro proyecto así como las versiones de las mismas.
Esto nos ayudará en el caso de que tengamos varios proyectos que necesiten versiones diferentes de las mismas gemas o en caso de que queramos cambiar de máquina. 
Pero a su vez Bundle es tambien una gema, asi que lo primero es instalarla.

    gem insall bundler

Para definir las dependencias de nuestro proyecto creamos un archivo llamado Gemfile donde vamos a poner las gemas de las que dependerá nuestro proyecto.

Incluimos el archivo a nuestro proyecto y lo explicamos con mas detalle en el mismo.


### 3º Ejercicio:

***Descargar el repositorio de ejemplo anterior, instalar las herramientas necesarias (principalmente Scala y sbt) y ejecutar el ejemplo desde sbt. Alternativamente, buscar otros marcos para REST en Scala tales como Finatra o Scalatra y probar los ejemplos que se incluyan en el repositorio.***

    git clone https://github.com/JJ/spray-test.git

Instalamos sbt, tenemos para pruebas el sistema ubuntu-16:

    wget http://apt.typesafe.com/repo-deb-build-0002.deb
    sudo dpkg -i repo-deb-build-0002.deb
    sudo apt-get update
    sudo apt-get install sbt

Tengo que instalar java8 para poder usarlo:

Primero compruebo las versiones que tengo instaladas:

    update-java-alternatives --list

Instalo la version que necesito

    sudo apt install openjdk-8-jdk

Pongo por defecto java 8

    sudo update-java-alternatives --set /usr/lib/jvm/java-1.8.0-openjdk-amd64

Seguimos las instrucciones del enlace del [repositorio](https://github.com/JJ/spray-test), y obtenemos las siguientes salidas:

![img](/img/Desarrollo_basado_en_pruebas/ejer3_localhost.png)

![img](/img/Desarrollo_basado_en_pruebas/ejer3_curl.png)

### 4º Ejercicio:

***Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga. A continuación, ejecutarlos desde mocha (u otro módulo de test de alto nivel), usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vamos a necesitar un poco más adelante.***


![img](/img/Desarrollo_basado_en_pruebas/ejer1_script.png)

![img](/img/Desarrollo_basado_en_pruebas/ejer4_producto.png)

![img](/img/Desarrollo_basado_en_pruebas/ejer4_test.png)

![img](/img/Desarrollo_basado_en_pruebas/ejer4_ruby_test.png)

Instalo [rspec](https://github.com/rspec/rspec) que es el módulo de test de alto nivel para Ruby.

![img](/img/Desarrollo_basado_en_pruebas/ejer4_rspec.png)

![img](/img/Desarrollo_basado_en_pruebas/ejer4_test_rspec.png)