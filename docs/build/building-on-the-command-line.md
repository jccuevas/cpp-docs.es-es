---
title: Uso del conjunto de herramientas de Microsoft C++ desde la línea de comandos
description: Use la cadena de herramientas del Compilador de Microsoft Visual C++ (MSVC) desde la línea de comandos fuera del IDE de Visual Studio.
ms.custom: conceptual
ms.date: 11/12/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: ec30cba8e119f96efc5bca156fa565db77904520
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422905"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Uso del conjunto de herramientas de Microsoft C++ desde la línea de comandos

Con las herramientas incluidas en Visual Studio, puede compilar aplicaciones de C y C++ en la línea de comandos. El conjunto de herramientas del compilador de Microsoft C++ (MSVC) también se puede descargar como un paquete independiente que no incluye el IDE de Visual Studio.

## <a name="download-and-install-the-tools"></a>Descarga e instalación de las herramientas

Si ha instalado Visual Studio y una carga de trabajo de C++, tiene todas las herramientas de línea de comandos. Para obtener información sobre cómo instalar C++ y Visual Studio, vea [Instalación de compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md). Si solo le interesa el conjunto de herramientas de línea de comandos, descargue las [herramientas de compilación para Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019). Cuando ejecute el archivo ejecutable que se ha descargado, este actualizará y ejecutará el Instalador de Visual Studio. Para instalar solo las herramientas que necesita para el desarrollo de C++, seleccione la carga de trabajo de las **herramientas de compilación de C++** . En **Detalles de la instalación**, puede seleccionar bibliotecas y conjuntos de herramientas opcionales para incluirlos. Para compilar código mediante los conjuntos de herramientas de Visual Studio 2015 o 2017, seleccione las herramientas de compilación opcionales MSVC v140 o MSVC v141. Cuando esté satisfecho con lo que ha seleccionado, haga clic en **Instalar**.

## <a name="how-to-use-the-command-line-tools"></a>Cómo usar las herramientas de línea de comandos

Al elegir una de las cargas de trabajo de C++ en el Instalador de Visual Studio, instala el *conjunto de herramientas de la plataforma* Visual Studio. Un conjunto de herramientas de la plataforma tiene todas las herramientas de C y C++ para una versión específica de Visual Studio. Entre las herramientas se incluyen compiladores de C/C++, enlazadores, ensambladores y otras herramientas de compilación, así como las bibliotecas correspondientes. Puede usar todas estas herramientas en la línea de comandos. También las usa internamente el IDE de Visual Studio. Existen compiladores independientes hospedados en x86 y x64, y herramientas para compilar código para destinos como x86, x64, ARM y ARM64. Cada conjunto de herramientas para una arquitectura de compilación de destino y de host en particular se almacena en su propio directorio.

Para que las herramientas funcionen correctamente, es necesario especificar varias variables específicas del entorno. Estas variables se usan para agregar las herramientas a la ruta de acceso y establecer las ubicaciones de los archivos, los archivos de biblioteca y el SDK. Para que sea fácil establecer estas variables de entorno, el instalador crea *archivos de comandos* personalizados, o archivos por lotes, durante la instalación. Puede ejecutar uno de estos archivos de comandos para establecer una arquitectura de compilación de host y de destino específica, la versión del SDK de Windows y el conjunto de herramientas de la plataforma. Para mayor comodidad, el instalador también crea accesos directos en el menú Inicio. Los accesos directos inician ventanas del símbolo del sistema para desarrolladores mediante estos archivos de comandos para combinaciones específicas de host y destino. Estos métodos abreviados garantizan que todas las variables de entorno necesarias estén establecidas y listas para su uso.

Las variables de entorno necesarias corresponden específicamente a su instalación y a la arquitectura de compilación que elija. Además, podrían cambiar con las actualizaciones del producto. Esta es la razón por la que se recomienda que use un archivo de comandos o un acceso directo del símbolo del sistema instalado, en lugar de establecer las variables de entorno por su cuenta. Para obtener más información, vea [Establecer las variables de ruta y entorno para las compilaciones de línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md).

