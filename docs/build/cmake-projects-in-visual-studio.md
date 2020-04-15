---
title: Proyectos de CMake en Visual Studio
description: Cómo crear y compilar proyectos de C++ mediante CMake en Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329157"
---
# <a name="cmake-projects-in-visual-studio"></a>Proyectos de CMake en Visual Studio

CMake es una herramienta de código abierto multiplataforma para definir procesos de compilación que se ejecutan en varias plataformas. En este artículo se supone que está familiarizado con CMake. Puede obtener más información sobre esta herramienta en [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar el software con CMake).

> [!NOTE]
> CMake se ha integrado cada vez más con Visual Studio en las últimas versiones. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

El componente **Herramientas C++ CMake para Windows** utiliza la característica Abrir [carpeta](open-folder-projects-cpp.md) para consumir archivos de proyecto CMake (como *CMakeLists.txt*) directamente para los fines de IntelliSense y la exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, genera un archivo de proyecto temporal y lo pasa a msbuild.exe. Sin embargo, el proyecto nunca se carga para IntelliSense o con fines de exploración. También puede importar una caché CMake existente.

## <a name="installation"></a>Instalación

Las **herramientas C++ CMake para Windows** se instalan como parte del desarrollo de **escritorios con C++** y Linux Development con cargas de trabajo **C++.** Para obtener más información, consulte [Proyectos CMake multiplataforma](../linux/cmake-linux-project.md).

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install-2019.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Al elegir **Archivo > Abrir > Carpeta** para abrir una carpeta que contiene un archivo *CMakeLists.txt,* suceden las siguientes cosas:

- Visual Studio agrega **elementos CMake** al menú **Proyecto,** con comandos para ver y editar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta cmake.exe y genera el archivo de caché CMake (*CMakeCache.txt*) para la configuración predeterminada (depuración x64). La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos *CMakeLists.txt* "raíz" del área de trabajo. Las operaciones de CMake (configurar, compilar, depurar), C++ IntelliSense y la exploración están disponibles para todos los proyectos de CMake en el área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Haga clic en el botón **Mostrar todos los archivos** en la parte superior del **Explorador** de soluciones para ver toda la salida generada por CMake en las carpetas *\<out/build/config>.*

Visual Studio usa un archivo de configuración denominado **CMakeSettings.json**. Este archivo le permite definir y almacenar varias configuraciones de compilación y cambiar convenientemente entre ellas en el IDE. Una *configuración* es una construcción de Visual Studio que encapsula la configuración que es específica de un tipo de compilación determinado. La configuración se usa para configurar las opciones de línea de comandos predeterminadas que Visual Studio pasa a cmake.exe. También puede especificar opciones adicionales de CMake aquí y definir cualquier variable adicional que desee. Todas las opciones se escriben en la memoria caché de CMake como variables internas o externas. En Visual Studio 2019, el Editor de configuración de **CMake** proporciona una manera cómoda de editar la configuración. Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Una configuración, `intelliSenseMode` no se pasa a CMake, pero solo lo usa Visual Studio.

Utilice el archivo **CMakeLists.txt** en cada carpeta del proyecto tal como lo haría en cualquier proyecto CMake. Puede especificar archivos de origen, buscar bibliotecas, establecer opciones del compilador y del vinculador y especificar otra información relacionada con el sistema de compilación.

Para pasar argumentos a un ejecutable en tiempo de depuración, puede usar otro archivo denominado **launch.vs.json**. En algunos escenarios, Visual Studio genera automáticamente estos archivos. Puede editarlos manualmente o incluso crear el archivo usted mismo.

> [!NOTE]
> Para otros tipos de proyectos de Open Folder, se utilizan dos archivos JSON adicionales: **CppProperties.json** y **tasks.vs.json**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="open-an-existing-cache"></a>Abrir una caché existente

Al abrir un archivo de caché CMake existente (*CMakeCache.txt*), Visual Studio no intenta administrar la memoria caché y el árbol de compilación por usted. Las herramientas personalizadas o preferidas tienen un control completo sobre cómo CMake configura el proyecto. Para abrir una caché existente en Visual Studio, elija **Archivo > Abrir > CMake**. A continuación, vaya a un archivo *CMakeCache.txt* existente.

