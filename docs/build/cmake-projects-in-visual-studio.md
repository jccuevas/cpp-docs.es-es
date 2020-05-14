---
title: Proyectos de CMake en Visual Studio
description: Cómo crear y compilar proyectos de C++ mediante CMake en Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329157"
---
# <a name="cmake-projects-in-visual-studio"></a>Proyectos de CMake en Visual Studio

CMake es una herramienta de código abierto multiplataforma para definir procesos de compilación que se ejecutan en varias plataformas. En este artículo se da por hecho que está familiarizado con CMake. Puede obtener más información sobre esta herramienta en [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar el software con CMake).

> [!NOTE]
> CMake se ha integrado cada vez más con Visual Studio en las últimas versiones. Para ver la documentación de su versión preferida de Visual Studio, use el control de selector **Versión**. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

El componente **Herramientas de CMake en C++ para Windows** usa la característica [Abrir carpeta](open-folder-projects-cpp.md) para el consumo de archivos de proyecto de CMake (por ejemplo, *CMakeLists.txt*) directamente para los propósitos de IntelliSense y la exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, se genera un archivo de proyecto temporal y se pasa a msbuild.exe. Sin embargo, el proyecto no se carga nunca con fines de exploración o de IntelliSense. También puede importar una caché de CMake existente.

## <a name="installation"></a>Instalación

El componente **Herramientas de CMake en C++ para Windows** se instala como parte de las cargas de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo de Linux con C++** . Para obtener más información, consulte el artículo sobre [proyectos multiplataforma de CMake](../linux/cmake-linux-project.md).

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install-2019.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Al seleccionar **Archivo > Abrir > Carpeta** para abrir una carpeta que contiene un archivo *CMakeLists.txt*, sucede lo siguiente:

- Visual Studio agrega elementos de **CMake** al menú **Proyecto**, con comandos para ver y editar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta cmake.exe y genera el archivo de caché de CMake (*CMakeCache.txt*) para la configuración predeterminada (x64 Debug). La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos *CMakeLists.txt* "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar y depurar), C++ IntelliSense y la exploración están disponibles para todos los proyectos de CMake del área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Haga clic en el botón **Mostrar todos los archivos** en la parte superior del **Explorador de soluciones** para ver todos los resultados generados por CMake en las carpetas *out/build/\<config>* .

Visual Studio usa un archivo de configuración denominado **CMakeSettings.json**. Este archivo le permite definir y almacenar varias configuraciones de compilación y cambiar fácilmente entre ellas en el IDE. Una *configuración* es una construcción de Visual Studio que encapsula valores específicos de un tipo de compilación determinado. Estos valores se usan para configurar las opciones predeterminadas de la línea de comandos que Visual Studio pasa a cmake.exe. También puede especificar aquí opciones adicionales de CMake y definir las variables adicionales que quiera. Todas las opciones se escriben en la caché de CMake como variables internas o externas. En Visual Studio 2019, el **Editor de configuración de CMake** proporciona una manera cómoda de editar la configuración. Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Un valor, `intelliSenseMode` no se pasa a CMake, sino que solo lo usa Visual Studio.

Use el archivo **CMakeLists.txt** en cada carpeta del proyecto tal como lo haría en cualquier proyecto de CMake. Puede especificar archivos de código fuente, buscar bibliotecas, establecer opciones del compilador y del enlazador, y especificar otra información relacionada con el sistema de compilación.

Para pasar argumentos a un archivo ejecutable en tiempo de depuración, puede usar otro archivo denominado **launch.vs.json**. En algunos escenarios, Visual Studio genera automáticamente estos archivos. Puede editarlos manualmente o incluso crearlos usted mismo.

> [!NOTE]
> Para otros tipos de proyectos Abrir carpeta, se usan dos archivos JSON adicionales: **CppProperties.json** y **tasks.vs.json**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="open-an-existing-cache"></a>Apertura de una caché existente

Al abrir un archivo de caché de CMake existente (*CMakeCache.txt*), Visual Studio no intenta administrar la caché y el árbol de compilación automáticamente. Las herramientas personalizadas o preferidas tienen un control completo sobre cómo CMake configura el proyecto. Para abrir una caché existente en Visual Studio, vaya a **Archivo > Abrir > CMake**. A continuación, navegue a un archivo *CMakeCache.txt* existente.

