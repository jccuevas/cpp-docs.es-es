---
title: Proyectos de CMake en Visual Studio
ms.date: 10/01/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 168f5b0aac34757a9c2d73bcebc908a0d58721fe
ms.sourcegitcommit: b85e1db6b7d4919852ac6843a086ba311ae97d40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2019
ms.locfileid: "71925571"
---
# <a name="cmake-projects-in-visual-studio"></a>Proyectos de CMake en Visual Studio

CMake es una herramienta de código abierto multiplataforma para definir procesos de compilación que se ejecutan en varias plataformas. En este artículo se da por hecho que está familiarizado con CMake. Puede obtener más información sobre esta herramienta en [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar el software con CMake). 

> [!NOTE]
> CMake se ha vuelto más integrado con Visual Studio en las últimas versiones. Para ver la información correcta de la versión que está usando, asegúrese de que el selector de versiones que se encuentra en la parte superior izquierda de esta página esté configurado correctamente. 

::: moniker range="vs-2019"

El  **C++ componente herramientas de CMake para Windows** usa la característica [Abrir carpeta](https://docs.microsoft.com/en-us/cpp/build/open-folder-projects-cpp?view=vs-2019) para consumir archivos de proyecto CMake (como archivo CMakeLists. txt) directamente con fines de IntelliSense y exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, se genera un archivo de proyecto temporal y se pasa a msbuild.exe, pero nunca se carga para IntelliSense o con fines de exploración. También puede importar una memoria caché de CMake existente.

## <a name="installation"></a>Instalación

**C++** **Las herramientas de CMake para Windows se instalan de forma predeterminada como parte del desarrollo de escritorio con carga de trabajo y como parte del desarrollo de Linux con C++**  carga de trabajo. **C++** Para obtener más información [, vea proyectos multiplataforma de CMake](../linux/cmake-linux-project.md) .

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install-2019.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Cuando elija **archivo > abrir > carpeta** para abrir una carpeta que contenga un archivo archivo CMakeLists. txt, ocurrirá lo siguiente:

- Visual Studio agrega elementos **CMake** al menú **proyecto** , con comandos para ver y editar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake. exe y genera la memoria caché de CMake para la *configuración*predeterminada, que es la depuración x64. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos CMakeLists.txt "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar, depurar) así como IntelliSense y la exploración de C++ están disponibles para todos los proyectos de CMake del área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Visual Studio usa un archivo llamado **CMakeSettings. JSON** para almacenar variables de entorno o opciones de línea de comandos para CMake. exe. **CMakeSettings. JSON** también permite definir y almacenar varias configuraciones de compilación de CMake y cambiar de forma cómoda entre ellas en el IDE. En Visual Studio 2019, el **Editor de configuración de CMake** proporciona una manera cómoda de editar la configuración. Consulte [Personalización](customize-cmake-settings.md) de la configuración de CMake para obtener más información.

De lo contrario, use **archivo CMakeLists. txt** tal como lo haría en cualquier proyecto de CMake para especificar archivos de código fuente, buscar bibliotecas, establecer opciones del compilador y del enlazador, y especificar otra información relacionada con el sistema de compilación.

Si necesita pasar argumentos a un archivo ejecutable en tiempo de depuración, puede utilizar otro archivo denominado **Launch. vs. JSON**. En algunos escenarios, Visual Studio generará automáticamente estos archivos, que se pueden editar manualmente. También puede crear el archivo usted mismo.

> [!NOTE]
> Para otros tipos de proyectos de carpeta abierta, se usan dos archivos JSON adicionales: **CppProperties. JSON** y **Tasks. vs. JSON**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="open-an-existing-cache"></a>Abrir una caché existente

Al abrir una memoria caché de CMake existente, Visual Studio no intentará administrar la memoria caché y el árbol de compilación automáticamente. Esto proporciona a las herramientas personalizadas o preferidas un control completo sobre cómo CMake configura el proyecto. Puede abrir una caché existente en Visual Studio a través de **archivo > abrir > CMake** y navegar a un CMakeCache. txt existente. Como alternativa, si ya ha abierto el proyecto en Visual Studio, puede agregarle una caché existente del mismo modo que agregaría una nueva configuración. Para obtener más información, consulte nuestra entrada de blog sobre cómo [abrir una caché existente en Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas general, busque la lista desplegable **configuraciones** . Probablemente muestra "x64-debug" de forma predeterminada. Seleccione la configuración deseada y presione **F5**o haga clic en el botón **Ejecutar** (triángulo verde) de la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en CMakeLists.txt y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > compilar todo** (**F7** o **Ctrl + Mayús + B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando Compilar del menú de CMake](media/cmake-build-menu.png "Comando Compilar del menú de CMake")

Puede personalizar las configuraciones de compilación, las variables de entorno, los argumentos de la línea de comandos y otros valores sin modificar el archivo archivo CMakeLists. txt mediante el **Editor de configuración de CMake**. Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "CMake build errors")

En una carpeta con varios destinos de compilación, puede elegir el elemento **Generar** del menú **CMake** o el menú contextual de **CMakeLists.txt** para especificar qué destino de CMake se va a compilar. Al presionar **Ctrl+Mayús+B** en un proyecto de CMake se compila el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija la configuración deseada y presione **F5**, o bien presione el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón Ejecutar de CMake](media/cmake-run-button.png "Botón Ejecutar de CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

Puede personalizar una sesión de depuración de CMake estableciendo las propiedades en el archivo **Launch. vs. JSON** . Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="just-my-code-for-cmake-projects"></a>Solo mi código para proyectos de CMake

Cuando se compila para Windows mediante el compilador de MSVC, los proyectos de CMake tienen compatibilidad con la depuración de solo mi código en el compilador y el enlazador si la opción está habilitada en Visual Studio. Para cambiar la configuración, vaya a **herramientas** > **Opciones** > **depuración** > **General**.

## <a name="vcpkg-integration"></a>Integración de Vcpkg

Si ha instalado [vcpkg](vcpkg.md), los proyectos de CMake abiertos en Visual Studio integrarán automáticamente el archivo de cadena de herramientas vcpkg. Esto significa que no se requiere ninguna configuración adicional para usar vcpkg con los proyectos de CMake. Esta compatibilidad funciona para las instalaciones locales de vcpkg y las instalaciones de vcpkg en sistemas remotos a los que se destina. Este comportamiento se deshabilita automáticamente cuando se especifica cualquier otra cadena de herramientas en la configuración de la configuración de CMake.

## <a name="customize-configuration-feedback"></a>Personalización de comentarios de configuración

De forma predeterminada, la mayoría de los mensajes de configuración se suprimen a menos que se produzca un error. Puede ver todos los mensajes habilitando esta característica en **herramientas** > **Opciones** > **CMake**.

   ![Configuración de opciones]de diagnóstico de CMake opciones de diagnóstico(media/vs2019-cmake-configure-options.png "CMake")

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo CMakeLists.txt, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado de color amarillo y le informa de que IntelliSense se va a actualizar, y le da la oportunidad de cancelar la operación de actualización. Para obtener información sobre CMakeLists.txt, vea la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición de archivos CMakeLists.txt](media/cmake-cmakelists.png "CMakeLists.txt file editing")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **Lista de errores** para navegar a la línea incorrecta en CMakeLists.txt.

   ![Errores de archivos CMakeLists.txt](media/cmake-cmakelists-error.png "CMakeLists.txt file errors")


## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios significativos en los archivos **CMakeSettings. JSON** o archivo CMakeLists. txt, Visual Studio vuelve a ejecutar automáticamente el paso de configuración de CMake. Si el paso de configuración finaliza sin errores, la información que se recopila está disponible en IntelliSense de C++ y los servicios de lenguaje, y también en las operaciones de compilación y depuración.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de la memoria caché de CMake para diagnosticar un problema, abra el menú principal del **proyecto** o el menú contextual de **archivo CMakeLists. txt** en **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo CMakeCache.txt desde la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para CMakeCache.txt se borra si limpia la caché. Para realizar cambios que se conservan después de limpiar la memoria caché, vea [personalizar la configuración de CMake](customize-cmake-settings.md)).

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza la ejecución del paso de generación aunque Visual Studio considere que el entorno está actualizado.

La generación automática de caché puede deshabilitarse en el cuadro de diálogo **herramientas > opciones > CMake > general** .

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Vea [Compilar en la línea de comandos](building-on-the-command-line.md) para obtener más información.

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 es compatible con CMake, incluidos los [proyectos de CMake multiplataforma](../linux/cmake-linux-project.md). El componente **Herramientas de Visual C++ para CMake** usa la característica **Abrir carpeta** para habilitar el IDE para el consumo de archivos de proyecto de CMake (por ejemplo, CMakeLists.txt) directamente para los propósitos de IntelliSense y la exploración. Se admiten generadores de Ninja y Visual Studio. Si usa un generador de Visual Studio, se genera un archivo de proyecto temporal y se pasa a msbuild.exe, pero nunca se carga para IntelliSense o con fines de exploración. También puede importar una memoria caché de CMake existente. 

