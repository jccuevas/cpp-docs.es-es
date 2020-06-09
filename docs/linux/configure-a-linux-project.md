---
title: Configuración de un proyecto de C++ para Linux en Visual Studio
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: c60fd678caef20d8b5a715b0e40bba6a37407709
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623587"
---
# <a name="configure-a-linux-project"></a>Configuración de un proyecto de Linux

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

En este tema se describe cómo configurar un proyecto C++ de Linux según se explica en [Creación de un proyecto de C++ para Linux en Visual Studio](create-a-new-linux-project.md). Para obtener información sobre los proyectos de Linux de CMake, consulte [Configuración de un proyecto de CMake de Linux](cmake-linux-project.md).

Puede configurar un proyecto de Linux que tenga como destino un equipo físico de Linux, una máquina virtual o el [subsistema Windows para Linux](/windows/wsl/about) (WSL).

::: moniker range="vs-2019"

**Visual Studio 2019 versión 16.1**:

- Si el destino es WSL, puede ahorrarse las operaciones de copia que sí deben realizarse para compilar y en IntelliSense cuando el destino es un sistema Linux remoto.

- Puede especificar destinos de Linux independientes para la compilación y depuración.

::: moniker-end

## <a name="general-settings"></a>Configuración general

Para ver las opciones de configuración, seleccione el menú **Proyecto > Propiedades** o haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades** en el menú contextual. Aparecerá la configuración **General**.

![Configuración general](media/settings_general.png)

De forma predeterminada, se crea un archivo ejecutable (.out). Para compilar una biblioteca estática o dinámica, o para usar un archivo Make existente, emplee la opción **Tipo de configuración**.

