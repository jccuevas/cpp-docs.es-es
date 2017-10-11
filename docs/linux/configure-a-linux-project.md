---
title: Configurar un proyecto de Linux | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 9a3239120ccdbc533c5063c50a523ad84774f81c
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---

# <a name="configure-a-linux-project"></a>Configurar un proyecto de Linux

## <a name="general-settings"></a>Configuración general
Con Visual Studio se pueden configurar una serie de opciones para un proyecto de Linux.  Para ver estas opciones, seleccione el menú **Proyecto > Propiedades** o haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades** en el menú contextual:

![Configuración general](media/settings_general.png)

De forma predeterminada, con la herramienta se crea un archivo ejecutable (.out).  Para compilar una biblioteca estática o dinámica o para usar un archivo Make existente, emplee la selección **Tipo de configuración**.

## <a name="remote-settings"></a>Configuración remota
Para cambiar la configuración relacionada con el equipo remoto Linux, seleccione el elemento **Configuración remota**:

![Configuración remota](media/settings_remote.png)

* Para cambiar el equipo Linux de destino, use la entrada **Equipo de destino**.  Esto le permitirá seleccionar una de las conexiones creadas anteriormente.  Para crear una nueva entrada, vea la sección [Conexión al equipo Linux remoto](connect-to-your-remote-linux-computer.md).

* El **directorio raíz remoto** determina la ubicación raíz donde se crea el proyecto en el equipo remoto Linux.  El valor predeterminado es **~/projects**, a menos que se cambie.

* El **directorio de proyecto remoto** es donde se creará este proyecto concreto en el equipo remoto Linux.  El valor predeterminado es **$(RemoteRootDir)/$(ProjectName)**, que se expandirá en un directorio con el nombre del proyecto actual, bajo el directorio raíz establecido arriba.

* Por último, para cambiar el valor predeterminado de los compiladores de C y C++, o el enlazador y el archivador usados para compilar el proyecto, use las entradas pertinentes de la sección **Valores predeterminados de herramientas**.  Podrían establecerse para usar una versión determinada de GCC o incluso el compilador Clang, por ejemplo.

## <a name="vc-directories"></a>Directorios de VC++
De forma predeterminada, Visual Studio no incluye ningún archivo de inclusión de nivel de sistema del equipo Linux.  Por ejemplo, los elementos del directorio **/usr/include** no están presentes en Visual Studio.  Para una compatibilidad total con [IntelliSense](/visualstudio/ide/using-intellisense), tendrá que copiar esos archivos en alguna ubicación del equipo de desarrollo y apuntar Visual Studio a esta ubicación.  Una opción es usar scp (Secure Copy) para copiar los archivos.  En Windows 10, puede usar [Bash en Windows](https://msdn.microsoft.com/commandline/wsl/about) para ejecutar scp.  En versiones anteriores de Windows, podría usar algo como [PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Puede copiar los archivos mediante un comando similar al siguiente:

`scp -r linux_username@remote_host:/usr/include .`

Por supuesto, reemplace los valores **linux_username** y **remote_host** anteriores por los adecuados para su propio entorno.

Una vez copiados los archivos, use el elemento **Directorios de VC++** de las propiedades del proyecto para indicarle a Visual Studio dónde encontrar los archivos de inclusión adicionales que se acaban de copiar.

![Directorios de VC++](media/settings_directories.png)

## <a name="copy-sources"></a>Copiar orígenes
Al compilar, los archivos de origen del equipo de desarrollo se copian en el equipo Linux y se compilan allí.  De forma predeterminada, se copian todos los orígenes del proyecto de Visual Studio en las ubicaciones establecidas en la configuración anterior.  Pero también pueden agregarse a la lista orígenes adicionales o se puede desactivar por completo la copia de orígenes, que es el valor predeterminado para un proyecto de archivos Make.

* **Orígenes para copiar** determina qué orígenes se copian en el equipo remoto.  De forma predeterminada, **@(SourcesToCopyRemotely)** usa el valor predeterminado de todos los archivos de código fuente en el proyecto, pero no incluye ningún archivo de activos/recursos, como imágenes.

* **Copiar orígenes** puede activarse y desactivarse para habilitar y deshabilitar la copia de archivos de origen en el equipo remoto.

* **Orígenes adicionales para copiar** permite agregar más archivos de origen para copiarlos en el sistema remoto.  Puede especificar una lista delimitada por punto y coma o puede usar la sintaxis **:=** para especificar un nombre local y remoto para usar:

  `C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Eventos de compilación
Dado que toda la compilación se produce en un equipo remoto, se han agregado varios eventos de compilación adicionales a la sección Eventos de compilación de las propiedades del proyecto.  Son **Evento remoto anterior a la compilación**, **Evento remoto anterior a la vinculación** y **Evento remoto posterior a la compilación** y se producirán en el equipo remoto antes o después de los pasos individuales del proceso.

![Eventos de compilación](media/settings_buildevents.png)

## <a name="see-also"></a>Vea también
[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)