## <a name="installation"></a>Instalación

**Herramientas de Visual C++ para CMake** se instala de forma predeterminada como parte de la carga de trabajo de **desarrollo para el escritorio con C++** y de la carga de trabajo **desarrollo de Linux con C++** .

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install.png)

Para obtener más información, vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integración del IDE

Cuando elija **archivo > abrir > carpeta** para abrir una carpeta que contenga un archivo archivo CMakeLists. txt, ocurrirá lo siguiente:

- Visual Studio agrega un elemento de menú **CMake** al menú principal, con los comandos para ver y modificar scripts de CMake.

- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.

- Visual Studio ejecuta CMake.exe y genera opcionalmente la caché de CMake para la *configuración* predeterminada, que es Debug x86. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.

- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.

Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos CMakeLists.txt "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar, depurar) así como IntelliSense y la exploración de C++ están disponibles para todos los proyectos de CMake del área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)

Los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

Visual Studio usa un archivo llamado **CMakeSettings. JSON** para almacenar variables de entorno o opciones de línea de comandos para CMake. exe. **CMakeSettings. JSON** también permite definir y almacenar varias configuraciones de compilación de CMake y cambiar de forma cómoda entre ellas en el IDE. 

De lo contrario, use el archivo **archivo CMakeLists. txt** tal como lo haría en cualquier proyecto de CMake para especificar archivos de código fuente, buscar bibliotecas, establecer opciones del compilador y del enlazador, y especificar otra información relacionada con el sistema de compilación.

Si necesita pasar argumentos a un archivo ejecutable en tiempo de depuración, puede utilizar otro archivo denominado **Launch. vs. JSON**. En algunos escenarios, Visual Studio generará automáticamente estos archivos, que se pueden editar manualmente. También puede crear el archivo usted mismo.

> [!NOTE]
> Para otros tipos de proyectos de carpeta abierta, se usan dos archivos JSON adicionales: **CppProperties. JSON** y **Tasks. vs. JSON**. Ninguno de estos es pertinente para los proyectos de CMake.

## <a name="import-an-existing-cache"></a>Importar una caché existente

Cuando se importa un archivo CMakeCache.txt existente, Visual Studio extrae las variables personalizadas de manera automática y crea un archivo **CMakeSettings.json** previamente rellenado basado en ellas. La caché original no se modifica de ninguna manera y se puede seguir usando desde la línea de comandos o con cualquier herramienta o IDE que se usara para generarla. El nuevo archivo **CMakeSettings. JSON** se colocará junto con la raíz archivo CMakeLists. txt del proyecto. Visual Studio genera una caché nueva en función del archivo de configuración. Puede invalidar la generación automática de caché en el cuadro de diálogo **herramientas > opciones > CMake > general** .

No se importa todo el contenido de la caché.  Propiedades como el generador y la ubicación de los compiladores se reemplazan con valores predeterminados que se sabe que funcionan de manera correcta con el IDE.

### <a name="to-import-an-existing-cache"></a>Para importar una caché existente

1. En el menú principal, elija **archivo > abrir > CMake**:

   ![Abrir CMake](media/cmake-file-open.png "Archivo, Abrir, CMake")

   Se abrirá el asistente **Importar proyecto CMake de la memoria caché**.

2. Navegue hasta el archivo CMakeCache.txt que quiere importar y después haga clic en **Aceptar**. Se abrirá el asistente **Importar proyecto CMake de la memoria caché**:

   ![Importar una caché CMake](media/cmake-import-wizard.png "Abrir el Asistente para importar la caché de CMake")

   Cuando se complete el asistente, verá el archivo CMakeCache.txt nuevo en el **Explorador de soluciones** junto al archivo CMakeLists.txt raíz del proyecto.

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. En la barra de herramientas general, busque la lista desplegable **configuraciones** . es probable que se muestre de forma predeterminada "Linux-debug" o "x64-debug". Seleccione la configuración deseada y presione **F5**o haga clic en el botón **Ejecutar** (triángulo verde) de la barra de herramientas. Primero se compila el proyecto de manera automática, como una solución de Visual Studio.

1. Haga clic con el botón derecho en CMakeLists.txt y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico.

1. En el menú principal, seleccione **Compilar > compilar solución** (**F7** o **Ctrl + Mayús + B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando Compilar del menú de CMake](media/cmake-build-menu.png "Comando Compilar del menú de CMake")

