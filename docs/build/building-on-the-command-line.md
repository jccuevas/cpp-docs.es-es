---
title: Utilice Microsoft C++ conjunto de herramientas de la línea de comandos
description: Use la cadena de herramientas del Compilador de Microsoft Visual C++ (MSVC) desde la línea de comandos fuera del IDE de Visual Studio.
ms.custom: conceptual
ms.date: 06/06/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: b5e9bf266d79ee86cae84535641a52c7c52be391
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821140"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Utilice Microsoft C++ conjunto de herramientas de la línea de comandos

Con las herramientas incluidas en Visual Studio, puede compilar aplicaciones de C y C++ en la línea de comandos. Microsoft C++ compiladoras (MSVC) es también puede descargar como un paquete independiente de la [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) página. Forma parte de la **Build Tools para Visual Studio** paquete. Puede elegir descargar sólo las herramientas que necesita para C++ desarrollo.

## <a name="how-to-use-the-command-line-tools"></a>Cómo usar las herramientas de línea de comandos

Al elegir una de las cargas de trabajo de C++ en el Instalador de Visual Studio, instala el *conjunto de herramientas de la plataforma* Visual Studio. Un conjunto de herramientas de plataforma tiene la de C y C++ herramientas para una versión específica de Visual Studio. Las herramientas incluyen el C /C++ compiladores, enlazadores, ensambladores y otras herramientas de compilación y las bibliotecas de búsqueda de coincidencias. Puede usar todas estas herramientas en la línea de comandos. También utilizan internamente por el IDE de Visual Studio. Existen compiladores hospedados x86 y hospedadas en x64 64 independientes y herramientas para crear código para x86, x 64, ARM y ARM64 destinos. Cada conjunto de herramientas para una arquitectura de compilación de destino y de host en particular se almacena en su propio directorio.

Para que las herramientas funcionen correctamente, es necesario especificar varias variables específicas del entorno. Estas variables se usan para agregar las herramientas para la ruta de acceso y para establecer incluyen archivo, archivo de biblioteca y ubicaciones de SDK. Para que sea fácil establecer estas variables de entorno, el instalador crea *archivos de comandos* personalizados, o archivos por lotes, durante la instalación. Puede ejecutar uno de estos archivos de comandos para establecer un host específico y arquitectura de la compilación de destino, versión del SDK de Windows y el conjunto de herramientas de plataforma. Para mayor comodidad, el programa de instalación también crea accesos directos en el menú Inicio. Los métodos abreviados de inician windows de símbolo del sistema para desarrolladores mediante el uso de estos archivos de comandos para combinaciones concretas de host y de destino. Estos métodos abreviados Asegúrese de que todas las variables de entorno necesarias son establecido y listo para su uso.

Las variables de entorno necesarias son específicas para la instalación y la arquitectura de compilación que elija. También podría cambiarse las actualizaciones del producto. Por este motivo se recomienda usar un archivo de acceso directo o un comando de símbolo del sistema instalados, en lugar de establecer las variables de entorno usted mismo. Para obtener más información, consulte [establecer las variables de entorno y la ruta de acceso para las compilaciones de línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md).

Los conjuntos de herramientas, archivos de comandos y los accesos directos instalados dependen de procesador del equipo y las opciones que seleccionó durante la instalación. Siempre se instalan las herramientas de x86 hospedados y herramientas multiplataforma que compilación código x86 y x64. Si tiene Windows de 64 bits, también se instalan las herramientas hospedadas en x64 64 y herramientas multiplataforma que compilación código x86 y x64. Si elige opcional C++ herramientas de la plataforma Universal de Windows y, a continuación, las herramientas de x86 y x64 que compilación código ARM y ARM64 también se instalan. Puede que otras cargas de trabajo instalen herramientas adicionales.

## <a name="developer_command_prompt_shortcuts"></a> Accesos directos del símbolo del sistema para desarrolladores

Los accesos directos del símbolo del sistema se instalan en una carpeta específica de la versión de Visual Studio en el menú Inicio. Esta es una lista de los accesos directos básicos del símbolo del sistema y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x86**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x64**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x86_x64**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x64_x86**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x86 de 32 bits.

::: moniker range=">= vs-2019"

