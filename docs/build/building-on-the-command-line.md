---
title: Usar el conjunto C++ de herramientas de Microsoft desde la línea de comandos
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422905"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Usar el conjunto C++ de herramientas de Microsoft desde la línea de comandos

Con las herramientas incluidas en Visual Studio, puede compilar aplicaciones de C y C++ en la línea de comandos. El conjunto C++ de herramientas del compilador de Microsoft (MSVC) también se puede descargar como un paquete independiente que no incluye el IDE de Visual Studio.

## <a name="download-and-install-the-tools"></a>Descargar e instalar las herramientas

Si ha instalado Visual Studio y una C++ carga de trabajo, tiene todas las herramientas de línea de comandos. Para obtener información sobre cómo instalar C++ y Visual Studio, consulte [instalación C++ de la compatibilidad en Visual Studio](vscpp-step-0-installation.md). Si solo desea el conjunto de herramientas de línea de comandos, descargue las [herramientas de compilación para Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019). Al ejecutar el ejecutable descargado, actualiza y ejecuta el Instalador de Visual Studio. Para instalar solo las herramientas que necesita para C++ el desarrollo, seleccione la **C++** carga de trabajo herramientas de compilación. Puede seleccionar bibliotecas y conjuntos de herramientas opcionales para incluirlos en detalles de la **instalación**. Para compilar código mediante los conjuntos de herramientas de Visual Studio 2015 o 2017, seleccione las herramientas de compilación opcionales MSVC V140 o MSVC v141. Cuando esté satisfecho con sus selecciones, elija **instalar**.

## <a name="how-to-use-the-command-line-tools"></a>Cómo usar las herramientas de línea de comandos

Al elegir una de las cargas de trabajo de C++ en el Instalador de Visual Studio, instala el *conjunto de herramientas de la plataforma* Visual Studio. Un conjunto de herramientas de la plataforma tiene C++ todas las herramientas de C y para una versión específica de Visual Studio. Entre las herramientas se incluyen CC++ /compiladores, vinculadores, ensambladores y otras herramientas de compilación, y bibliotecas coincidentes. Puede usar todas estas herramientas en la línea de comandos. También se usan internamente en el IDE de Visual Studio. Existen compiladores y herramientas independientes hospedados en x86 y en x64 para compilar código para los destinos x86, x64, ARM y ARM64. Cada conjunto de herramientas para una arquitectura de compilación de destino y de host en particular se almacena en su propio directorio.

Para que las herramientas funcionen correctamente, es necesario especificar varias variables específicas del entorno. Estas variables se usan para agregar las herramientas a la ruta de acceso y para establecer el archivo de inclusión, el archivo de biblioteca y las ubicaciones del SDK. Para que sea fácil establecer estas variables de entorno, el instalador crea *archivos de comandos* personalizados, o archivos por lotes, durante la instalación. Puede ejecutar uno de estos archivos de comandos para establecer un host específico y la arquitectura de compilación de destino, la versión de Windows SDK y el conjunto de herramientas de la plataforma. Para mayor comodidad, el instalador también crea accesos directos en el menú Inicio. Los accesos directos inician ventanas del símbolo del sistema de desarrollador mediante estos archivos de comandos para combinaciones específicas de host y destino. Estos métodos abreviados garantizan que todas las variables de entorno necesarias estén establecidas y listas para usarse.

Las variables de entorno necesarias son específicas de la instalación y de la arquitectura de compilación que elija. También podrían cambiarse mediante actualizaciones o actualizaciones del producto. Esta es la razón por la que se recomienda usar un archivo de comandos o un acceso directo al símbolo del sistema instalado, en lugar de establecer las variables de entorno usted mismo. Para obtener más información, vea [establecer la ruta de acceso y las variables de entorno para las compilaciones de línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md).

Los conjuntos de herramientas, los archivos de comandos y los métodos abreviados instalados dependen del procesador del equipo y de las opciones que haya seleccionado durante la instalación. Las herramientas hospedadas en x86 y las herramientas cruzadas que compilan el código x86 y x64 siempre están instaladas. Si tiene Windows de 64 bits, también se instalan las herramientas hospedadas en x64 y las herramientas cruzadas que compilan el código x86 y x64. Si elige las herramientas de C++ plataforma universal de Windows opcionales, las herramientas de x86 y x64 que compilan el código ARM y ARM64 también se instalan. Puede que otras cargas de trabajo instalen herramientas adicionales.

## <a name="developer_command_prompt_shortcuts"></a> Accesos directos del símbolo del sistema para desarrolladores

