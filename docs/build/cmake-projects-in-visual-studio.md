---
title: Proyectos de CMake en Visual Studio
description: Cómo crear y compilar C++ proyectos mediante CMake en Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: be252759e93eb30d4f9b4ff1446dd4217fcdf2a6
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791835"
---
# <a name="cmake-projects-in-visual-studio"></a>Proyectos de CMake en Visual Studio

CMake es una herramienta de código abierto multiplataforma para definir procesos de compilación que se ejecutan en varias plataformas. En este artículo se da por supuesto que está familiarizado con CMake. Puede obtener más información sobre esta herramienta en [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar el software con CMake).

> [!NOTE]
> CMake se ha vuelto más integrado con Visual Studio en las últimas versiones. Para ver la información correcta de la versión que está usando, asegúrese de que el selector de versiones que se encuentra en la parte superior izquierda de esta página esté configurado correctamente.

::: moniker range="vs-2019"

El  **C++ componente herramientas de CMake para Windows** usa la característica [Abrir carpeta](open-folder-projects-cpp.md) para consumir archivos de proyecto CMake (como *archivo CMakeLists. txt*) directamente con fines de IntelliSense y exploración. Se admiten generadores de Ninja y Visual Studio. Si utiliza un generador de Visual Studio, genera un archivo de proyecto temporal y lo pasa a MSBuild. exe. Sin embargo, el proyecto no se carga nunca con fines de exploración o de IntelliSense. También puede importar una memoria caché de CMake existente.

## <a name="installation"></a>Instalación de

**C++**  **C++ CMake Tools para Windows** se instala como parte del desarrollo de escritorio con y el **desarrollo de C++ Linux con** cargas de trabajo. Para obtener más información, vea [proyectos multiplataforma de CMake](../linux/cmake-linux-project.md).

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install-2019.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Cuando elija **archivo > abrir > carpeta** para abrir una carpeta que contenga un archivo *archivo CMakeLists. txt* , ocurrirá lo siguiente:

- Visual Studio agrega elementos **CMake** al menú **proyecto** , con comandos para ver y editar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake. exe y genera el archivo de caché CMake (*CMakeCache. txt*) para la configuración predeterminada (depuración x64). La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos *archivo CMakeLists. txt* "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar C++ , depurar), IntelliSense y examinar están disponibles para todos los proyectos de CMake en el área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Haga clic en el botón **Mostrar todos los archivos** situado en la parte superior de **Explorador de soluciones** para ver todas las salidas generadas por CMake en las carpetas *out/Build/\<Config >* .

Visual Studio usa un archivo de configuración denominado **CMakeSettings. JSON**. Este archivo le permite definir y almacenar varias configuraciones de compilación y cambiar de forma cómoda entre ellas en el IDE. Una *configuración* es una construcción de Visual Studio que encapsula valores que son específicos de un tipo de compilación determinado. La configuración se usa para configurar las opciones predeterminadas de la línea de comandos que Visual Studio pasa a CMake. exe. También puede especificar opciones de CMake adicionales aquí y definir las variables adicionales que desee. Todas las opciones se escriben en la memoria caché de CMake como variables internas o externas. En Visual Studio 2019, el **Editor de configuración de CMake** proporciona una manera cómoda de editar la configuración. Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Un valor, `intelliSenseMode` no se pasa a CMake, pero solo lo usa Visual Studio.

Use el archivo **archivo CMakeLists. txt** en cada carpeta del proyecto tal como lo haría en cualquier proyecto de CMake. Puede especificar archivos de código fuente, buscar bibliotecas, establecer opciones del compilador y del enlazador, y especificar otra información relacionada con el sistema de compilación.

Para pasar argumentos a un archivo ejecutable en tiempo de depuración, puede utilizar otro archivo denominado **Launch. vs. JSON**. En algunos escenarios, Visual Studio genera automáticamente estos archivos. Puede editarlos manualmente o incluso crear el archivo.

> [!NOTE]
> Para otros tipos de proyectos de carpeta abierta, se usan dos archivos JSON adicionales: **CppProperties. JSON** y **Tasks. vs. JSON**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="open-an-existing-cache"></a>Abrir una caché existente

Al abrir un archivo de caché de CMake existente (*CMakeCache. txt*), Visual Studio no intenta administrar la memoria caché y el árbol de compilación automáticamente. Las herramientas personalizadas o preferidas tienen un control completo sobre cómo CMake configura el proyecto. Para abrir una memoria caché existente en Visual Studio, elija **archivo > abrir > CMake**. A continuación, navegue a un archivo *CMakeCache. txt* existente.