Los conjuntos de herramientas, los archivos de comandos y los accesos directos instalados dependen del procesador del equipo y de las opciones seleccionadas durante la instalación. Las herramientas hospedadas en x86 y las herramientas cruzadas que compilan código x86 y x64 siempre están instaladas. Si tiene Windows de 64 bits, también están instaladas las herramientas hospedadas en x64 y las herramientas cruzadas que compilan código x86 y x64. Si opta por las herramientas opcionales de la Plataforma universal de Windows de C++, también se instalan las herramientas x86 y x64 que compilan código ARM y ARM64. Puede que otras cargas de trabajo instalen herramientas adicionales.

## <a name="developer-command-prompt-shortcuts"></a><a name="developer_command_prompt_shortcuts"></a> Accesos directos del símbolo del sistema para desarrolladores

Los accesos directos del símbolo del sistema se instalan en una carpeta específica de la versión de Visual Studio en el menú Inicio. Esta es una lista de los accesos directos básicos del símbolo del sistema y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x86**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x64**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x86_x64**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x64_x86**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x86 de 32 bits.

::: moniker range=">= vs-2019"

La carpeta del menú Inicio y los nombres de acceso directo varían en función de la versión instalada de Visual Studio. También dependen del **alias** de la instalación, si configuró uno. Por ejemplo, supongamos que ha instalado Visual Studio 2019 y que le ha asignado el alias *Más reciente*. El acceso directo del símbolo del sistema para desarrolladores se denominará **Símbolo del sistema para desarrolladores de VS 2019 (más reciente)** , en una carpeta llamada **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

La carpeta del menú Inicio y los nombres de acceso directo varían en función de la versión instalada de Visual Studio. También dependen del **alias** de la instalación, si configuró uno. Por ejemplo, supongamos que ha instalado Visual Studio 2017 y que le ha asignado el alias *Más reciente*. El acceso directo del símbolo del sistema para desarrolladores se denominará **Símbolo del sistema para desarrolladores de VS 2017 (más reciente)** , en una carpeta llamada **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

La carpeta del menú Inicio y los nombres de acceso directo varían en función de la versión instalada de Visual Studio. Por ejemplo, supongamos que ha instalado Visual Studio 2015. El acceso directo del símbolo del sistema para desarrolladores se denominará **Símbolo del sistema para desarrolladores de VS 2015 (más reciente)** .

::: moniker-end

### <a name="to-open-a-developer-command-prompt-window"></a><a name="developer_command_prompt"></a> Para abrir una ventana del símbolo del sistema para desarrolladores

1. En el escritorio, abra el menú **Inicio** de Windows y desplácese para buscar y abrir la carpeta de la versión de Visual Studio, como por ejemplo, **Visual Studio 2019**.

1. En la carpeta, elija **Símbolo del sistema para desarrolladores** de su versión de Visual Studio. Este acceso directo inicia una ventana del símbolo del sistema para desarrolladores que usa las herramientas nativas x86 de la arquitectura de compilación predeterminada de 32 bits para compilar código nativo x86 de 32 bits. Si prefiere una arquitectura de compilación no predeterminada, elija uno de los símbolos del sistema de herramientas nativas o cruzadas para especificar la arquitectura de host y de destino.

Una manera aún más rápida de abrir un símbolo del sistema para desarrolladores consiste en escribir *símbolo del sistema para desarrolladores* en el cuadro de búsqueda del escritorio. Después, elija el resultado que quiera.

## <a name="developer-command-file-locations"></a><a name="developer_command_file_locations"></a> Ubicaciones de archivos de comandos para desarrolladores

Si prefiere configurar el entorno de compilación en una ventana del símbolo del sistema existente, puede usar uno de los archivos de comandos creado por el instalador. Le recomendamos que establezca el entorno en una nueva ventana del símbolo del sistema. Se desaconseja cambiar más adelante los entornos en la misma ventana de comandos.

::: moniker range=">= vs-2019"

La ubicación de los archivos de comandos depende de la versión de Visual Studio que haya instalado y de las decisiones que haya tomado durante la instalación. Para Visual Studio 2019, la ubicación de instalación típica en un sistema de 64 bits es \\Archivos de programa (x86)\\Microsoft Visual Studio\\2019\\*edición*. La *edición* puede ser Community, Professional, Enterprise, BuildTools u otro alias proporcionado.

::: moniker-end
::: moniker range="= vs-2017"

La ubicación de los archivos de comandos depende de la versión de Visual Studio que haya instalado y de las decisiones que haya tomado durante la instalación. Para Visual Studio 2017, la ubicación de instalación típica en un sistema de 64 bits es \\Archivos de programa (x86)\\Microsoft Visual Studio\\2017\\*edición*. La *edición* puede ser Community, Professional, Enterprise, BuildTools u otro alias proporcionado.