Los accesos directos del símbolo del sistema se instalan en una carpeta específica de la versión de Visual Studio en el menú Inicio. Esta es una lista de los accesos directos básicos del símbolo del sistema y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x86**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x64**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x86_x64**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x64_x86**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x86 de 32 bits.

::: moniker range=">= vs-2019"

La carpeta del menú Inicio y los nombres de acceso directo varían en función de la versión instalada de Visual Studio. Si establece uno, también dependen del **sobrenombre**de instalación. Por ejemplo, supongamos que ha instalado Visual Studio 2019 y le ha asignado un alias de la *versión más reciente*. El acceso directo del símbolo del sistema para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2019 (latest)** , en una carpeta denominada **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

La carpeta del menú Inicio y los nombres de acceso directo varían en función de la versión instalada de Visual Studio. Si establece uno, también dependen del **sobrenombre**de instalación. Por ejemplo, supongamos que ha instalado Visual Studio 2017 y le ha asignado un alias de la *versión más reciente*. El acceso directo del símbolo del sistema para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2017 (latest)** , en una carpeta denominada **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

La carpeta del menú Inicio y los nombres de acceso directo varían en función de la versión instalada de Visual Studio. Por ejemplo, supongamos que instaló Visual Studio 2015. El acceso directo del símbolo del sistema para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2015**.

::: moniker-end

### <a name="developer_command_prompt"></a> Para abrir una ventana del símbolo del sistema para desarrolladores

1. En el escritorio, abra el menú **Inicio** de Windows y desplácese para buscar y abrir la carpeta de la versión de Visual Studio, como por ejemplo, **Visual Studio 2019**.

1. En la carpeta, elija **Símbolo del sistema para desarrolladores** de su versión de Visual Studio. Este acceso directo inicia una ventana del símbolo del sistema para desarrolladores que usa las herramientas nativas x86 de la arquitectura de compilación predeterminada de 32 bits para compilar código nativo x86 de 32 bits. Si prefiere una arquitectura de compilación no predeterminada, elija uno de los símbolos del sistema de herramientas nativas o cruzadas para especificar la arquitectura de host y de destino.

Para una manera incluso más rápida de abrir un símbolo del sistema para desarrolladores, escriba *símbolo del sistema para desarrolladores* en el cuadro búsqueda en el escritorio. A continuación, elija el resultado que desee.

## <a name="developer_command_file_locations"></a> Ubicaciones de archivos de comandos para desarrolladores

Si prefiere establecer el entorno de compilación en una ventana de símbolo del sistema existente, puede usar uno de los archivos de comandos creados por el instalador. Se recomienda establecer el entorno en una nueva ventana del símbolo del sistema. No se recomienda cambiar más adelante los entornos en la misma ventana de comandos.

::: moniker range=">= vs-2019"

La ubicación del archivo de comandos depende de la versión de Visual Studio que haya instalado y de las opciones que haya realizado durante la instalación. Para Visual Studio 2019, la ubicación de instalación típica en un sistema de 64 bits está en \\archivos de programa (x86)\\Microsoft Visual Studio\\2019\\*Edition*. La *edición* puede ser Community, Professional, Enterprise, BuildTools u otro alias proporcionado.

::: moniker-end
::: moniker range="= vs-2017"

La ubicación del archivo de comandos depende de la versión de Visual Studio que haya instalado y de las opciones que haya realizado durante la instalación. Para Visual Studio 2017, la ubicación de instalación típica en un sistema de 64 bits está en \\archivos de programa (x86)\\Microsoft Visual Studio\\2017\\*Edition*. La *edición* puede ser Community, Professional, Enterprise, BuildTools u otro alias proporcionado.

::: moniker-end
::: moniker range="< vs-2017"

La ubicación del archivo de comandos depende de la versión de Visual Studio y del directorio de instalación. En Visual Studio 2015, la ubicación de instalación típica está en \\archivos de programa (x86)\\Microsoft Visual Studio 14,0.

::: moniker-end

El archivo de comandos principal del símbolo del sistema para desarrolladores, VsDevCmd. bat, se encuentra en el subdirectorio herramientas de Common7\\. Cuando no se especifica ningún parámetro, establece el entorno para usar las herramientas nativas x86 para compilar código x86 de 32 bits.

::: moniker range=">= vs-2017"

Hay más archivos de comandos disponibles para configurar arquitecturas de compilación específicas. Los archivos de comandos disponibles dependen de las cargas de trabajo y las opciones de Visual Studio que haya instalado. En Visual Studio 2017 y Visual Studio 2019, los encontrará en el\\de VC\\subdirectorio Build.