Puede personalizar las configuraciones de compilación, las variables de entorno, los argumentos de la línea de comandos y otros valores sin modificar el archivo archivo CMakeLists. txt con el archivo **CMakeSettings. JSON** . Para obtener más información, vea [Personalización de la configuración de CMake](customize-cmake-settings.md).

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.

![Errores de compilación de CMake](media/cmake-build-errors.png "CMake build errors")

En una carpeta con varios destinos de compilación, puede elegir el elemento **Generar** del menú **CMake** o el menú contextual de **CMakeLists.txt** para especificar qué destino de CMake se va a compilar. Al presionar **Ctrl+Mayús+B** en un proyecto de CMake se compila el documento activo actual.

## <a name="debugging-cmake-projects"></a>Depuración de proyectos de CMake

Para depurar un proyecto de CMake, elija la configuración deseada y presione **F5**, o bien presione el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp).

![Botón Ejecutar de CMake](media/cmake-run-button.png "Botón Ejecutar de CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

Puede personalizar una sesión de depuración de CMake estableciendo las propiedades en el archivo **Launch. vs. JSON** . Para obtener más información, vea [Configure CMake debugging sessions](configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).


## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo CMakeLists.txt, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado de color amarillo y le informa de que IntelliSense se va a actualizar, y le da la oportunidad de cancelar la operación de actualización. Para obtener información sobre CMakeLists.txt, vea la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición de archivos CMakeLists.txt](media/cmake-cmakelists.png "CMakeLists.txt file editing")

Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **Lista de errores** para navegar a la línea incorrecta en CMakeLists.txt.

   ![Errores de archivos CMakeLists.txt](media/cmake-cmakelists-error.png "CMakeLists.txt file errors")


## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios significativos en los archivos **CMakeSettings. JSON** o archivo CMakeLists. txt, Visual Studio vuelve a ejecutar automáticamente el paso de configuración de CMake. Si el paso de configuración finaliza sin errores, la información que se recopila está disponible en IntelliSense de C++ y los servicios de lenguaje, y también en las operaciones de compilación y depuración.

Cuando varios proyectos de CMake usan el mismo nombre de configuración de CMake (por ejemplo, x86-Debug), todos se configuran y compilan (en su propia carpeta raíz de compilación) al seleccionar esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en esa configuración de CMake.

   ![Elemento de menú Solo compilación de CMake](media/cmake-build-only.png "CMake Build Only menu item")

Para limitar las compilaciones y las sesiones de depuración a un subconjunto de los proyectos del área de trabajo, cree una nueva configuración con un nombre único en el archivo **CMakeSettings. JSON** y aplíquela solo a esos proyectos. Al seleccionar esa configuración, los comandos de IntelliSense y de compilación y depuración se habilitan solo para los proyectos especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **CMake** o el menú contextual de **CMakeLists.txt** en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo CMakeCache.txt desde la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para CMakeCache.txt se borra si limpia la caché. Para realizar cambios que se conservan después de limpiar la memoria caché, vea [personalizar la configuración de CMake](customize-cmake-settings.md)).

- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.

- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.

- **Generar caché** fuerza la ejecución del paso de generación aunque Visual Studio considere que el entorno está actualizado.

La generación automática de caché puede deshabilitarse en el cuadro de diálogo **herramientas > opciones > CMake > general** .

## <a name="single-file-compilation"></a>Compilación de archivo único

Para compilar un único archivo en un proyecto de CMake, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y elija **Compilar**. También puede compilar el archivo que esté actualmente abierto en el editor, usando para ello el menú principal de CMake:

![Compilación de archivo único de CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ejecutar CMake desde la línea de comandos

Si ha instalado CMake desde el instalador de Visual Studio, puede ejecutarlo desde la línea de comandos siguiendo estos pasos:

1. Ejecute el vsdevcmd.bat adecuado (x86/x64). Vea [Compilar en la línea de comandos](building-on-the-command-line.md) para obtener más información.

1. Cambie a la carpeta de salida.

1. Ejecute CMake para compilar o configurar la aplicación.

::: moniker-end

::: moniker range="vs-2015"

In Visual Studio 2015, los usuarios de Visual Studio pueden usar un [generador CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) para generar archivos de proyecto de MSBuild que, después, el IDE usa para IntelliSense, exploración y compilación.

::: moniker-end


## <a name="see-also"></a>Vea también

[Tutorial: Creación de proyectos multiplataforma de C++ en Visual Studio](get-started-linux-cmake.md)<br/>
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)<br/>
[Referencia de CMakeSettings.json](cmakesettings-reference.md)<br/>
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)<br/>
