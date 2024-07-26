# Guía para la construcción del entorno de desarrollo de código abierto para la FPGA Tang Nano 9k

## Instalación de Visual Studio Code

Se utilizará VSCode como editor de texto y para alojar todo el proceso de diseño, pruebas e implementación física en la FPGA. Puede descargarlo [aquí](https://code.visualstudio.com/?ref=learn.lushaylabs.com).

## Instalación de la extensión Lushay Code

Al abrir `VSCode`, encontrará la sección de extensiones en la columna izquierda, como se muestra en la siguiente imagen:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/79e61e72-a827-4524-901f-9d4885579684" alt="Extensiones en VSCode">
</div>

Dentro de las extensiones, busque *Lushay Code* en el cuadro de búsqueda y haga clic en "Instalar", como se indica en la siguiente imagen:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/09cbabf7-c5e2-4d54-afe1-2bf6fd92153b" alt="Instalación de Lushay Code en VSCode">
</div>

## Instalación de otras extensiones necesarias

De manera similar a la instalación de *Lushay Code*, instale *Verilog-HDL/SystemVerilog*. Puede descargarla directamente desde: [*Verilog-HDL/SystemVerilog*](https://marketplace.visualstudio.com/items?itemName=mshr-h.VerilogHDL).

## Instalación del OSS-Cad-Suite de YosysHQ

Para instalar las herramientas necesarias en todo el proceso de diseño, pruebas e implementación, descargue el paquete *OSS-Cad-Suite* desde el siguiente enlace. Guárdelo en la ubicación que desee (esta ubicación será necesaria más adelante).
- Windows: [Descargar aquí](https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2023-02-10/oss-cad-suite-windows-x64-20230210.exe)
- Otros sistemas operativos: [Descargar aquí](https://github.com/YosysHQ/oss-cad-suite-build/releases/tag/2023-02-10)

Si usa Windows, al abrir el archivo descargado, es posible que aparezca la siguiente advertencia:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/2d0b9cde-dacb-492c-9e4c-e345ffae0d47" alt="Advertencia en la instalación de OSS-Cad-Suite">
</div>

Presione "Más Información" y luego "Ejecutar de todas formas". Esto extraerá los archivos en una carpeta llamada *oss-cad-suite* en la misma ubicación:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/1912a6b0-4456-4505-aa0f-7f6ffd1ad383" alt="Carpeta oss-cad-suite">
</div>

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/b98360c3-8f59-4b69-b145-55583405efad" alt="Carpeta oss-cad-suite (continuación)">
</div>

## Configuración de la extensión Lushay Code

Abra VSCode, en la parte inferior derecha, haga clic en *FPGA Toolchain*:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/b2637e91-6d59-418a-93b6-c539bbe86150" alt="Configuración de la extensión Lushay Code">
</div>

Aparecerá un error y la opción "Setup Now". Al hacer clic, seleccione la carpeta *bin* dentro de la carpeta *oss-cad-suite* que extrajo.

Otra forma es abrir la extensión *Lushay Code*, ir a la configuración:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/4cf5da3f-2eb2-4b3a-83fe-7027d2aeec33" alt="Configuración de Lushay Code en VSCode">
</div>



<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/6507ecf2-ee39-4054-b985-2dd4da61f5b0" alt="Configuración de Lushay Code en VSCode (continuación)">
</div>

Allí, copie la ruta de la carpeta *bin* dentro de la carpeta *oss-cad-suite* en la ubicación que la guardó. Preferiblemente, esta ruta no debe contener espacios ni caracteres especiales:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/45d7ba05-c810-4754-b08e-f4b2ba9ee29d" alt="Carpeta bin en oss-cad-suite">
</div>

Y pegue esa ruta en la sección de *OSS Cad Suite* en la configuración de la extensión:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/e4f9123f-43c1-4325-b11c-97d4d493566b" alt="Configuración de OSS Cad Suite en Lushay Code">
</div>

## Configuración del Driver USB de Windows

Es necesario modificar el controlador USB de Windows para programar la FPGA con *openFPGALoader*. Para esto, instale el programa [Zadig](https://zadig.akeo.ie/).

Al instalarlo y abrirlo, se mostrará la ventana del programa. Después de conectar la FPGA al puerto USB de la computadora, vaya a "Options" y seleccione "List All Devices":

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/85d18255-bb6e-47f6-8d67-3f7e984f2c5b" alt="Opciones en Zadig">
</div>

Luego, seleccione *JTAG Debugger (Interface 0)*:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/2928a4d8-e7e8-4674-9c74-79e14b96c281" alt="Seleccionar JTAG Debugger en Zadig">
</div>

Presione "Replace Driver" y espere a que se complete la acción:

<div align="center">
  <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/6ef1fe2f-d0d9-4731-a443-82e645a95f80" alt="Reemplazar el controlador en Zadig">
</div>

## Instalación de GNU-Make

En esta sección se instalará Make para automatizar los comandos de consola que se puedan necesitar en la elaboración de proyectos.

- Para instalar Make haga click [aquí](https://gnuwin32.sourceforge.net/downlinks/make.php)

Ejecute el archivo descargado y acepte los términos:

![alt text](image.png)

Seleccione la ruta donde se instalará:

![alt text](image-2.png)

Y acepte en todas las ventanas:

![alt text](image-1.png)



### Agregar Make al Path

Para ejecutar la aplicación desde cualquier proyecto en la consola de VSCode, es necesario agregar la carpeta `bin` que está dentro de la carpeta `GnuWin32` que acaba de instalar a la variable de entorno PATH.

1. **Copie la ruta de la carpeta `bin`:** esta se encuentra en la ruta que seleccionó para la instalación de Make.

    ![alt text](image-3.png)

1. **Edite las variables de entorno del sistema:**
   
   Busque en el cuadro de búsqueda de Windows *variables de entorno*:

   <p align="center">
     <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/19d09880-5d3c-455e-966a-b381a101090f" alt="Buscar variables de entorno">
   </p>

2. **Ingrese al editor de variables de entorno y presione *Variables de entorno...*:**
   
   <p align="center">
     <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/d29bbac5-9c8f-4fff-9fea-af05853882aa" alt="Editor de variables de entorno">
   </p>

3. **Seleccione *Path* y presione *Editar*:**
   
   <p align="center">
     <img src="https://github.com/DJosueMM/open_source_fpga_environment/assets/81501061/a885a522-3758-4e57-bd0e-a6fc692f0e8a" alt="Editar Path">
   </p>

4. **Presione *Nuevo* y pegue la ruta a la carpeta `bin` que copió anteriormente. Finalmente, presione Aceptar en cada ventana.**

    ![alt text](image-4.png)

Con esto se da por concluida la guía de instalación de herramientas, puede continuar con la siguiente guía:  

# Referencias
Esta guía está basada en el siguiente documento: [Getting Setup with the Tang Nano 9k](https://learn.lushaylabs.com/getting-setup-with-the-tang-nano-9k/).


## Ultima actualización:
- David Medina
- 25-07-2024.