Los nombres de carpeta y el método abreviado de menú de inicio varían dependiendo de la versión instalada de Visual Studio. Si establece uno, también dependen de la instalación **sobrenombre**. Por ejemplo, suponga que ha instalado Visual Studio de 2019, y se le asignó un sobrenombre de *más reciente*. El acceso directo del símbolo para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2019 (más reciente)** , en una carpeta denominada **2019 de Visual Studio**.

::: moniker-end
::: moniker range="= vs-2017"

Los nombres de carpeta y el método abreviado de menú de inicio varían dependiendo de la versión instalada de Visual Studio. Si establece uno, también dependen de la instalación **sobrenombre**. Por ejemplo, supongamos que ha instalado Visual Studio 2017, y se le asignó un sobrenombre de *más reciente*. El acceso directo del símbolo para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2017 (versión más reciente)** , en una carpeta denominada **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Los nombres de carpeta y el método abreviado de menú de inicio varían dependiendo de la versión instalada de Visual Studio. Por ejemplo, supongamos que ha instalado Visual Studio 2015. El acceso directo del símbolo para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2015**.

::: moniker-end

## <a name="developer_command_prompt"></a> Para abrir una ventana del símbolo del sistema para desarrolladores

1. En el escritorio, abra el menú **Inicio** de Windows y desplácese para buscar y abrir la carpeta de la versión de Visual Studio, como por ejemplo, **Visual Studio 2019**.

1. En la carpeta, elija **Símbolo del sistema para desarrolladores** de su versión de Visual Studio. Este acceso directo inicia una ventana del símbolo del sistema para desarrolladores que usa las herramientas nativas x86 de la arquitectura de compilación predeterminada de 32 bits para compilar código nativo x86 de 32 bits. Si prefiere una arquitectura de compilación no predeterminada, elija uno de los símbolos del sistema de herramientas nativas o cruzadas para especificar la arquitectura de host y de destino.

Para conocer una manera incluso más rápida abrir un símbolo del sistema para desarrolladores, escriba *símbolo* en el cuadro de búsqueda en el escritorio. A continuación, elija el resultado deseado.

## <a name="developer_command_file_locations"></a> Ubicaciones de archivos de comandos para desarrolladores

Si prefiere configurar el entorno de compilación en una ventana de símbolo del sistema existente, puede usar uno de los archivos de comandos creados por el instalador. Se recomienda que establecer el entorno en una nueva ventana de símbolo del sistema. No recomendamos que cambie los entornos más adelante en la misma ventana de comandos.

::: moniker range=">= vs-2019"

La ubicación del archivo de comandos depende de la versión de Visual Studio que ha instalado y tomadas durante la instalación. Para Visual Studio 2019, la ubicación de instalación típica en un sistema de 64 bits está en \\archivos de programa (x86)\\Microsoft Visual Studio\\2019\\*edition*. *Edición* puede ser Community, Professional, Enterprise, BuildTools u otro alias proporcionado.

::: moniker-end
::: moniker range="= vs-2017"

La ubicación del archivo de comandos depende de la versión de Visual Studio que ha instalado y tomadas durante la instalación. Para Visual Studio 2017, la ubicación de instalación típica en un sistema de 64 bits está en \\archivos de programa (x86)\\Microsoft Visual Studio\\2017\\*edition*. *Edición* puede ser Community, Professional, Enterprise, BuildTools u otro alias proporcionado.

::: moniker-end
::: moniker range="< vs-2017"

La ubicación del comando archivo depende de la versión de Visual Studio y el directorio de instalación. Visual Studio 2015, la ubicación de instalación típica es en \\archivos de programa (x86)\\14.0 de Microsoft Visual Studio.

::: moniker-end

El archivo de comandos del símbolo del sistema de desarrollador principal, VsDevCmd.bat, se encuentra en el Common7\\subdirectorio Tools. Cuando se especifica ningún parámetro, Establece el entorno para usar las herramientas nativas de x86 para compilar 32-bit x86 código.

::: moniker range=">= vs-2017"

Varios archivos de comandos están disponibles para configurar las arquitecturas de compilación concreta. Los archivos de comandos disponibles dependen de las opciones que se ha instalado y las cargas de trabajo de Visual Studio. En Visual Studio 2017 y Visual Studio de 2019, encontrará en el circuito virtual\\auxiliar\\subdirectorio de compilación.

::: moniker-end
::: moniker range="< vs-2017"