::: moniker-end
::: moniker range="< vs-2017"

La ubicación del archivo de comandos depende de la versión de Visual Studio y del directorio de instalación. Para Visual Studio 2015, la ubicación de instalación típica es \\Archivos de programa (x86)\\Microsoft Visual Studio 14.0.

::: moniker-end

El archivo de comandos principal del símbolo del sistema para desarrolladores, VsDevCmd.bat, se encuentra en el subdirectorio Common7Tools\\Tools. Cuando no se especifica ningún parámetro, se establece el entorno para usar las herramientas nativas x86 para compilar código x86 de 32 bits.

::: moniker range=">= vs-2017"

Hay más archivos de comandos disponibles para configurar arquitecturas de compilación específicas. Los archivos de comandos disponibles dependen de las cargas de trabajo y las opciones de Visual Studio que haya instalado. En Visual Studio 2017 y Visual Studio 2019, los encontrará en el subdirectorio VC\\Auxiliary\\Build.

::: moniker-end
::: moniker range="< vs-2017"

Hay más archivos de comandos disponibles para configurar arquitecturas de compilación específicas. Los archivos de comandos disponibles dependen de las cargas de trabajo y las opciones de Visual Studio que haya instalado. En Visual Studio 2015, se encuentran en los subdirectorios VC, VC\\bin o VC\\bin\\*architecture*, donde *architecture* es una de las opciones del compilador nativo o cruzado.

::: moniker-end

Estos archivos de comandos establecen los parámetros predeterminados y llaman a VsDevCmd.bat para configurar el entorno de arquitectura de compilación especificada. Una instalación típica puede incluir estos archivos de comandos:

|Archivo de comandos|Arquitecturas de host y de destino|
|---|---|
|**vcvars32.bat**| Usa las herramientas nativas x86 de 32 bits para compilar código x86 de 32 bits.|
|**vcvars64.bat**| Usa las herramientas nativas x64 de 64 bits para compilar código x64 de 64 bits.|
|**vcvarsx86_amd64.bat**| Usa las herramientas nativas x86 de 32 bits para compilar código x64 de 64 bits.|
|**vcvarsamd64_x86.bat**| Usa las herramientas cruzadas nativas x64 de 64 bits para compilar código x86 de 32 bits.|
|**vcvarsx86_arm.bat**| Usa las herramientas nativas x86 de 32 bits para compilar código ARM.|
|**vcvarsamd64_arm.bat**| Usa las herramientas cruzadas nativas x64 de 64 bits para compilar código ARM.|
|**vcvarsall.bat**| Usa parámetros para especificar las arquitecturas de host y de destino, el SDK de Windows y las opciones de plataforma. Para obtener una lista de las opciones admitidas, realice una llamada mediante el parámetro **/help**.|

> [!CAUTION]
> El archivo vcvarsall.bat y otros archivos de comandos de Visual Studio pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el instalador de Visual Studio para reemplazar el archivo que falta.
>
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si se instala la versión actual de Visual Studio en un equipo que también tiene una versión anterior de Visual Studio, no ejecute vcvarsall.bat o cualquier otro archivo de comandos de Visual Studio de versiones diferentes en la misma ventana del símbolo del sistema.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Usar las herramientas de desarrollo en una ventana de comandos existente

La manera más sencilla de especificar una arquitectura de compilación determinada en una ventana de comandos existente consiste en usar el archivo vcvarsall.bat. Use vcvarsall.bat para establecer las variables de entorno con el fin de configurar la línea de comandos para la compilación nativa de 32 bits o de 64 bits. Los argumentos permiten especificar la compilación cruzada en procesadores x86, x64, ARM o ARM64. Puede establecer como destino Microsoft Store, la Plataforma universal de Windows o las plataformas de escritorio de Windows. Incluso puede especificar qué SDK de Windows se va a usar y seleccionar la versión del conjunto de herramientas de la plataforma.

Cuando se usa sin argumentos, vcvarsall.bat configura las variables de entorno para usar el compilador nativo x86 actual para los destinos de escritorio de Windows de 32 bits. Puede agregar argumentos para configurar el entorno de modo que use cualquiera de las herramientas de compilador nativo o cruzado. vcvarsall.bat muestra un mensaje de error si especifica una configuración que no está instalada o disponible en el equipo.

