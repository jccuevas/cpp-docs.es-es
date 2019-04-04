---
title: Proyectos de CMake en Visual Studio
ms.date: 03/27/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 479179d94a0534f5f0c790fea18e281053b686e2
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565300"
---
# <a name="cmake-projects-in-visual-studio"></a>Proyectos de CMake en Visual Studio

CMake es una herramienta de código abierto multiplataforma para definir procesos de compilación que se ejecutan en varias plataformas. En este artículo se da por hecho que está familiarizado con CMake. Puede obtener más información sobre esta herramienta en [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar el software con CMake).

In Visual Studio 2015, los usuarios de Visual Studio pueden usar un [generador CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) para generar archivos de proyecto de MSBuild que, después, el IDE usa para IntelliSense, exploración y compilación.

Visual Studio 2017 incluye compatibilidad enriquecida con CMake, incluidos [proyectos de CMake multiplataforma](../linux/cmake-linux-project.md). El componente **Herramientas de Visual C++ para CMake** usa la característica **Abrir carpeta** para habilitar el IDE para el consumo de archivos de proyecto de CMake (por ejemplo, CMakeLists.txt) directamente para los propósitos de IntelliSense y la exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, se genera un archivo de proyecto temporal y se pasa a msbuild.exe, pero nunca se carga para IntelliSense o con fines de exploración. Puede importar una caché de CMake existente; Visual Studio automáticamente extrae variables personalizadas y crea rellenada previamente **CMakeSettings.json** archivo. 

## <a name="installation"></a>Instalación

**Herramientas de Visual C++ para CMake** se instala de forma predeterminada como parte de la carga de trabajo de **desarrollo para el escritorio con C++** y de la carga de trabajo **desarrollo de Linux con C++**.

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Al seleccionar **Archivo | Abrir | Carpeta** para abrir una carpeta que contiene un archivo CMakeLists.txt, sucede lo siguiente:

- Visual Studio agrega un elemento de menú **CMake** al menú principal, con los comandos para ver y modificar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake.exe y genera opcionalmente la caché de CMake para la *configuración* predeterminada, que es Debug x86. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos CMakeLists.txt "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar, depurar) así como IntelliSense y la exploración de C++ están disponibles para todos los proyectos de CMake del área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Visual Studio usa un archivo denominado **CMakeSettings.json** para almacenar las variables de entorno u opciones de línea de comandos para Cmake.exe. **CMakeSettings.json** también permite definir y almacenar CMake varias configuraciones de compilación y cambiar fácilmente entre ellos en el IDE. 

En caso contrario, use el **CMakeLists.txt** tal como se haría en cualquier proyecto de CMake para especificar archivos de origen, buscar bibliotecas, establecer opciones de compilador y vinculador y especificar otro sistema de compilación relacionados con la información.

Si necesita pasar argumentos a un archivo ejecutable en tiempo de depuración, puede usar otro archivo denominado **launch.vs.json**. En algunos escenarios, Visual Studio generará automáticamente estos archivos, que se pueden editar manualmente. También puede crear el archivo usted mismo.

> [!NOTE]
> Para otros tipos de proyectos de la carpeta abierta, se utilizan dos archivos adicionales de JSON: **CppProperties.json** y **tasks.vs.json**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="import-an-existing-cache"></a>Importar una caché existente

Cuando se importa un archivo CMakeCache.txt existente, Visual Studio extrae las variables personalizadas de manera automática y crea un archivo **CMakeSettings.json** previamente rellenado basado en ellas. La caché original no se modifica de ninguna manera y se puede seguir usando desde la línea de comandos o con cualquier herramienta o IDE que se usara para generarla. El nuevo **CMakeSettings.json** archivo se coloca junto con la raíz del proyecto CMakeLists.txt. Visual Studio genera una caché nueva en función del archivo de configuración. La generación automática de caché se puede invalidar en el cuadro de diálogo **Herramientas | Opciones | CMake | General**.

No se importa todo el contenido de la caché.  Propiedades como el generador y la ubicación de los compiladores se reemplazan con valores predeterminados que se sabe que funcionan de manera correcta con el IDE.

### <a name="to-import-an-existing-cache"></a>Para importar una caché existente

1. En el menú principal, seleccione **Archivo | Abrir | CMake**:

   ![Abrir CMake](media/cmake-file-open.png "Archivo, Abrir, CMake")

   Se abrirá el asistente **Importar proyecto CMake de la memoria caché**.