Varios archivos de comandos están disponibles para configurar las arquitecturas de compilación concreta. Los archivos de comandos disponibles dependen de las opciones que se ha instalado y las cargas de trabajo de Visual Studio. En Visual Studio 2015, se encuentra en el VC, VC\\bin o VC\\bin\\*arquitectura* subdirectorios, donde *arquitectura* es uno de nativo o Opciones del compilador cruzado.

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
|**vcvarsall.bat**| Usar parámetros para especificar las arquitecturas de host y de destino, el SDK de Windows y opciones de plataforma. Para obtener una lista de las opciones admitidas, realice una llamada mediante el parámetro **/help**.|

> [!CAUTION]
> El archivo vcvarsall.bat y otros archivos de comandos de Visual Studio pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el instalador de Visual Studio para reemplazar el archivo que falta.
>
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si se instala la versión actual de Visual Studio en un equipo que también tiene una versión anterior de Visual Studio, no ejecute vcvarsall.bat o cualquier otro archivo de comandos de Visual Studio de versiones diferentes en la misma ventana del símbolo del sistema.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Usar las herramientas de desarrollo en una ventana de comandos existente

La manera más sencilla de especificar una arquitectura de compilación determinada en una ventana de comandos existente consiste en usar el archivo vcvarsall.bat. Utilizar vcvarsall.bat para establecer las variables de entorno para configurar la línea de comandos para la compilación nativa de 32 bits o 64 bits. Argumentos le permiten especificar la compilación cruzada para x86, x 64, ARM, ARM64 procesadores o. Puede tener como destino plataformas de Microsoft Store, la plataforma Universal de Windows o el escritorio de Windows. Incluso puede especificar qué SDK de Windows para usar y seleccione la versión de herramientas de plataforma.

Cuando se utiliza sin argumentos, vcvarsall.bat configura las variables de entorno para usar el compilador nativo x86 actual para los destinos de escritorio de Windows de 32 bits. Puede agregar argumentos para configurar el entorno para usar cualquiera de nativo o entre las herramientas del compilador. vcvarsall.bat muestra un mensaje de error si se especifica una configuración que no está instalada o disponible en el equipo.

### <a name="vcvarsall-syntax"></a>Sintaxis de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Este argumento opcional especifica la arquitectura de host y de destino que se van a usar. Si *arquitectura* no se especifica, se usa el entorno de compilación predeterminada. Se admiten estos argumentos:

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

Use **-vcvars_ver = 14.2 x .yyyyy** para especificar una versión específica del conjunto de herramientas del compilador de Visual Studio de 2019.

Use **-vcvars_ver = 14.16** para especificar la versión más reciente del conjunto de herramientas del compilador de Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Use **-vcvars_ver = 14.16** para especificar la versión más reciente del conjunto de herramientas del compilador de Visual Studio 2017.

Use **-vcvars_ver = 14,1 x .yyyyy** para especificar una versión específica del conjunto de herramientas del compilador de Visual Studio 2017.

::: moniker-end

Use **-vcvars_ver = 14.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Para configurar el entorno de compilación en una ventana del símbolo del sistema existente

1. En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. Después, vuelva a usar CD para cambiar al subdirectorio que contiene los archivos de comandos específicos de la configuración. 2019 de Visual Studio y Visual Studio 2017, use el *VC\\auxiliar\\compilar* subdirectorio. Para Visual Studio 2015, use el *VC* subdirectorio.

1. Escriba el comando para el entorno de desarrollo preferido. Por ejemplo, para compilar código ARM para UWP en una plataforma de 64 bits, con la más reciente Windows SDK y Visual Studio del compilador conjunto de herramientas, puede usar esta línea de comandos:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Crear su propio acceso directo del símbolo del sistema

::: moniker range=">= vs-2019"