Puede agregar una caché de CMake existente a un proyecto abierto. Se hace de la misma manera que para agregar una nueva configuración. Para obtener más información, consulte nuestra entrada de blog sobre [cómo abrir una caché existente en Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas General, busque el menú desplegable **Configuraciones**. Probablemente muestra "x64-Debug" de forma predeterminada. Seleccione la configuración preferida y presione **F5**, o bien haga clic en el botón **Ejecutar** (el triángulo de color verde) en la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en *CMakeLists.txt* y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > Compilar todo** (**F7** o **Ctrl+Mayús+B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando del menú de compilación de CMake](media/cmake-build-menu.png "Menú de comandos de compilación de CMake")

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "Errores de compilación de CMake")

En una carpeta con varios destinos de compilación, puede especificar qué destino de CMake se va a compilar: Elija el elemento **Compilar** en el menú de **CMake** o en el menú contextual de *CMakeLists.txt* para especificar el destino. Si presiona **Ctrl+Mayús+B** en un proyecto de CMake, se compila el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija su configuración preferida y presione **F5**, o bien presione el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable. A continuación, elija el destino que quiere ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón Ejecutar de CMake](media/cmake-run-button.png "Botón Ejecutar de CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior. Los cambios en *CMakeSettings.json* hacen que se vuelva a generar la caché de CMake.

Puede personalizar una sesión de depuración de CMake mediante el establecimiento de las propiedades en el archivo **launch.vs.json**. Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="just-my-code-for-cmake-projects"></a>Solo mi código para proyectos de CMake

Cuando se compila para Windows mediante el compilador de MSVC, los proyectos de CMake admiten la característica de depuración Solo mi código. Para cambiar el valor de Solo mi código, vaya a **Herramientas** > **Opciones** > **Depuración** > **General**.

## <a name="vcpkg-integration"></a>Integración de vcpkg

Si ha instalado [vcpkg](vcpkg.md), los proyectos de CMake abiertos en Visual Studio integran automáticamente el archivo de cadena de herramientas de vcpkg. Esto significa que no se requiere ninguna configuración adicional para usar vcpkg con los proyectos de CMake. Esta compatibilidad funciona para las instalaciones locales de vcpkg y las instalaciones de vcpkg en sistemas remotos de destino. Este comportamiento se deshabilita automáticamente cuando se especifica cualquier otra cadena de herramientas en la configuración de los valores de CMake.

## <a name="customize-configuration-feedback"></a>Personalización de comentarios de configuración

De forma predeterminada, la mayoría de los mensajes de configuración se suprimen a menos que haya un error. Puede ver todos los mensajes habilitando esta característica en **Herramientas** > **Opciones** > **CMake**.

   ![Configuración de las opciones de diagnóstico de CMake](media/vs2019-cmake-configure-options.png "Opciones de diagnóstico de CMake")

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo *CMakeLists.txt*, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado de color amarillo y le informa de que IntelliSense se va a actualizar. Le ofrece la oportunidad de cancelar la operación de actualización. Para obtener información sobre *CMakeLists.txt*, vea la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición del archivo CMakeLists.txt](media/cmake-cmakelists.png "Edición del archivo CMakeLists.txt")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **Lista de errores** para navegar a la línea incorrecta en *CMakeLists.txt*.

   ![Errores del archivo CMakeLists.txt](media/cmake-cmakelists-error.png "Errores del archivo CMakeLists.txt")

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios importantes en los archivos *CMakeSettings.json* o *CMakeLists.txt*, Visual Studio vuelve a ejecutar de manera automática el paso de configuración de CMake. Si el paso de configuración finaliza sin errores, la información que se recopila está disponible en C++ IntelliSense y en los servicios de lenguaje. También se usa esta información en las operaciones de compilación y depuración.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **Proyecto** o el menú contextual de *CMakeLists.txt* en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo *CMakeCache.txt* desde la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para *CMakeCache.txt* se borra si limpia la caché. Para realizar cambios que se conserven después de limpiar la caché, vea [Personalización de la configuración de CMake](customize-cmake-settings.md)).

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza la ejecución del paso de generación aunque Visual Studio considere que el entorno está actualizado.

La generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas > Opciones > CMake > General**.

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Para obtener más información, vea el artículo sobre cómo [compilar en la línea de comandos](building-on-the-command-line.md).

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 incluye compatibilidad enriquecida con CMake, incluidos [proyectos multiplataforma de CMake](../linux/cmake-linux-project.md). El componente **Herramientas de Visual C++ para CMake** usa la característica **Abrir carpeta** para habilitar el IDE para el consumo de archivos de proyecto de CMake (por ejemplo, *CMakeLists.txt*) directamente para los propósitos de IntelliSense y la exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, se genera un archivo de proyecto temporal y se pasa a msbuild.exe. Sin embargo, el proyecto no se carga nunca con fines de exploración o de IntelliSense. También puede importar una caché de CMake existente.

## <a name="installation"></a>Instalación

El componente **Herramientas de Visual C++ para CMake** se instala como parte de las cargas de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo de Linux con C++** .

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Al seleccionar **Archivo > Abrir > Carpeta** para abrir una carpeta que contiene un archivo *CMakeLists.txt*, sucede lo siguiente:

- Visual Studio agrega un elemento de menú **CMake** al menú principal, con los comandos para ver y modificar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake.exe y genera opcionalmente la caché de CMake para la *configuración* predeterminada, que es Debug x86. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos *CMakeLists.txt* "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar y depurar), C++ IntelliSense y la exploración están disponibles para todos los proyectos de CMake del área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Visual Studio usa un archivo denominado *CMakeSettings.json* para almacenar variables de entorno u opciones de línea de comandos para Cmake.exe. *CMakeSettings.json* también permite definir y almacenar varias configuraciones de compilación de CMake. Puede cambiar fácilmente entre ellas en el IDE.

En caso contrario, use *CMakeLists.txt* tal como haría en cualquier proyecto de CMake para especificar archivos de código fuente, buscar bibliotecas, establecer opciones del compilador y del enlazador y especificar otra información relacionada con el sistema de compilación.

Si necesita pasar argumentos a un archivo ejecutable en tiempo de depuración, puede usar otro archivo denominado **launch.vs.json**. En algunos escenarios, Visual Studio genera automáticamente estos archivos. Puede editarlos manualmente o incluso crearlos usted mismo.

> [!NOTE]
> Para otros tipos de proyectos Abrir carpeta, se usan dos archivos JSON adicionales: **CppProperties.json** y **tasks.vs.json**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="import-an-existing-cache"></a>Importar una caché existente

Cuando se importa un archivo *CMakeCache.txt* existente, Visual Studio extrae las variables personalizadas de manera automática y crea un archivo *CMakeSettings.json* previamente rellenado basado en ellas. La caché original no se modifica de ninguna manera. Todavía se puede usar el archivo existente desde la línea de comandos o con cualquier herramienta o IDE que se haya usado para generarlo. El archivo *CMakeSettings.json* nuevo se coloca junto al archivo raíz *CMakeLists.txt* del proyecto. Visual Studio genera una caché nueva en función del archivo de configuración. La generación automática de caché se puede invalidar en el cuadro de diálogo **Herramientas > Opciones > CMake > General**.

No se importa todo el contenido de la caché.  Propiedades como el generador y la ubicación de los compiladores se reemplazan con valores predeterminados que se sabe que funcionan de manera correcta con el IDE.

### <a name="to-import-an-existing-cache"></a>Para importar una caché existente

1. En el menú principal, seleccione **Archivo > Abrir > CMake**:

   ![Apertura de CMake](media/cmake-file-open.png "Archivo, Abrir, CMake")

   Ese comando abre el asistente **Importar proyecto CMake de la memoria caché**.

2. Navegue hasta el archivo *CMakeCache.txt* que quiera importar y, después, haga clic en **Aceptar**. Se abrirá el asistente **Importar proyecto CMake de la memoria caché**:

   ![Importación de una caché de CMake](media/cmake-import-wizard.png "Abrir el asistente para importar la caché de CMake")

   Cuando se complete el asistente, verá el archivo *CMakeCache.txt* nuevo en el **Explorador de soluciones** junto al archivo raíz *CMakeLists.txt* del proyecto.

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas General, busque el menú desplegable **Configuraciones**. Probablemente muestre "Linux-Debug" o "x64-Debug" de forma predeterminada. Seleccione la configuración preferida y presione **F5**, o bien haga clic en el botón **Ejecutar** (el triángulo de color verde) en la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en *CMakeLists.txt* y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > Compilar solución** (**F7** o **Ctrl+Mayús+B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando del menú de compilación de CMake](media/cmake-build-menu.png "Menú de comandos de compilación de CMake")