2. Navegue hasta el archivo CMakeCache.txt que quiere importar y después haga clic en **Aceptar**. Se abrirá el asistente **Importar proyecto CMake de la memoria caché**:

   ![Importar una caché CMake](media/cmake-import-wizard.png "Abrir el Asistente para importar la caché de CMake")

   Cuando se complete el asistente, verá el archivo CMakeCache.txt nuevo en el **Explorador de soluciones** junto al archivo CMakeLists.txt raíz del proyecto.

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas en General, busque el **configuraciones** desplegable; probablemente se muestra "Linux-Debug" o "x64-Debug" de forma predeterminada. Seleccione la configuración deseada y presione **F5**, o haga clic en el **ejecutar** botón (triángulo verde) en la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en CMakeLists.txt y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. en el menú principal, seleccione **Compilar | Compilar solución** (**F7** o **Ctrl+Mayús+B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando Compilar del menú de CMake](media/cmake-build-menu.png "Comando Compilar del menú de CMake")

Puede personalizar las configuraciones de compilación, las variables de entorno, los argumentos de línea de comandos y otras opciones sin modificar el archivo CMakeLists.txt mediante el **CMakeSettings.json** archivo. Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "CMake build errors")

En una carpeta con varios destinos de compilación, puede elegir el elemento **Generar** del menú **CMake** o el menú contextual de **CMakeLists.txt** para especificar qué destino de CMake se va a compilar. Al presionar **Ctrl+Mayús+B** en un proyecto de CMake se compila el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija la configuración deseada y presione **F5**, o bien presione el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón Ejecutar de CMake](media/cmake-run-button.png "Botón Ejecutar de CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

Puede personalizar un CMake a la sesión de depuración estableciendo propiedades en el **launch.vs.json** archivo. Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).


## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo CMakeLists.txt, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado de color amarillo y le informa de que IntelliSense se va a actualizar, y le da la oportunidad de cancelar la operación de actualización. Para obtener información sobre CMakeLists.txt, vea la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición de archivos CMakeLists.txt](media/cmake-cmakelists.png "CMakeLists.txt file editing")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **Lista de errores** para navegar a la línea incorrecta en CMakeLists.txt.

   ![Errores de archivos CMakeLists.txt](media/cmake-cmakelists-error.png "CMakeLists.txt file errors")


## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios significativos en el **CMakeSettings.json** o a archivos CMakeLists.txt, Visual Studio automáticamente vuelve a ejecutar el CMake el paso de configuración. Si el paso de configuración finaliza sin errores, la información que se recopila está disponible en IntelliSense de C++ y los servicios de lenguaje, y también en las operaciones de compilación y depuración.

Cuando varios proyectos de CMake usan el mismo nombre de configuración de CMake (por ejemplo, x86-Debug), todos se configuran y compilan (en su propia carpeta raíz de compilación) al seleccionar esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en esa configuración de CMake.

   ![Elemento de menú Solo compilación de CMake](media/cmake-build-only.png "CMake Build Only menu item")

Para limitar las compilaciones y depurar las sesiones para un subconjunto de los proyectos en el área de trabajo, crear una nueva configuración con un nombre único en la **CMakeSettings.json** de archivos y aplicarla a solo los proyectos. Al seleccionar esa configuración, los comandos de IntelliSense y de compilación y depuración se habilitan solo para los proyectos especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **CMake** o el menú contextual de **CMakeLists.txt** en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo CMakeCache.txt desde la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para CMakeCache.txt se borra si limpia la caché. Para realizar cambios que se conservan cuando se limpia la memoria caché, consulte [CMake Personalizar configuración](customize-cmake-settings.md).)

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza la ejecución del paso de generación aunque Visual Studio considere que el entorno está actualizado.

La generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas | Opciones | CMake | General**.

## <a name="single-file-compilation"></a>Compilación de archivo único

Para compilar un único archivo en un proyecto de CMake, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y elija **Compilar**. También puede compilar el archivo que esté actualmente abierto en el editor, usando para ello el menú principal de CMake:

![Compilación de archivo único de CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Vea [Compilar en la línea de comandos](building-on-the-command-line.md) para obtener más información.

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.
  
## <a name="see-also"></a>Vea también

[Tutorial: Creación de proyectos multiplataforma de C++ en Visual Studio](get-started-linux-cmake.md)<br/>
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)<br/>
[Referencia de CMakeSettings.json](cmakesettings-reference.md)<br/>
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)<br/>