### <a name="vcvarsall-syntax"></a>Sintaxis de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Este argumento opcional especifica la arquitectura de host y de destino que se van a usar. Si no se especifica *architecture*, se usa el entorno de compilación predeterminado. Se admiten estos argumentos:

|*architecture*|Compilador|Arquitectura del equipo host|Arquitectura de salida de compilación (destino)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 nativo de 32 bits|x86, x64|x86|
|**x86\_amd64** o **x86\_x64**|x64 en x86 cruzado|x86, x64|x64|
|**x86_arm**|ARM en x86 cruzado|x86, x64|ARM|
|**x86_arm64**|ARM64 en x86 cruzado|x86, x64|ARM64|
|**amd64** o **x64**|x64 nativo de 64 bits|x64|x64|
|**amd64\_x86** o **x64\_x86**|x86 en x64 cruzado|x64|x86|
|**amd64\_arm** o **x64\_arm**|ARM en x64 cruzado|x64|ARM|
|**amd64\_arm64** o **x64\_arm64**|ARM64 en x64 cruzado|x64|ARM64|

*platform_type*<br/>
Este argumento opcional permite especificar **store** o **uwp** como el tipo de plataforma. De forma predeterminada, el entorno se configura para compilar aplicaciones de escritorio o de consola.

*winsdk_version*<br/>
Especifica, de manera opcional, la versión de Windows SDK que se va a usar. De forma predeterminada, se usa el Windows SDK que se ha instalado más recientemente. Para especificar la versión de Windows SDK, puede usar un número completo de Windows SDK 10, como **10.0.10240.0**, o especificar **8.1** para usar Windows SDK 8.1.

*vcversion*<br/>
Especifica, de manera opcional, el conjunto de herramientas del compilador de Visual Studio que se van a usar. De forma predeterminada, se configura el entorno para usar el conjunto de herramientas del compilador de Visual Studio actual.

::: moniker range=">= vs-2019"

Use **-vcvars_ver=14.2x.yyyyy** para especificar una versión determinada del conjunto de herramientas del compilador de Visual Studio 2019.

Use **-vcvars_ver=14.16** para especificar la versión más reciente del conjunto de herramientas del compilador de Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Use **-vcvars_ver=14.16** para especificar la versión más reciente del conjunto de herramientas del compilador de Visual Studio 2017.

Use **-vcvars_ver=14.1x.yyyyy** para especificar una versión determinada del conjunto de herramientas del compilador de Visual Studio 2017.

::: moniker-end

Use **-vcvars_ver=14.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2015.

#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a><a name="vcvarsall"></a> Para configurar el entorno de compilación en una ventana del símbolo del sistema existente

1. En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. Después, vuelva a usar CD para cambiar al subdirectorio que contiene los archivos de comandos específicos de la configuración. Para Visual Studio 2019 y Visual Studio 2017, use el subdirectorio *VC\\Auxiliary\\Build*. Para Visual Studio 2015, use el subdirectorio *VC*.

1. Escriba el comando para el entorno de desarrollo preferido. Por ejemplo, para compilar código ARM para UWP en una plataforma de 64 bits mediante la versión más reciente del SDK de Windows y del conjunto de herramientas del compilador de Visual Studio, use esta línea de comandos:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Crear su propio acceso directo del símbolo del sistema

::: moniker range=">= vs-2019"

Abra el cuadro de diálogo Propiedades para un acceso directo del símbolo del sistema para desarrolladores para ver el destino del comando usado. Por ejemplo, el destino del acceso directo **Símbolo del sistema de las herramientas nativas x64 para VS 2019** es algo parecido a esto:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Abra el cuadro de diálogo Propiedades para un acceso directo del símbolo del sistema para desarrolladores para ver el destino del comando usado. Por ejemplo, el destino del acceso directo **Símbolo del sistema de las herramientas nativas x64 para VS 2017** es algo parecido a esto:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Abra el cuadro de diálogo Propiedades para un acceso directo del símbolo del sistema para desarrolladores para ver el destino del comando usado. Por ejemplo, el destino del acceso directo **Símbolo del sistema de las herramientas nativas x64 para VS2015** es algo parecido a esto:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

