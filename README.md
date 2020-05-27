Este ejemplo intenta demostrar que se puede crear de manera sencilla
interfaces gráficas portables del siglo XXI en C/++ haciendo que el código
fuente agregado a un sistema de versiones sea liviano y usando las ventajas de
un gestor de paquetes para C.

Para ello este ejemplo se apoya en CONAN:

Si deseas instalarlo debes utilizar pip:

pip install conan

Una vez que tengas todo funcionando es importante seguir los pasos

1. Añadir un repositorio con las dependencias necesarias:

conan remote add bincrafters https://api.bintray.com/conan/bincrafters/public-conan

2. Compilar y generar las dependencias para nuestro programa con la configuración óptima

conan install . -s build_type=Release --build missing

3. Generar los makefiles o archivos de configuración para compilar y linkar:

cmake .

4. Compilar:

make

5. Ejecutar (en la carpeta bin):

./bin/opengl-gui