Para obtener más información sobre la configuración de las páginas de propiedades, vea [Referencia de las páginas de propiedades de un proyecto de Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Configuración remota

Para cambiar la configuración correspondiente al equipo Linux remoto, configure las opciones remotas que aparecen en [General](prop-pages/general-linux.md).

- Para especificar un equipo Linux de destino remoto, use la entrada **Máquina de compilación remota**. Esto le permitirá seleccionar una de las conexiones creadas anteriormente. Para crear una entrada, vea la sección [Conexión al equipo Linux remoto](connect-to-your-remote-linux-computer.md).

   ![Máquina de compilación](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 versión 16.1**: Para establecer como destino el subsistema de Windows para Linux, haga clic en la flecha abajo **Conjunto de herramientas de la plataforma** y elija **WSL_1_0**. Las otras opciones remotas desaparecerán y se mostrará en su lugar la ruta de acceso al shell de WSL predeterminado:

   ![Máquina de compilación de WSL](media/wsl-remote-vs2019.png)

   Si tiene instalaciones de WSL en paralelo, aquí puede especificar una ruta de acceso distinta. Para obtener más información sobre cómo administrar varias distribuciones, consulte [Manage and configure Windows Subsystem for Linux](/windows/wsl/wsl-config#set-a-default-distribution) (Administrar y configurar el subsistema de Windows para Linux).

   Puede especificar otro destino de depuración en la página **Propiedades de configuración** > **Depuración**.

   ::: moniker-end

- El **Directorio raíz de la compilación remota** determina la ubicación raíz donde se crea el proyecto en el equipo Linux remoto. El valor predeterminado es **~/projects**, a menos que se cambie.

- El **Directorio del proyecto de compilación remota** es donde se creará este proyecto concreto en el equipo remoto Linux. El valor predeterminado es **$(RemoteRootDir)/$(ProjectName)** , que se expandirá en un directorio con el nombre del proyecto actual, bajo el directorio raíz establecido arriba.

> [!NOTE]
> Para cambiar el valor predeterminado de los compiladores de C y C++, o el enlazador y el archivador usados para compilar el proyecto, use las entradas pertinentes de la sección **C/C++ > General** y en la sección **Enlazador > General**. Puede especificar una versión determinada de GCC o Clang, por ejemplo. Para más información, vea [Propiedades de C o C++ (C++ para Linux)](prop-pages/c-cpp-linux.md) y [Propiedades del enlazador (C++ para Linux)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Copiar orígenes (solo sistemas remotos)

::: moniker range="vs-2019"

Esta sección no es válida si el destino es WSL.

::: moniker-end

Al compilar en sistemas remotos, los archivos de origen del equipo de desarrollo se copian en el equipo Linux y se compilan allí. De forma predeterminada, se copian todos los orígenes del proyecto de Visual Studio en las ubicaciones establecidas en la configuración anterior. Pero también pueden agregarse a la lista orígenes adicionales o se puede desactivar por completo la copia de orígenes, que es el valor predeterminado para un proyecto de archivos Make.

- **Orígenes para copiar** determina qué orígenes se copian en el equipo remoto. De forma predeterminada, **\@(SourcesToCopyRemotely)** usa el valor predeterminado de todos los archivos de código fuente en el proyecto, pero no incluye ningún archivo de activos/recursos, como imágenes.

- **Copiar orígenes** puede activarse y desactivarse para habilitar y deshabilitar la copia de archivos de origen en el equipo remoto.

- **Orígenes adicionales para copiar** permite agregar más archivos de origen para copiarlos en el sistema remoto. Puede especificar una lista delimitada por punto y coma o puede usar la sintaxis **:=** para especificar un nombre local y remoto para usar:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Eventos de compilación

Dado que toda la compilación se produce en un equipo remoto (o en WSL), se han agregado varios eventos de compilación más a la sección Eventos de compilación de las propiedades del proyecto. Estos son **Evento remoto anterior a la compilación**, **Evento remoto anterior a la vinculación** y **Evento remoto posterior a la compilación**, y se producirán en el equipo remoto antes o después de los pasos individuales del proceso.

![Eventos de compilación](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a> IntelliSense para encabezados en sistemas remotos

Cuando se agrega una conexión nueva en **Connection Manager**, Visual Studio detecta automáticamente los directorios de inclusión para el compilador en el sistema remoto. Luego, Visual Studio comprime y copia esos archivos en un directorio en el equipo Windows local. Después de eso, cuando se use esa conexión en un proyecto de Visual Studio o CMake, se usan los encabezados de esos directorios para proporcionar IntelliSense.

> [!NOTE]
> En la versión 16.5 de Visual Studio 2019 y versiones posteriores se ha optimizado la copia remota de encabezados. Ahora, los encabezados se copian a petición al abrir un proyecto de Linux o configurar CMake para un destino de Linux. La copia se produce en segundo plano en función de cada proyecto, según los compiladores especificados del proyecto en cuestión. Para obtener más información, vea [Mejoras en la precisión y el rendimiento de IntelliSense en Linux](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/).

Esta funcionalidad depende de que el equipo Linux tenga instalado zip. Puede instalar zip mediante este comando apt-get:

```cmd
sudo apt install zip
```

Para administrar la caché de encabezados, vaya a **Herramientas > Opciones, multiplataforma > Connection Manager > Administrador de IntelliSense de encabezados remotos**. Para actualizar la caché de encabezados después de realizar cambios en el equipo Linux, seleccione la conexión remota y, después, haga clic en **Actualizar**. Haga clic en **Eliminar** para quitar los encabezados sin eliminar la propia conexión. Haga clic en **Explorar** para abrir el directorio local en el **Explorador de archivos**. Trate a esta carpeta como de solo lectura. Para descargar los encabezados de una conexión existente que se creó antes de Visual Studio 2017 versión 15.3, seleccione la conexión y, después, haga clic en **Descargar**.

::: moniker range="vs-2017"

![IntelliSense de encabezados remotos](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![IntelliSense de encabezados remotos](media/connection-manager-vs2019.png)

Puede habilitar el registro para ayudar a solucionar problemas:

![Registro remoto](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Vea también

[Set compiler and build properties](../build/working-with-project-properties.md) (Establecer las propiedades del compilador y la compilación)<br/>
[C++ General Properties (Linux C++)](prop-pages/general-linux.md) (Propiedades generales de C++ (Linux C++))<br/>
[VC++ Directories (Linux C++)](prop-pages/directories-linux.md) (Directorios de VC++ (Linux C++))<br/>
[Copy Sources Project Properties (Linux C++)](prop-pages/copy-sources-project.md) (Propiedades del proyecto Copiar orígenes (Linux C++))<br/>
[Build Event Properties (Linux C++)](prop-pages/build-events-linux.md) (Propiedades de evento de compilación (Linux C++))