Puede Agregar una memoria caché de CMake existente a un proyecto abierto. Se realiza de la misma manera que agregaría una nueva configuración. Para obtener más información, consulte nuestra entrada de blog sobre cómo [abrir una caché existente en Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas general, busque la lista desplegable **configuraciones** . Probablemente muestra "x64-debug" de forma predeterminada. Seleccione la configuración preferida y presione **F5**o haga clic en el botón **Ejecutar** (triángulo verde) de la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en *archivo CMakeLists. txt* y seleccione **compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > compilar todo** (**F7** o **Ctrl + Mayús + B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando de menú compilar CMake](media/cmake-build-menu.png "CMake menú de comandos de compilación")

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "Errores de compilación de CMake")

En una carpeta con varios destinos de compilación, puede especificar qué destino de CMake se va a compilar: elija el elemento **compilar** en el menú **CMake** o el menú contextual *archivo CMakeLists. txt* para especificar el destino. Si **presiona Ctrl + Mayús + B** en un proyecto CMake, se genera el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija la configuración preferida y presione **F5**o haga clic en el botón **Ejecutar** de la barra de herramientas. Si el botón **Ejecutar** indica "seleccionar elemento de inicio", seleccione la flecha de lista desplegable. Elija el destino que desea ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![CMake botón ejecutar](media/cmake-run-button.png "CMake botón ejecutar")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior. Los cambios en *CMakeSettings. JSON* provocan que se vuelva a generar la caché de CMake.

Puede personalizar una sesión de depuración de CMake estableciendo las propiedades en el archivo **Launch. vs. JSON** . Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="just-my-code-for-cmake-projects"></a>Solo mi código para proyectos de CMake

Cuando se compila para Windows mediante el compilador de MSVC, los proyectos de CMake admiten la depuración Solo mi código. Para cambiar el valor de Solo mi código, vaya a **herramientas** > **Opciones** > **depuración** > **General**.

## <a name="vcpkg-integration"></a>Integración de Vcpkg

Si ha instalado [vcpkg](vcpkg.md), los proyectos de CMake abiertos en Visual Studio integran automáticamente el archivo de cadena de herramientas vcpkg. Esto significa que no se requiere ninguna configuración adicional para usar vcpkg con los proyectos de CMake. Esta compatibilidad funciona para las instalaciones locales de vcpkg y las instalaciones de vcpkg en sistemas remotos a los que está destinada. Este comportamiento se deshabilita automáticamente cuando se especifica cualquier otra cadena de herramientas en la configuración de la configuración de CMake.

## <a name="customize-configuration-feedback"></a>Personalización de comentarios de configuración

De forma predeterminada, la mayoría de los mensajes de configuración se suprimen a menos que haya un error. Puede ver todos los mensajes habilitando esta característica en **herramientas** > **Opciones** > **CMake**.

   ![Configuración de opciones de diagnóstico de CMake](media/vs2019-cmake-configure-options.png "Opciones de diagnóstico de CMake")

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo *archivo CMakeLists. txt* , haga clic con el botón derecho en el archivo en **Explorador de soluciones** y elija **abrir**. Si realiza cambios en el archivo, aparecerá una barra de estado amarilla que le informará de que IntelliSense se actualizará. Le ofrece la oportunidad de cancelar la operación de actualización. Para obtener información acerca de *archivo CMakeLists. txt*, consulte la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición del archivo archivo CMakeLists. txt](media/cmake-cmakelists.png "Edición del archivo archivo CMakeLists. txt")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en el **lista de errores** para ir a la línea infractora en *archivo CMakeLists. txt*.

   ![Errores del archivo archivo CMakeLists. txt](media/cmake-cmakelists-error.png "Errores del archivo archivo CMakeLists. txt")

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Al realizar cambios significativos en los archivos *CMakeSettings. JSON* o *archivo CMakeLists. txt* , Visual Studio vuelve a ejecutar automáticamente el paso de configuración de CMake. Si el paso configurar finaliza sin errores, la información que se recopila está disponible en C++ IntelliSense y en los servicios de lenguaje. También se usa en las operaciones de compilación y depuración.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de la memoria caché de CMake para diagnosticar un problema, abra el menú principal del **proyecto** o el menú contextual de *archivo CMakeLists. txt* en **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo *CMakeCache. txt* de la carpeta raíz de compilación en el editor. (Las ediciones que realice aquí en *CMakeCache. txt* se borrarán si limpia la memoria caché. Para realizar cambios que se conservan después de limpiar la memoria caché, vea [personalizar la configuración de CMake](customize-cmake-settings.md)).

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza el paso de generación a ejecutarse incluso si Visual Studio considera el entorno actualizado.

