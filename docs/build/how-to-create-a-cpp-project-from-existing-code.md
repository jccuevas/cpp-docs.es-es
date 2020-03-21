---
title: 'Cómo: Crear un proyecto de C++ a partir del código existente'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 5e59230186380b787c95dbe08914bcd9d3ca2407
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078551"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Cómo: Crear un proyecto de C++ a partir del código existente

En Visual Studio, puede trasladar los archivos de código existentes a un proyecto de C++ mediante el asistente **Create New Project From Existing Code Files** (Crear nuevo proyecto de archivos de código fuente existentes). Este asistente crea una solución de proyecto que usa el sistema MSBuild para administrar los archivos de código fuente y la configuración de compilación. Funciona mejor con proyectos relativamente sencillos que no tienen jerarquías de carpetas complejas. Este asistente no está disponible en las ediciones Express anteriores de Visual Studio.

Trasladar los archivos de código existentes a un proyecto de C++ permite usar las características nativas de administración de proyectos de MSBuild integradas en el IDE. Si prefiere usar el sistema de compilación existente, como archivos Make de nmake, CMake u otras alternativas, en su lugar puede usar las opciones Abrir carpeta o CMake. Para obtener más información, consulte [Abrir proyectos de C++ carpeta para proyectos de](open-folder-projects-cpp.md) o [CMake en Visual Studio](cmake-projects-in-visual-studio.md). Ambas opciones permiten usar características del IDE como [IntelliSense](/visualstudio/ide/using-intellisense) y [Propiedades del proyecto](working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Para crear un proyecto de C++ a partir de código existente

1. En el menú **Archivo**, seleccione **Nuevo** > **Project From Existing Code** (Proyecto a partir de código existente).

1. Especifique la ubicación del proyecto, el directorio para los archivos de origen y los tipos de archivos que el asistente importará al nuevo proyecto. Elija **Siguiente** para continuar.

    | Configuración | Descripción |
    | --- | --- |
    | **Ubicación del archivo de proyecto** | Especifica la ruta del directorio del proyecto nuevo. Esta ubicación es donde el asistente deposita todos los archivos (y subdirectorios) del proyecto nuevo.<br/><br/>Seleccione **Examinar** para ver el cuadro de diálogo **Ubicación del archivo de proyecto**. Vaya a la carpeta adecuada y especifique el directorio que contenga el nuevo proyecto. |
    | **Nombre del proyecto** | Especifica el nombre del proyecto nuevo. Los archivos de proyecto, que tienen extensiones de archivo como .vcxproj, tomarán este nombre, mientras que los archivos de código existentes conservarán su nombre original. |
    | **Agregar archivos al proyecto desde estas carpetas** | Marque esta opción para establecer el asistente para copiar los archivos de código existentes desde sus directorios originales (que se especifican en el cuadro de lista situado debajo de este control) en el proyecto nuevo.<br/><br/>Marque **Agregar subcarpetas** para especificar la copia de los archivos de código de todos los subdirectorios al proyecto. Los directorios se muestran en la columna **Carpeta**.<br/>- Seleccione **Agregar** para ver el cuadro de diálogo **Agregar archivos al proyecto desde esta carpeta**, con el que podrá especificar los directorios en los que el asistente buscará archivos de código existentes.<br/>- Seleccione **Quitar** para eliminar la ruta de acceso de directorio seleccionada en el cuadro de lista.<br/><br/>En el cuadro **Tipos de archivo para agregar al proyecto**, especifique los tipos de archivo que el asistente agregará al nuevo proyecto en función de las extensiones de archivo. Las extensiones de archivo están precedidas por el carácter comodín de asterisco y se delimitan mediante un punto y coma en la lista de extensiones de archivo. |
    | **Mostrar todos los archivos en el Explorador de soluciones** | Especifica que todos los archivos del proyecto nuevo sean visibles y se muestren en la ventana **Explorador de soluciones**. Esta opción está habilitada de manera predeterminada. |

    ![Ubicación del proyecto](media/location.png)

1. Especifique la configuración del proyecto que se usará (por ejemplo, el entorno y la configuración de compilación), de modo que coincida con un tipo de proyecto específico que se deba generar. Elija **Siguiente** para continuar.

    | Configuración | Descripción |
    | --- | --- |
    | **Usar Visual Studio** | Especifica que se usen las herramientas de compilación que se incluyen en Visual Studio para generar el proyecto nuevo. Esta opción está activada de forma predeterminada.<br/><br/>Seleccione **Tipo de proyecto** para especificar el tipo de proyecto que generará el asistente. Elija **Proyecto de aplicación Windows**, **Proyecto aplicación de consola**, **Proyecto de biblioteca de vínculos dinámicos (DLL)** o **Proyecto de biblioteca estática (LIB)** .<br/><br/>Marque **Agregar compatibilidad con ATL** para agregar compatibilidad con ATL al nuevo proyecto.<br/><br/>Marque **Agregar compatibilidad con MFC** para agregar compatibilidad con MFC al nuevo proyecto.<br/><br/>Marque **Agregar compatibilidad con Common Language Runtime** para agregar compatibilidad con la programación en CLR al proyecto. Elija la **compatibilidad con Common Language Runtime** para el tipo de cumplimiento, como **Common Language Runtime (sintaxis antigua)** para la compatibilidad con C++ las extensiones administradas para la sintaxis, la sintaxis de programación de CLR antes de Visual Studio 2005. |
    | **Usar el sistema de compilación externo** | Especifica que se usen las herramientas de compilación que no se incluyen en Visual Studio para generar el proyecto nuevo. Cuando esta opción está seleccionada, puede especificar líneas de comandos de compilación en las páginas **Especificar valores de configuración Debug** y **Especificar valores de configuración Release**. |

    ![Configuración del proyecto](media/settings.png)

    > [!NOTE]
    > Cuando se activa la opción **Usar el sistema de compilación externo**, el IDE no genera el proyecto, por lo que no se necesitan las opciones /D, /I, /FI, /AI o /FU para la compilación. Pero estas opciones se deben establecer de manera correcta para que IntelliSense funcione correctamente.

1. Especifique los valores de configuración de depuración que se van a usar. Elija **Siguiente** para continuar.

    | Configuración | Descripción |
    | --- | --- |
    | **Línea de comandos de Compilar** | Especifica la línea de comandos que compila el proyecto. Escriba el nombre del compilador (además de los modificadores o argumentos) o los scripts de compilación que quiera usar para compilar el proyecto. |
    | **Línea de comandos de recompilación** | Especifica la línea de comandos que recompila el proyecto nuevo. |
    | **Línea de comandos de limpieza** | Especifica la línea de comandos para eliminar los archivos de soporte generados por las herramientas de compilación para el proyecto. |
    | **Salida (para depuración)** | Especifica la ruta de acceso de directorio de los archivos de salida para la configuración de depuración del proyecto. |
    | **Definiciones del preprocesador (/D)** | Define símbolos de preprocesador para el proyecto. Vea [/D (Definiciones de preprocesador)](../build/reference/d-preprocessor-definitions.md). |
    | **Ruta de acceso de búsqueda de inclusión (/I)** | Especifica las rutas de acceso de directorio que el compilador busca para resolver referencias a archivos pasadas a directivas de prepocesador en el proyecto. Vea [I (directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md). |
    | **Archivos de inclusión forzados (/FI)** | Especifica los archivos de encabezado que se procesan al compilar el proyecto. Vea [/FI (Dar nombre al archivo de inclusión obligatorio)](../build/reference/fi-name-forced-include-file.md). |
    | **Ruta de acceso de búsqueda de ensamblado .NET (/AI)** | Especifica las rutas de acceso de directorio que el compilador busca para resolver las referencias de ensamblado de .NET que se pasan a las directivas de preprocesador en el proyecto. Vea [/AI (Especificar directorios de metadatos)](../build/reference/ai-specify-metadata-directories.md). |
    | **Forzados usando ensamblados .NET (/FU)** | Especifica los ensamblados .NET que se van a procesar al compilar el proyecto. Vea [/FU (Asignar nombre al archivo #using obligatorio)](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Configuración de proyecto](media/config.png)

    > [!NOTE]
    > Las opciones **Compilar**, **Volver a compilar**, **Borrar** línea de comandos y **Salida (para depuración)** solo están habilitadas si la opción **Usar sistema de compilación externo** está seleccionado en la página **Especificar configuración del proyecto**.

1. Especifique las opciones de configuración de versión que se usarán. Estas opciones son las mismas que las opciones de configuración de depuración. Haga clic en **Finalizar** para generar el proyecto nuevo.

    > [!NOTE]
    > Aquí puede marcar **Igual a la configuración de depuración** para especificar que el asistente genere unas opciones de configuración de proyecto de versión idénticas a las opciones de configuración de proyecto de depuración. Esta opción está activada de forma predeterminada. Todas las demás opciones de esta página están inactivas, a menos que desactive esta casilla.