Los archivos por lotes específicos de la arquitectura establecen el parámetro *arquitectura* y llaman a vcvarsall.bat. Puede pasar las mismas opciones a estos archivos por lotes, del mismo modo que los pasa a vcvarsall.bat, o puede simplemente llamar a vcvarsall.bat directamente. Para especificar parámetros para su propio acceso directo de comandos, agréguelos al final del comando con comillas dobles. Por ejemplo, este es un acceso directo para compilar código ARM para UWP en una plataforma de 64 bits, con la versión más reciente del SDK de Windows. Para usar un conjunto anterior de herramientas del compilador, especifique el número de versión. Use algo parecido a este destino de comando en el acceso directo:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Ajuste la ruta de acceso para reflejar el directorio de instalación de Visual Studio. El archivo vcvarsall.bat tiene información adicional sobre los números de versión específicos.

## <a name="command-line-tools"></a>Herramientas de la línea de comandos

Para compilar un proyecto de C/C++ en el símbolo del sistema, Visual Studio proporciona estas herramientas de línea de comandos:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.

[Vínculo](reference/linking.md)<br/>
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Use MSBuild (msbuild.exe) y un archivo de proyecto (.vcxproj) para configurar una compilación e invocar el conjunto de herramientas indirectamente. Equivale a ejecutar el proyecto **Build** o el comando **Build Solution** en el IDE de Visual Studio. La ejecución de MSBuild desde la línea de comandos es un escenario avanzado y no se suele recomendar.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Use DEVENV (devenv.exe) combinado con un modificador de la línea de comandos, como **/Build** o **/Clean**, para ejecutar determinados comandos de compilación sin mostrar el IDE de Visual Studio. En general, se prefiere DEVENV a usar MSBuild directamente, porque puede dejar que Visual Studio controle las complejidades de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Use NMAKE (nmake.exe) en Windows para compilar proyectos de C++ basados en un archivo Make tradicional.

Cuando se compila en la línea de comandos, el comando F1 no está disponible para obtener ayuda instantánea. En su lugar, puede usar un motor de búsqueda para obtener información sobre advertencias, errores y mensajes, o puede usar los archivos de ayuda sin conexión. Para usar la búsqueda en [docs.microsoft.com](https://docs.microsoft.com/cpp/), use el cuadro de búsqueda de la parte superior de la página.

## <a name="in-this-section"></a>En esta sección

En estos artículos se muestra cómo compilar aplicaciones en la línea de comandos y se describe cómo personalizar el entorno de compilación de la línea de comandos. En algunos de ellos se indica cómo usar conjuntos de herramientas de 64 bits y cómo establecer como destino plataformas x86, x64, ARM y ARM64. También se describe el uso de las herramientas de compilación de línea de comandos MSBuild y NMAKE.

[Tutorial: Compilar un programa nativo de C++ en la línea de comandos](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Ofrece un ejemplo que muestra cómo crear y compilar un programa de C++ en la línea de comandos.

[Tutorial: Compilación de un programa escrito en C en la línea de comandos](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Describe cómo compilar un programa escrito en el lenguaje de programación C.

[Tutorial: Compilación de un programa de C++/CLI en la línea de comandos](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CLI que utilice .NET Framework.

[Tutorial: Compilación de un programa de C++/CX en la línea de comandos](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CX que utilice Windows en tiempo de ejecución.

[Establecer las variables de ruta y entorno para las compilaciones de línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Cómo establecer variables de entorno para usar un conjunto de herramientas de 32 bits o 64 bits que tenga como destino plataformas x86, x64, ARM y ARM64.

[Referencia de NMAKE](reference/nmake-reference.md)<br/>
Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft (NMAKE.EXE).

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)<br/>
Proporciona vínculos a artículos en los que se explica cómo usar msbuild.exe desde la línea de comandos.

## <a name="related-sections"></a>Secciones relacionadas

[/MD, /MT, /LD (usar la biblioteca en tiempo de ejecución)](reference/md-mt-ld-use-run-time-library.md)<br/>
Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.

[Opciones del compilador de C/C++](reference/compiler-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C++, y CL.exe.

[Opciones del enlazador MSVC](reference/linker-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.

[Herramientas de generación MSVC adicionales](reference/c-cpp-build-tools.md)<br/>
Proporciona vínculos a las herramientas de compilación de C/C++ que se incluyen en Visual Studio.

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)