Abra el cuadro de diálogo de propiedades para un acceso directo del símbolo para desarrolladores ver el destino del comando utilizado. Por ejemplo, el destino del acceso directo **Símbolo del sistema de las herramientas nativas x64 para VS 2019** es algo parecido a esto:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Abra el cuadro de diálogo de propiedades para un acceso directo del símbolo para desarrolladores ver el destino del comando utilizado. Por ejemplo, el destino de la **x64 nativo símbolo de herramientas para VS 2017** acceso directo es algo parecido a:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Abra el cuadro de diálogo de propiedades para un acceso directo del símbolo para desarrolladores ver el destino del comando utilizado. Por ejemplo, el destino de la **VS2015 x64 símbolo herramientas nativas** acceso directo es algo parecido a:

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64`

::: moniker-end

Los archivos por lotes específicos de la arquitectura establecen el parámetro *arquitectura* y llaman a vcvarsall.bat. Puede pasar las mismas opciones para estos archivos por lotes que se pasaría a vcvarsall.bat o, simplemente puede llamar directamente vcvarsall.bat. Para especificar parámetros para su propio acceso directo de comandos, agréguelos al final del comando con comillas dobles. Por ejemplo, este es un acceso directo para compilar código ARM para UWP en una plataforma de 64 bits, con el último SDK de Windows. Para usar un conjunto de herramientas del compilador anterior, especifique el número de versión. Use algo parecido a este destino de comando en el acceso directo:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.16"`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.0"`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64 -vcvars_ver=12.0`

::: moniker-end

Ajuste la ruta de acceso para reflejar el directorio de instalación de Visual Studio. El archivo vcvarsall.bat tiene información adicional sobre los números de versión específicos.

## <a name="command-line-tools"></a>Herramientas de la línea de comandos

Para crear una C /C++ proyecto en un símbolo del sistema, Visual Studio proporciona estas herramientas de línea de comandos:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.

[Vínculo](reference/linking.md)<br/>
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Use MSBuild (msbuild.exe) y un archivo de proyecto (.vcxproj) para configurar una compilación e invocar el conjunto de herramientas indirectamente. Equivale a ejecutar el **compilar** proyecto o **compilar solución** comando en el IDE de Visual Studio. Ejecutar MSBuild desde la línea de comandos es un escenario avanzado y normalmente no se recomienda.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Utilice DEVENV (devenv.exe) combinado con un conmutador de línea de comandos como **/Build** o **/limpiar** para ejecutar determinados comandos de compilación sin mostrar el IDE de Visual Studio. En general, DEVENV es preferible con respecto a MSBuild directamente, porque puede dejar que Visual Studio controlan las complejidades de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Use NMAKE (nmake.exe) en Windows para compilar proyectos de C++ basados en un archivo Make tradicional.

Cuando se compila en la línea de comandos, el comando F1 no está disponible para obtener ayuda de instantánea. En su lugar, puede usar un motor de búsqueda para obtener información sobre advertencias, errores y mensajes, o puede usar los archivos de ayuda sin conexión. Para usar la búsqueda en [docs.microsoft.com](https://docs.microsoft.com/cpp/), utilice el cuadro de búsqueda en la parte superior de la página.

## <a name="in-this-section"></a>En esta sección

Estos artículos muestran cómo compilar aplicaciones en la línea de comandos y describen cómo personalizar el entorno de compilación de línea de comandos. Algunos muestran cómo utilizar conjuntos de herramientas de 64 bits y de destino x86, x 64, ARM, ARM64 plataformas y. También se describe el uso de las herramientas de compilación de línea de comandos MSBuild y NMAKE.

[Tutorial: Compilación de un programa nativo de C++ en la línea de comandos](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Proporciona un ejemplo que muestra cómo crear y compilar un C++ programa en la línea de comandos.

[Tutorial: Compilar un programa de C en la línea de comandos](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Describe cómo compilar un programa escrito en el lenguaje de programación C.

[Tutorial: Compilación de un programa de C++/CLI en la línea de comandos](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CLI que utilice .NET Framework.

[Tutorial: Compilación de un programa de C++/CX en la línea de comandos](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CX que utilice Windows en tiempo de ejecución.

[Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Cómo establecer variables de entorno para usar un conjunto de herramientas de 32 bits o 64 bits al destino x86, x64, ARM, ARM64 plataformas y.

[Referencia de NMAKE](reference/nmake-reference.md)<br/>
Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft (NMAKE.EXE).

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)<br/>
Proporciona vínculos a artículos en los que se explica cómo usar msbuild.exe desde la línea de comandos.

## <a name="related-sections"></a>Secciones relacionadas

[/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](reference/md-mt-ld-use-run-time-library.md)<br/>
Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.

[Opciones del compilador de C/C++](reference/compiler-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C++, y CL.exe.

[Opciones del enlazador MSVC](reference/linker-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.

[Herramientas de compilación de MSVC adicionales](reference/c-cpp-build-tools.md)<br/>
Proporciona vínculos a las herramientas de compilación de C/C++ que se incluyen en Visual Studio.

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)