::: moniker-end
::: moniker range="< vs-2017"

Hay más archivos de comandos disponibles para configurar arquitecturas de compilación específicas. Los archivos de comandos disponibles dependen de las cargas de trabajo y las opciones de Visual Studio que haya instalado. En Visual Studio 2015, se encuentran en los subdirectorios VC, VC\\bin o VC\\bin\\*Architecture* , donde *Architecture* es una de las opciones nativas o entre compiladores.

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
|**vcvarsall.bat**| Use los parámetros para especificar las arquitecturas de host y de destino, Windows SDK y las opciones de plataforma. Para obtener una lista de las opciones admitidas, realice una llamada mediante el parámetro **/help**.|

> [!CAUTION]
> El archivo vcvarsall.bat y otros archivos de comandos de Visual Studio pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el instalador de Visual Studio para reemplazar el archivo que falta.
>
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si se instala la versión actual de Visual Studio en un equipo que también tiene una versión anterior de Visual Studio, no ejecute vcvarsall.bat o cualquier otro archivo de comandos de Visual Studio de versiones diferentes en la misma ventana del símbolo del sistema.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Usar las herramientas de desarrollo en una ventana de comandos existente

La manera más sencilla de especificar una arquitectura de compilación determinada en una ventana de comandos existente consiste en usar el archivo vcvarsall.bat. Use vcvarsall. bat para establecer las variables de entorno con el fin de configurar la línea de comandos para la compilación nativa de 32 bits o de 64 bits. Los argumentos permiten especificar la compilación cruzada en procesadores x86, x64, ARM o ARM64. Puede tener como destino Microsoft Store, Plataforma universal de Windows o plataformas de escritorio de Windows. Incluso puede especificar qué Windows SDK usar y seleccionar la versión del conjunto de herramientas de la plataforma.

Cuando se usa sin argumentos, vcvarsall. bat configura las variables de entorno para utilizar el compilador actual de x86-nativo para los destinos de escritorio de Windows de 32 bits. Puede Agregar argumentos para configurar el entorno con el fin de usar cualquiera de las herramientas de compilador nativa o cruzada. vcvarsall. bat muestra un mensaje de error si especifica una configuración que no está instalada o disponible en el equipo.

### <a name="vcvarsall-syntax"></a>Sintaxis de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Este argumento opcional especifica la arquitectura de host y de destino que se van a usar. Si no se especifica la *arquitectura* , se usa el entorno de compilación predeterminado. Se admiten estos argumentos:

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

Use **-vcvars_ver = 14.2 x. yyyyy** para especificar una versión específica del conjunto de herramientas del compilador de Visual Studio 2019.

Use **-vcvars_ver = 14.16** para especificar la versión más reciente del conjunto de herramientas del compilador de Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Use **-vcvars_ver = 14.16** para especificar la versión más reciente del conjunto de herramientas del compilador de Visual Studio 2017.

Use **-vcvars_ver = 14,1 x. yyyyy** para especificar una versión específica del conjunto de herramientas del compilador de Visual Studio 2017.

::: moniker-end

Use **-vcvars_ver = 14.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2015.

#### <a name="vcvarsall"></a>Para configurar el entorno de compilación en una ventana de símbolo del sistema existente

1. En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. Después, vuelva a usar CD para cambiar al subdirectorio que contiene los archivos de comandos específicos de la configuración. Para Visual Studio 2019 y Visual Studio 2017, use el subdirectorio\\de la *compilación de VC\\auxiliar* . Para Visual Studio 2015, use el subdirectorio *VC* .

1. Escriba el comando para el entorno de desarrollo preferido. Por ejemplo, para compilar código ARM para UWP en una plataforma de 64 bits, con el conjunto de herramientas de compilador de Visual Studio y el Windows SDK más reciente, use esta línea de comandos:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Crear su propio acceso directo del símbolo del sistema

::: moniker range=">= vs-2019"

Abra el cuadro de diálogo de propiedades de un acceso directo del símbolo del sistema para desarrolladores para ver el destino del comando usado. Por ejemplo, el destino del acceso directo **Símbolo del sistema de las herramientas nativas x64 para VS 2019** es algo parecido a esto:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Abra el cuadro de diálogo de propiedades de un acceso directo del símbolo del sistema para desarrolladores para ver el destino del comando usado. Por ejemplo, el destino de la **símbolo del sistema de las herramientas nativas x64 para el acceso directo de VS 2017** es similar a:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Abra el cuadro de diálogo de propiedades de un acceso directo del símbolo del sistema para desarrolladores para ver el destino del comando usado. Por ejemplo, el destino del acceso directo **VS2015 símbolo del sistema de las herramientas nativas x64** es similar a:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