La generación automática de caché puede deshabilitarse en el cuadro de diálogo **herramientas > opciones > CMake > general** .

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Para obtener más información, vea [compilar en la línea de comandos](building-on-the-command-line.md).

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 es compatible con CMake, incluidos los [proyectos de CMake multiplataforma](../linux/cmake-linux-project.md). El **componente C++ Visual Tools para cmake** usa la característica **Abrir carpeta** para permitir que el IDE consuma archivos de proyecto CMake (por ejemplo, *archivo CMakeLists. txt*) directamente con fines de IntelliSense y exploración. Se admiten generadores de Ninja y Visual Studio. Si utiliza un generador de Visual Studio, genera un archivo de proyecto temporal y lo pasa a MSBuild. exe. Sin embargo, el proyecto no se carga nunca con fines de exploración o de IntelliSense. También puede importar una memoria caché de CMake existente.

## <a name="installation"></a>Instalación de

**Visual C++ Tools para cmake** se instala como parte del desarrollo de **escritorio con C++**  y **desarrollo de Linux C++ con** cargas de trabajo.

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Cuando elija **archivo > abrir > carpeta** para abrir una carpeta que contenga un archivo *archivo CMakeLists. txt* , ocurrirá lo siguiente:

- Visual Studio agrega un elemento de menú **CMake** al menú principal, con los comandos para ver y modificar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake.exe y genera opcionalmente la caché de CMake para la *configuración* predeterminada, que es Debug x86. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos *archivo CMakeLists. txt* "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar C++ , depurar), IntelliSense y examinar están disponibles para todos los proyectos de CMake en el área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Visual Studio usa un archivo llamado *CMakeSettings. JSON* para almacenar variables de entorno o opciones de línea de comandos para CMake. exe. *CMakeSettings. JSON* también permite definir y almacenar varias configuraciones de compilación de CMake. Puede cambiar fácilmente entre ellos en el IDE.

De lo contrario, use el archivo *archivo CMakeLists. txt* tal como lo haría en cualquier proyecto de CMake para especificar archivos de código fuente, buscar bibliotecas, establecer opciones del compilador y del enlazador, y especificar otra información relacionada con el sistema de compilación.

Si necesita pasar argumentos a un archivo ejecutable en tiempo de depuración, puede utilizar otro archivo denominado **Launch. vs. JSON**. En algunos escenarios, Visual Studio genera automáticamente estos archivos. Puede editarlos manualmente o incluso crear el archivo.

> [!NOTE]
> Para otros tipos de proyectos de carpeta abierta, se usan dos archivos JSON adicionales: **CppProperties. JSON** y **Tasks. vs. JSON**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="import-an-existing-cache"></a>Importar una caché existente

Al importar un archivo *CMakeCache. txt* existente, Visual Studio extrae automáticamente las variables personalizadas y crea un archivo *CMakeSettings. JSON* rellenado previamente basado en ellos. La caché original no se modifica de ninguna manera. Todavía se puede usar desde la línea de comandos o con cualquier herramienta o IDE que se use para generarlo. El nuevo archivo *CMakeSettings. JSON* se colocará junto con la raíz *archivo CMakeLists. txt*del proyecto. Visual Studio genera una caché nueva en función del archivo de configuración. Puede invalidar la generación automática de caché en el cuadro de diálogo **herramientas > opciones > CMake > general** .

No se importa todo el contenido de la caché.  Propiedades como el generador y la ubicación de los compiladores se reemplazan con valores predeterminados que se sabe que funcionan de manera correcta con el IDE.

### <a name="to-import-an-existing-cache"></a>Para importar una caché existente

1. En el menú principal, elija **archivo > abrir > CMake**:

   ![Abrir CMake](media/cmake-file-open.png "Archivo, abrir, CMake")

   Este comando abre el Asistente para la **importación de CMake desde la memoria caché** .

2. Desplácese hasta el archivo *CMakeCache. txt* que desea importar y, a continuación, haga clic en **Aceptar**. Se abrirá el asistente **Importar proyecto CMake de la memoria caché**:

   ![Importar una memoria caché de CMake](media/cmake-import-wizard.png "Abrir el Asistente para importar caché de CMake")

   Cuando se complete el asistente, podrá ver el nuevo archivo *CMakeCache. txt* en **Explorador de soluciones** junto al archivo *archivo CMakeLists. txt* raíz en el proyecto.

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas general, busque la lista desplegable **configuraciones** . Probablemente muestra "Linux-debug" o "x64-debug" de forma predeterminada. Seleccione la configuración preferida y presione **F5**o haga clic en el botón **Ejecutar** (triángulo verde) de la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en *archivo CMakeLists. txt* y seleccione **compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > compilar solución** (**F7** o **Ctrl + Mayús + B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando de menú compilar CMake](media/cmake-build-menu.png "CMake menú de comandos de compilación")