Puede agregar una caché CMake existente a un proyecto abierto. Se hace de la misma manera que agregaría una nueva configuración. Para obtener más información, vea nuestra entrada de blog sobre la apertura de [una caché existente en Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas General, busque el menú desplegable **Configuraciones**. Probablemente muestra "x64-Debug" de forma predeterminada. Seleccione la configuración preferida y pulse **F5**o haga clic en el botón **Ejecutar** (triángulo verde) de la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en *CMakeLists.txt* y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Generar > Compilar todo** (**F7** o **Ctrl+Mayús+B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![CHacer comando de menú de compilación](media/cmake-build-menu.png "CHacer menú de comandos de compilación")

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "Errores de compilación de CMake")

En una carpeta con varios destinos de compilación, puede especificar qué destino de CMake se va a compilar: elija el elemento **Build** en el menú **CMake** o el menú contextual *CMakeLists.txt* para especificar el destino. Si escribe **Ctrl+Mayús+B** en un proyecto CMake, crea el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto CMake, elija la configuración preferida y presione **F5**o presione el botón **Ejecutar** en la barra de herramientas. Si el botón **Ejecutar** dice "Seleccionar elemento de inicio", seleccione la flecha desplegable. Elija el destino que desea ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón de ejecución CMake](media/cmake-run-button.png "Botón de ejecución CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior. Los cambios en *CMakeSettings.json* hacen que se regenere la memoria caché de CMake.

Puede personalizar una sesión de depuración de CMake estableciendo propiedades en el archivo **launch.vs.json.** Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="just-my-code-for-cmake-projects"></a>Sólo mi código para proyectos CMake

Al compilar para Windows mediante el compilador MSVC, los proyectos de CMake tienen compatibilidad con la depuración Just My Code. Para cambiar la configuración de Solo mi código, vaya a **Opciones** > **Options** > de herramientas**Depuración** > **general**.

## <a name="vcpkg-integration"></a>Integración de Vcpkg

Si ha instalado [vcpkg](vcpkg.md), los proyectos CMake abiertos en Visual Studio integran automáticamente el archivo de cadena de herramientas vcpkg. Esto significa que no se requiere ninguna configuración adicional para usar vcpkg con sus proyectos CMake. Este soporte funciona tanto para instalaciones vcpkg locales como para instalaciones vcpkg en sistemas remotos a los que se dirige. Este comportamiento se deshabilita automáticamente cuando se especifica cualquier otra cadena de herramientas en la configuración de Configuración de CMake.

## <a name="customize-configuration-feedback"></a>Personalizar los comentarios de configuración

De forma predeterminada, la mayoría de los mensajes de configuración se suprimen a menos que haya un error. Puede ver todos los mensajes habilitando esta función en**Opciones** > de **herramientas** > **CMake**.

   ![Configuración de las opciones de diagnóstico de CMake](media/vs2019-cmake-configure-options.png "Opciones de diagnóstico de CMake")

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo *CMakeLists.txt,* haga clic con el botón derecho en el archivo en el **Explorador** de soluciones y elija **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado amarilla que le informa de que IntelliSense se actualizará. Le da la oportunidad de cancelar la operación de actualización. Para obtener información acerca de *CMakeLists.txt*, consulte la documentación de [CMake](https://cmake.org/documentation/).

   ![Edición de archivos CMakeLists.txt](media/cmake-cmakelists.png "Edición de archivos CMakeLists.txt")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **lista** de errores para navegar a la línea infractora en *CMakeLists.txt*.

   ![Errores de archivo CMakeLists.txt](media/cmake-cmakelists-error.png "Errores de archivo CMakeLists.txt")

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Al realizar cambios significativos en los archivos *CMakeSettings.json* o *CMakeLists.txt,* Visual Studio vuelve a ejecutar automáticamente el paso de configuración de CMake. Si el paso de configuración finaliza sin errores, la información recopilada está disponible en C++ IntelliSense y servicios de lenguaje. También se usa en operaciones de compilación y depuración.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de la caché de CMake para diagnosticar un problema, abra el menú principal **del proyecto** o el menú contextual *CMakeLists.txt* en el **Explorador** de soluciones para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo *CMakeCache.txt* de la carpeta raíz de compilación en el editor. (Cualquier edición que realice aquí en *CMakeCache.txt* se eliminará si limpia la memoria caché. Para realizar cambios que persisten después de limpiar la memoria caché, consulte Personalizar la configuración de [CMake](customize-cmake-settings.md).)

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza el paso de generación para ejecutar se ejecuta incluso si Visual Studio considera el entorno actualizado.

La generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas > opciones > CMake > General.**

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Para obtener más información, consulte [Creación en la línea de comandos](building-on-the-command-line.md).

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 tiene una compatibilidad completa con CMake, incluidos [los proyectos CMake multiplataforma.](../linux/cmake-linux-project.md) El componente Herramientas de **Visual C++ para CMake** utiliza la característica **Abrir carpeta** para permitir que el IDE consuma archivos de proyecto CMake (como *CMakeLists.txt)* directamente para los fines de IntelliSense y la exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, genera un archivo de proyecto temporal y lo pasa a msbuild.exe. Sin embargo, el proyecto nunca se carga para IntelliSense o con fines de exploración. También puede importar una caché CMake existente.

## <a name="installation"></a>Instalación

**Visual C++ Tools para CMake** se instala como parte del desarrollo de **escritorio con C++** y Linux Development con cargas de trabajo **C++.**

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Al elegir **Archivo > Abrir > Carpeta** para abrir una carpeta que contiene un archivo *CMakeLists.txt,* suceden las siguientes cosas:

- Visual Studio agrega un elemento de menú **CMake** al menú principal, con los comandos para ver y modificar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake.exe y genera opcionalmente la caché de CMake para la *configuración* predeterminada, que es Debug x86. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos *CMakeLists.txt* "raíz" del área de trabajo. Las operaciones de CMake (configurar, compilar, depurar), C++ IntelliSense y la exploración están disponibles para todos los proyectos de CMake en el área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Visual Studio usa un archivo denominado *CMakeSettings.json* para almacenar variables de entorno u opciones de línea de comandos para Cmake.exe. *CMakeSettings.json* también le permite definir y almacenar varias configuraciones de compilación de CMake. Puede cambiar convenientemente entre ellos en el IDE.

De lo contrario, use *CMakeLists.txt* tal como lo haría en cualquier proyecto de CMake para especificar archivos de origen, buscar bibliotecas, establecer opciones del compilador y del vinculador y especificar otra información relacionada con el sistema de compilación.

Si necesita pasar argumentos a un ejecutable en tiempo de depuración, puede usar otro archivo denominado **launch.vs.json**. En algunos escenarios, Visual Studio genera automáticamente estos archivos. Puede editarlos manualmente o incluso crear el archivo usted mismo.

> [!NOTE]
> Para otros tipos de proyectos de Open Folder, se utilizan dos archivos JSON adicionales: **CppProperties.json** y **tasks.vs.json**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="import-an-existing-cache"></a>Importar una caché existente

Al importar un archivo *CMakeCache.txt* existente, Visual Studio extrae automáticamente variables personalizadas y crea un archivo *CMakeSettings.json* rellenado previamente en función de ellas. La memoria caché original no se modifica de ninguna manera. Todavía se puede utilizar desde la línea de comandos, o con cualquier herramienta o IDE utilizado para generarlo. El nuevo archivo *CMakeSettings.json* se coloca junto a la raíz del proyecto *CMakeLists.txt*. Visual Studio genera una caché nueva en función del archivo de configuración. Puede invalidar la generación automática de caché en el cuadro de diálogo **Herramientas > opciones > CMake > General.**

No se importa todo el contenido de la caché.  Propiedades como el generador y la ubicación de los compiladores se reemplazan con valores predeterminados que se sabe que funcionan de manera correcta con el IDE.

### <a name="to-import-an-existing-cache"></a>Para importar una caché existente

1. En el menú principal, elija **Archivo > Abrir > CMake**:

   ![Abrir CMake](media/cmake-file-open.png "Archivo, Abierto, CMake")

   Este comando abre el asistente **Importar CMake desde caché.**

2. Vaya al archivo *CMakeCache.txt* que desea importar y, a continuación, haga clic en **Aceptar**. Se abrirá el asistente **Importar proyecto CMake de la memoria caché**:

   ![Importar una caché CMake](media/cmake-import-wizard.png "Abra el asistente de caché de importación de CMake")

   Cuando se complete el asistente, puede ver el nuevo archivo *CMakeCache.txt* en el **Explorador** de soluciones junto al archivo *CMakeLists.txt* raíz del proyecto.

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas General, busque el menú desplegable **Configuraciones**. Probablemente esté mostrando "Linux-Debug" o "x64-Debug" de forma predeterminada. Seleccione la configuración preferida y pulse **F5**o haga clic en el botón **Ejecutar** (triángulo verde) de la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en *CMakeLists.txt* y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > compilar solución** (**F7** o **Ctrl+Mayús+B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![CHacer comando de menú de compilación](media/cmake-build-menu.png "CHacer menú de comandos de compilación")

Puede personalizar las configuraciones de compilación, las variables de entorno, los argumentos de línea de comandos y otras opciones de configuración en el archivo *CMakeSettings.json.* Le permite realizar cambios sin modificar el archivo *CMakeLists.txt.* Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "Errores de compilación de CMake")

En una carpeta con varios destinos de compilación, puede especificar qué destino de CMake se va a compilar: elija el elemento **Build** en el menú **CMake** o el menú contextual *CMakeLists.txt* para especificar el destino. Si escribe **Ctrl+Mayús+B** en un proyecto CMake, crea el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto CMake, elija la configuración preferida y presione **F5**. O bien, pulse el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón de ejecución CMake](media/cmake-run-button.png "Botón de ejecución CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

Puede personalizar una sesión de depuración de CMake estableciendo propiedades en el archivo **launch.vs.json.** Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo *CMakeLists.txt,* haga clic con el botón derecho en el archivo en el **Explorador** de soluciones y elija **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado amarilla que le informa de que IntelliSense se actualizará. Le da la oportunidad de cancelar la operación de actualización. Para obtener información acerca de *CMakeLists.txt*, consulte la documentación de [CMake](https://cmake.org/documentation/).

   ![Edición de archivos CMakeLists.txt](media/cmake-cmakelists.png "Edición de archivos CMakeLists.txt")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **lista** de errores para navegar a la línea infractora en *CMakeLists.txt*.

   ![Errores de archivo CMakeLists.txt](media/cmake-cmakelists-error.png "Errores de archivo CMakeLists.txt")

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios significativos en el *CMakeSettings.json* o en *CMakeLists.txt* archivos, Visual Studio vuelve a ejecutar automáticamente el CMake configurar paso. Si el paso de configuración finaliza sin errores, la información recopilada está disponible en C++ IntelliSense y servicios de lenguaje. También se usa en operaciones de compilación y depuración.

Varios proyectos DeCMake pueden usar el mismo nombre de configuración de CMake (por ejemplo, x86-Debug). Todos ellos se configuran y se construyen (en su propia carpeta raíz de compilación) cuando se selecciona esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en esa configuración de CMake.

   ![Elemento de menú CMake Build Only](media/cmake-build-only.png "Elemento de menú CMake Build Only")

Puede limitar las compilaciones y las sesiones de depuración a un subconjunto de los proyectos del área de trabajo. Cree una nueva configuración con un nombre único en el archivo *CMakeSettings.json.* A continuación, aplique la configuración solo a esos proyectos. Cuando se selecciona esa configuración, IntelliSense y los comandos de compilación y depuración solo se aplican a esos proyectos especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **CMake** o el menú contextual de *CMakeLists.txt* en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo *CMakeCache.txt* de la carpeta raíz de compilación en el editor. (Cualquier edición que realice aquí en *CMakeCache.txt* se eliminará si limpia la memoria caché. Para realizar cambios que persisten después de limpiar la memoria caché, consulte Personalizar la configuración de [CMake](customize-cmake-settings.md).)

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza el paso de generación para ejecutar se ejecuta incluso si Visual Studio considera el entorno actualizado.

La generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas > opciones > CMake > General.**

## <a name="single-file-compilation"></a>Compilación de un solo archivo

Para crear un único archivo en un proyecto de CMake, haga clic con el botón derecho en el archivo en el **Explorador**de soluciones . Elija **Compilar** en el menú emergente. También puede crear el archivo abierto actualmente en el editor mediante el menú **principal de CMake:**

![Compilación de archivo único de CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Para obtener más información, consulte Creación en la línea de [comandos](building-on-the-command-line.md) .

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2015"

In Visual Studio 2015, los usuarios de Visual Studio pueden usar un [generador CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) para generar archivos de proyecto de MSBuild que, después, el IDE usa para IntelliSense, exploración y compilación.

::: moniker-end

## <a name="see-also"></a>Consulte también

[Tutorial: Crear proyectos multiplataforma de C++ en Visual Studio](get-started-linux-cmake.md)\
[Configurar un proyecto de Linux CMake](../linux/cmake-linux-project.md)\
[Conéctese a su ordenador Linux remoto](../linux/connect-to-your-remote-linux-computer.md)\
[Personalizar la configuración de compilación de CMake](customize-cmake-settings.md)\
[Referencia de esquema CMakeSettings.json](cmakesettings-reference.md)\
[Configurar sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)\
[Implemente, ejecute y depure su proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)
