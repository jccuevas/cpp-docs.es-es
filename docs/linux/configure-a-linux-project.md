---
title: Configuración de un proyecto de C++ de Linux en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: b4e5bad5b0688a2f0deeb237335c26419e2d9cbe
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207907"
---
# <a name="configure-a-linux-project"></a>Configurar un proyecto de Linux
En este tema se describe cómo configurar un proyecto C++ de Linux en Visual Studio. Para obtener información sobre los proyectos de Linux de CMake en Visual Studio, consulte [Configuración de un proyecto de CMake de Linux](cmake-linux-project.md).

## <a name="general-settings"></a>Configuración general
Con Visual Studio se pueden configurar una serie de opciones para un proyecto de Linux.  Para ver estas opciones, seleccione el menú **Proyecto > Propiedades** o haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades** en el menú contextual. Aparecerá la configuración **General**.

![Configuración general](media/settings_general.png)

De forma predeterminada, con la herramienta se crea un archivo ejecutable (.out).  Para compilar una biblioteca estática o dinámica o para usar un archivo Make existente, emplee la selección **Tipo de configuración**.

## <a name="remote-settings"></a>Configuración remota
Para cambiar la configuración correspondiente al equipo Linux remoto, configure las opciones remotas que aparecen en la configuración **General**:

* Para cambiar el equipo Linux de destino, use la entrada **Máquina de compilación remota**.  Esto le permitirá seleccionar una de las conexiones creadas anteriormente.  Para crear una nueva entrada, vea la sección [Conexión al equipo Linux remoto](connect-to-your-remote-linux-computer.md).

* El **Directorio raíz de la compilación remota** determina la ubicación raíz donde se crea el proyecto en el equipo Linux remoto.  El valor predeterminado es **~/projects**, a menos que se cambie.

* El **Directorio del proyecto de compilación remota** es donde se creará este proyecto concreto en el equipo remoto Linux.  El valor predeterminado es **$(RemoteRootDir)/$(ProjectName)**, que se expandirá en un directorio con el nombre del proyecto actual, bajo el directorio raíz establecido arriba.

> [!NOTE]
> Para cambiar el valor predeterminado de los compiladores de C y C++, o el enlazador y el archivador usados para compilar el proyecto, use las entradas pertinentes de la sección **C/C++ > General** y en la sección **Enlazador > General**.  Podrían establecerse para usar una versión determinada de GCC o incluso el compilador Clang, por ejemplo.

## <a name="include-directories-and-intellisense-support"></a>Directorios de inclusión y compatibilidad con IntelliSense

**Visual Studio 2017 versión 15.6 y anteriores:** de forma predeterminada, Visual Studio no incluye los archivos de inclusión de nivel de sistema del equipo Linux.  Por ejemplo, los elementos del directorio **/usr/include** no están presentes en Visual Studio.
Para una compatibilidad total con [IntelliSense](/visualstudio/ide/using-intellisense), tendrá que copiar esos archivos en alguna ubicación del equipo de desarrollo y apuntar Visual Studio a esta ubicación.  Una opción es usar scp (Secure Copy) para copiar los archivos.  En Windows 10, puede usar [Bash en Windows](https://msdn.microsoft.com/commandline/wsl/about) para ejecutar scp.  En versiones anteriores de Windows, podría usar algo como [PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Puede copiar los archivos mediante un comando similar al siguiente:

`scp -r linux_username@remote_host:/usr/include .`

Por supuesto, reemplace los valores **linux_username** y **remote_host** anteriores por los adecuados para su propio entorno.

Una vez copiados los archivos, use el elemento **Directorios de VC++** de las propiedades del proyecto para indicarle a Visual Studio dónde encontrar los archivos de inclusión adicionales que se acaban de copiar.

![Directorios de VC++](media/settings_directories.png)

**Visual Studio 2017 15.7 y versiones posteriores:** vea [Administrar encabezados remotos para IntelliSense](#remote_intellisense).

## <a name="copy-sources"></a>Copiar orígenes
Al compilar, los archivos de origen del equipo de desarrollo se copian en el equipo Linux y se compilan allí.  De forma predeterminada, se copian todos los orígenes del proyecto de Visual Studio en las ubicaciones establecidas en la configuración anterior.  Pero también pueden agregarse a la lista orígenes adicionales o se puede desactivar por completo la copia de orígenes, que es el valor predeterminado para un proyecto de archivos Make.

* **Orígenes para copiar** determina qué orígenes se copian en el equipo remoto.  De forma predeterminada, **@(SourcesToCopyRemotely)** usa el valor predeterminado de todos los archivos de código fuente en el proyecto, pero no incluye ningún archivo de activos/recursos, como imágenes.

* **Copiar orígenes** puede activarse y desactivarse para habilitar y deshabilitar la copia de archivos de origen en el equipo remoto.

* **Orígenes adicionales para copiar** permite agregar más archivos de origen para copiarlos en el sistema remoto.  Puede especificar una lista delimitada por punto y coma o puede usar la sintaxis **:=** para especificar un nombre local y remoto para usar:

  `C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Eventos de compilación
Dado que toda la compilación se produce en un equipo remoto, se han agregado varios eventos de compilación adicionales a la sección Eventos de compilación de las propiedades del proyecto.  Estos son **Evento remoto anterior a la compilación**, **Evento remoto anterior a la vinculación** y **Evento remoto posterior a la compilación**, y se producirán en el equipo remoto antes o después de los pasos individuales del proceso.

![Eventos de compilación](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> IntelliSense para los encabezados remotos (Visual Studio 2017 15.7 y versiones posteriores)

Cuando se agrega una conexión nueva en **Connection Manager**, Visual Studio detecta automáticamente los directorios de inclusión para el compilador en el sistema remoto. Luego, Visual Studio comprime y copia esos archivos en un directorio en el equipo Windows local. Después de eso, cuando se use esa conexión en un proyecto de Visual Studio o CMake, se usan los encabezados de esos directorios para proporcionar IntelliSense.

Esta funcionalidad depende de que el equipo Linux tenga instalado zip. Puede instalar zip mediante este comando apt-get:

```cmd
apt install zip
```

Para administrar la caché de encabezados, vaya a **Herramientas > Opciones, multiplataforma > Connection Manager > Administrador de IntelliSense de encabezados remotos**. Para actualizar la caché de encabezados después de realizar cambios en el equipo Linux, seleccione la conexión remota y, después, haga clic en **Actualizar**. Haga clic en **Eliminar** para quitar los encabezados sin eliminar la propia conexión. Haga clic en **Explorar** para abrir el directorio local en el **Explorador de archivos**. Trate a esta carpeta como de solo lectura. Para descargar los encabezados de una conexión existente que se creó antes de la versión 15.3, seleccione la conexión y, después, haga clic en **Descargar**.

![IntelliSense de encabezados remotos](media/remote-header-intellisense.png)

## <a name="see-also"></a>Vea también
[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)  
[C++ General Properties (Linux C++)](../linux/prop-pages/general-linux.md) (Propiedades generales de C++ (Linux C++))  
[VC++ Directories (Linux C++)](../linux/prop-pages/directories-linux.md) (Directorios de VC++ (Linux C++))  
[Copy Sources Project Properties (Linux C++)](../linux/prop-pages/copy-sources-project.md) (Propiedades del proyecto Copiar orígenes (Linux C++))  
[Build Event Properties (Linux C++)](../linux/prop-pages/build-events-linux.md) (Propiedades de evento de compilación (Linux C++))