Puede personalizar las configuraciones de compilación, las variables de entorno, los argumentos de línea de comandos y otras opciones del archivo *CMakeSettings. JSON* . Permite realizar cambios sin modificar el archivo *archivo CMakeLists. txt* . Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "Errores de compilación de CMake")

En una carpeta con varios destinos de compilación, puede especificar qué destino de CMake se va a compilar: elija el elemento **compilar** en el menú **CMake** o el menú contextual *archivo CMakeLists. txt* para especificar el destino. Si **presiona Ctrl + Mayús + B** en un proyecto CMake, se genera el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija la configuración preferida y presione **F5**. O bien, haga clic en el botón **Ejecutar** de la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![CMake botón ejecutar](media/cmake-run-button.png "CMake botón ejecutar")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

Puede personalizar una sesión de depuración de CMake estableciendo las propiedades en el archivo **Launch. vs. JSON** . Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo *archivo CMakeLists. txt* , haga clic con el botón derecho en el archivo en **Explorador de soluciones** y elija **abrir**. Si realiza cambios en el archivo, aparecerá una barra de estado amarilla que le informará de que IntelliSense se actualizará. Le ofrece la oportunidad de cancelar la operación de actualización. Para obtener información acerca de *archivo CMakeLists. txt*, consulte la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición del archivo archivo CMakeLists. txt](media/cmake-cmakelists.png "Edición del archivo archivo CMakeLists. txt")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en el **lista de errores** para ir a la línea infractora en *archivo CMakeLists. txt*.

   ![Errores del archivo archivo CMakeLists. txt](media/cmake-cmakelists-error.png "Errores del archivo archivo CMakeLists. txt")

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios significativos en los archivos *CMakeSettings. JSON* o *archivo CMakeLists. txt* , Visual Studio vuelve a ejecutar automáticamente el paso de configuración de CMake. Si el paso configurar finaliza sin errores, la información que se recopila está disponible en C++ IntelliSense y en los servicios de lenguaje. También se usa en las operaciones de compilación y depuración.

Varios proyectos de CMake pueden usar el mismo nombre de configuración de CMake (por ejemplo, x86-debug). Todos ellos se configuran y compilan (en su propia carpeta raíz de compilación) cuando se selecciona esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en esa configuración de CMake.

   ![Elemento de menú solo compilar CMake](media/cmake-build-only.png "Elemento de menú solo compilar CMake")

Puede limitar las compilaciones y las sesiones de depuración a un subconjunto de los proyectos en el área de trabajo. Cree una nueva configuración con un nombre único en el archivo *CMakeSettings. JSON* . A continuación, aplique la configuración solo a esos proyectos. Cuando se selecciona esa configuración, IntelliSense y los comandos de compilación y depuración solo se aplican a los proyectos especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **CMake** o el menú contextual de *CMakeLists.txt* en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo *CMakeCache. txt* de la carpeta raíz de compilación en el editor. (Las ediciones que realice aquí en *CMakeCache. txt* se borrarán si limpia la memoria caché. Para realizar cambios que se conservan después de limpiar la memoria caché, vea [personalizar la configuración de CMake](customize-cmake-settings.md)).

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza el paso de generación a ejecutarse incluso si Visual Studio considera el entorno actualizado.

La generación automática de caché puede deshabilitarse en el cuadro de diálogo **herramientas > opciones > CMake > general** .

## <a name="single-file-compilation"></a>Compilación de un solo archivo

Para compilar un único archivo en un proyecto de CMake, haga clic con el botón derecho en el archivo en **Explorador de soluciones**. Elija **compilar** en el menú emergente. También puede compilar el archivo abierto actualmente en el editor mediante el menú principal **CMake** :

![Compilación de archivo único de CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Para obtener más información, vea [compilar en la línea de comandos](building-on-the-command-line.md) .

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2015"

In Visual Studio 2015, los usuarios de Visual Studio pueden usar un [generador CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) para generar archivos de proyecto de MSBuild que, después, el IDE usa para IntelliSense, exploración y compilación.

::: moniker-end

## <a name="see-also"></a>Vea también

[Tutorial: crear C++ proyectos multiplataforma en Visual Studio](get-started-linux-cmake.md)\
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)\
[Conéctese al equipo Linux remoto](../linux/connect-to-your-remote-linux-computer.md)\
[Personalizar la configuración de compilación de CMake](customize-cmake-settings.md)\
\ de [Referencia del esquema CMakeSettings. JSON](cmakesettings-reference.md)
[Configurar sesiones de depuración CMake](configure-cmake-debugging-sessions.md)\
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)