Los archivos por lotes específicos de la arquitectura establecen el parámetro *arquitectura* y llaman a vcvarsall.bat. Puede pasar las mismas opciones a estos archivos por lotes que pasaría a vcvarsall. bat o simplemente llamar a vcvarsall. bat directamente. Para especificar parámetros para su propio acceso directo de comandos, agréguelos al final del comando con comillas dobles. Por ejemplo, este es un acceso directo para compilar código ARM para UWP en una plataforma de 64 bits, con la Windows SDK más reciente. Para usar un conjunto de herramientas de compilador anterior, especifique el número de versión. Use algo parecido a este destino de comando en el acceso directo:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Ajuste la ruta de acceso para reflejar el directorio de instalación de Visual Studio. El archivo vcvarsall.bat tiene información adicional sobre los números de versión específicos.

## <a name="command-line-tools"></a>Herramientas de línea de comandos

Para compilar unC++ proyecto de C/en un símbolo del sistema, Visual Studio proporciona estas herramientas de línea de comandos:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.

[Vínculo](reference/linking.md)<br/>
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Use MSBuild (msbuild.exe) y un archivo de proyecto (.vcxproj) para configurar una compilación e invocar el conjunto de herramientas indirectamente. Es equivalente a ejecutar el comando **compilar proyecto o** **compilar solución** en el IDE de Visual Studio. Ejecutar MSBuild desde la línea de comandos es un escenario avanzado y no suele ser recomendable.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Use DEVENV (devenv. exe) combinado con un modificador de la línea de comandos como **/Build** o **/Clean** para ejecutar determinados comandos de compilación sin mostrar el IDE de Visual Studio. En general, DEVENV es preferible usar MSBuild directamente, ya que puede dejar que Visual Studio controle las complejidades de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Use NMAKE (nmake.exe) en Windows para compilar proyectos de C++ basados en un archivo Make tradicional.

Al compilar en la línea de comandos, el comando F1 no está disponible para la ayuda instantánea. En su lugar, puede usar un motor de búsqueda para obtener información sobre advertencias, errores y mensajes, o puede usar los archivos de ayuda sin conexión. Para usar la búsqueda en [docs.Microsoft.com](https://docs.microsoft.com/cpp/), use el cuadro de búsqueda de la parte superior de la página.

## <a name="in-this-section"></a>En esta sección

En estos artículos se muestra cómo compilar aplicaciones en la línea de comandos y se describe cómo personalizar el entorno de compilación de la línea de comandos. Algunos muestran cómo usar los conjuntos de herramientas de 64 bits y las plataformas x86, x64, ARM y ARM64 de destino. También se describe el uso de las herramientas de compilación de línea de comandos MSBuild y NMAKE.

[Tutorial: compilar C++ un programa nativo en la línea de comandos](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Proporciona un ejemplo que muestra cómo crear y compilar C++ un programa en la línea de comandos.

[Tutorial: Compilar un programa escrito en C en la línea de comandos](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Describe cómo compilar un programa escrito en el lenguaje de programación C.

[Tutorial: compilar un C++programa/CLI en la línea de comandos](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CLI que utilice .NET Framework.

[Tutorial: compilar un C++programa/CX en la línea de comandos](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CX que utilice Windows en tiempo de ejecución.

[Establecer la ruta de acceso y las variables de entorno para compilaciones de línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Cómo establecer variables de entorno para usar un conjunto de herramientas de 32 bits o 64 bits para tener como destino las plataformas x86, x64, ARM y ARM64.

[Referencia de NMAKE](reference/nmake-reference.md)<br/>
Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft (NMAKE.EXE).

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)<br/>
Proporciona vínculos a artículos en los que se explica cómo usar msbuild.exe desde la línea de comandos.

## <a name="related-sections"></a>Secciones relacionadas

[/MD,/MT,/LD (usar la biblioteca en tiempo de ejecución)](reference/md-mt-ld-use-run-time-library.md)<br/>
Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.

[Opciones deC++ C/Compiler](reference/compiler-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C++, y CL.exe.

[Opciones del vinculador MSVC](reference/linker-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.

[Herramientas de generación MSVC adicionales](reference/c-cpp-build-tools.md)<br/>
Proporciona vínculos a las herramientas de compilación de C/C++ que se incluyen en Visual Studio.

## <a name="see-also"></a>Consulte también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)