Puede personalizar configuraciones de compilación, variables de entorno, argumentos de línea de comandos y otras opciones en el archivo *CMakeSettings.json*. Esto le permite realizar cambios sin modificar el archivo *CMakeLists.txt*. Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "Errores de compilación de CMake")

En una carpeta con varios destinos de compilación, puede especificar qué destino de CMake se va a compilar: Elija el elemento **Compilar** en el menú de **CMake** o en el menú contextual de *CMakeLists.txt* para especificar el destino. Si presiona **Ctrl+Mayús+B** en un proyecto de CMake, se compila el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija su configuración preferida y presione **F5**. O bien, presione el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón Ejecutar de CMake](media/cmake-run-button.png "Botón Ejecutar de CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

Puede personalizar una sesión de depuración de CMake mediante el establecimiento de las propiedades en el archivo **launch.vs.json**. Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo *CMakeLists.txt*, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado de color amarillo y le informa de que IntelliSense se va a actualizar. Le ofrece la oportunidad de cancelar la operación de actualización. Para obtener información sobre *CMakeLists.txt*, vea la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición del archivo CMakeLists.txt](media/cmake-cmakelists.png "Edición del archivo CMakeLists.txt")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **Lista de errores** para navegar a la línea incorrecta en *CMakeLists.txt*.

   ![Errores del archivo CMakeLists.txt](media/cmake-cmakelists-error.png "Errores del archivo CMakeLists.txt")

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios importantes en los archivos *CMakeSettings.json* o *CMakeLists.txt*, Visual Studio vuelve a ejecutar de manera automática el paso de configuración de CMake. Si el paso de configuración finaliza sin errores, la información que se recopila está disponible en C++ IntelliSense y en los servicios de lenguaje. También se usa esta información en las operaciones de compilación y depuración.

Varios proyectos de CMake pueden usar el mismo nombre de configuración de CMake (por ejemplo, "x86-Debug"). Todos ellos se configuran y compilan (en su propia carpeta raíz de compilación) cuando se selecciona esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en esa configuración de CMake.

   ![Elemento de menú de solo compilación de CMake](media/cmake-build-only.png "Elemento de menú de solo compilación de CMake")

Puede limitar las compilaciones y las sesiones de depuración a un subconjunto de los proyectos en el área de trabajo. Cree una nueva configuración con un nombre único en el archivo *CMakeSettings.json*. A continuación, aplique la configuración solo a esos proyectos. Al seleccionar esa configuración, IntelliSense y los comandos de compilación y depuración se aplican solo a los proyectos especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **CMake** o el menú contextual de *CMakeLists.txt* en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo *CMakeCache.txt* desde la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para *CMakeCache.txt* se borra si limpia la caché. Para realizar cambios que se conservan después de limpiar la caché, vea [Personalización de la configuración de CMake](customize-cmake-settings.md)).

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza la ejecución del paso de generación aunque Visual Studio considere que el entorno está actualizado.

La generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas > Opciones > CMake > General**.

## <a name="single-file-compilation"></a>Compilación de un único archivo

Para compilar un único archivo en un proyecto de CMake, haga clic con el botón derecho en el archivo en el **Explorador de soluciones**. Elija **Compilar** en el menú emergente. También puede compilar el archivo abierto actualmente en el editor si usa el menú principal de **CMake**:

![Compilación de archivo único de CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Para obtener más información, vea el artículo sobre cómo [compilar en la línea de comandos](building-on-the-command-line.md).

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2015"

In Visual Studio 2015, los usuarios de Visual Studio pueden usar un [generador CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) para generar archivos de proyecto de MSBuild que, después, el IDE usa para IntelliSense, exploración y compilación.

::: moniker-end

## <a name="see-also"></a>Vea también

[Tutorial: Creación de proyectos multiplataforma de C++ en Visual Studio](get-started-linux-cmake.md)\
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)\
[Conexión al equipo remoto Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)\
[Referencia del esquema CMakeSettings.json](cmakesettings-reference.md)\
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)\
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)
