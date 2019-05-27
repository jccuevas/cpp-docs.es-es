---
title: Uso del conjunto de herramientas de MSVC desde la línea de comandos - Visual Studio
description: Use la cadena de herramientas del Compilador de Microsoft Visual C++ (MSVC) desde la línea de comandos fuera del IDE de Visual Studio.
ms.custom: conceptual
ms.date: 05/16/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 97626455ace0d3ad47b9011594e82c144d7ea27d
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837125"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>Uso del conjunto de herramientas de MSVC desde la línea de comandos

Con las herramientas incluidas en Visual Studio, puede compilar aplicaciones de C y C++ en la línea de comandos. También puede descargar el conjunto de herramientas del compilador como un paquete independiente desde la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/). Forma parte del paquete **Herramientas de compilación para Visual Studio**; puede elegir descargar solo las herramientas que necesita para el desarrollo con C++.

## <a name="how-to-use-the-command-line-tools"></a>Cómo usar las herramientas de línea de comandos

Al elegir una de las cargas de trabajo de C++ en el Instalador de Visual Studio, instala el *conjunto de herramientas de la plataforma* Visual Studio. Un conjunto de herramientas de plataforma tiene todas las herramientas de C y C++ para una versión específica de Visual Studio, incluidos los compiladores, los enlazadores, los ensambladores y otras herramientas de compilación de C /C++, así como las bibliotecas de búsqueda de coincidencias. Puede usar todas estas herramientas en la línea de comandos y el IDE de Visual Studio también puede usarlas internamente. Existen compiladores independientes hospedados en x86 y x64, y herramientas para compilar código para destinos como x86, x64, ARM y ARM64. Cada conjunto de herramientas para una arquitectura de compilación de destino y de host en particular se almacena en su propio directorio.

Los conjuntos de herramientas del compilador que se instalan dependen del procesador del equipo y de las opciones seleccionadas durante la instalación. Como mínimo, se instalan las herramientas hospedadas en x86 de 32 bits que compilan código nativo x86 de 32 bits, así como las herramientas cruzadas que compilan código nativo x64 de 64 bits. Si tiene instalado Windows de 64 bits, también se instalan las herramientas hospedadas en x64 de 64 bits que compilan código nativo de 64 bits, así como las herramientas cruzadas que compilan código nativo de 32 bits. Si opta por instalar las herramientas opcionales de la Plataforma universal de Windows de C++, también se instalan las herramientas nativas de 32 bits y 64 bits que compilan código ARM. Puede que otras cargas de trabajo instalen herramientas adicionales.

## <a name="environment-variables-and-developer-command-prompts"></a>Variables de entorno y símbolo del sistema para desarrolladores

Para que las herramientas funcionen correctamente, es necesario especificar varias variables específicas del entorno. Se usan para agregarlas a la ruta de acceso y establecer las ubicaciones de los archivos, los archivos de biblioteca y el SDK. Para que sea fácil establecer estas variables de entorno, el instalador crea *archivos de comandos* personalizados, o archivos por lotes, durante la instalación. Puede ejecutar uno de estos archivos de comandos en una ventana del símbolo del sistema para establecer una arquitectura de compilación de host y de destino específica, la versión de Windows SDK, la plataforma de destino y el conjunto de herramientas de la plataforma. Para mayor comodidad, el instalador también crea accesos directos en el menú Inicio para poder iniciar ventanas del símbolo del sistema para desarrolladores mediante estos archivos de comandos, de modo que todas las variables de entorno necesarias estén configuradas y listas para usar.

Las variables de entorno necesarias corresponden específicamente a su instalación y a la arquitectura de compilación que elija, y podrían cambiar con las actualizaciones del producto. Por eso le recomendamos que use uno de los archivos de comandos o los accesos directos del símbolo del sistema que se han instalado, en lugar de configurar las variables de entorno de Windows por su cuenta. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="developer_command_prompt_shortcuts"></a> Accesos directos del símbolo del sistema para desarrolladores

Los accesos directos del símbolo del sistema se instalan en una carpeta específica de la versión de Visual Studio en el menú Inicio. Esta es una lista de los accesos directos básicos del símbolo del sistema y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x86**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x86 de 32 bits.
- **Símbolo del sistema de las herramientas nativas x64**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x86_x64**: configura el entorno para usar herramientas nativas x86 de 32 bits para compilar código nativo x64 de 64 bits.
- **Símbolo del sistema de las herramientas cruzadas x64_x86**: configura el entorno para usar herramientas nativas x64 de 64 bits para compilar código nativo x86 de 32 bits.

La carpeta real del menú Inicio y los nombres de los accesos directos varían según la versión de Visual Studio que haya instalado y el alias de instalación, si configuró uno. Por ejemplo, si tiene instalado Visual Studio 2019 y le ha asignado un alias de instalación *Versión preliminar*, el acceso directo del símbolo del sistema para desarrolladores tendrá el nombre **Símbolo del sistema para desarrolladores para VS 2019**, en una carpeta llamada **Visual Studio 2019**.

## <a name="developer_command_prompt"></a> Para abrir una ventana del símbolo del sistema para desarrolladores

1. En el escritorio, abra el menú **Inicio** de Windows y desplácese para buscar y abrir la carpeta de la versión de Visual Studio, como por ejemplo, **Visual Studio 2019**. En algunas versiones anteriores de Visual Studio, los accesos directos se encuentran en una subcarpeta denominada **Visual Studio Tools**.

1. En la carpeta, elija **Símbolo del sistema para desarrolladores** de su versión de Visual Studio. Este acceso directo inicia una ventana del símbolo del sistema para desarrolladores que usa las herramientas nativas x86 de la arquitectura de compilación predeterminada de 32 bits para compilar código nativo x86 de 32 bits. Si prefiere una arquitectura de compilación no predeterminada, elija uno de los símbolos del sistema de herramientas nativas o cruzadas para especificar la arquitectura de host y de destino.

Una manera aún más rápida de abrir una ventana del símbolo del sistema para desarrolladores consiste en escribir *símbolo del sistema para desarrolladores* en el cuadro de búsqueda del escritorio y, después, elegir el resultado que quiera.

## <a name="developer_command_file_locations"></a> Ubicaciones de archivos de comandos para desarrolladores

Si prefiere configurar el entorno de la arquitectura de compilación en una ventana del símbolo del sistema existente, puede usar uno de los archivos de comandos (archivos por lotes) creado por el instalador para configurar el entorno que necesite. Recomendamos hacer esto solamente en una nueva ventana del símbolo del sistema y no cambiar de entorno más tarde en la misma ventana de comandos. La ubicación de estos archivos depende de la versión de Visual Studio que haya instalado y de la ubicación y los nombres que haya elegido durante la instalación. Para Visual Studio 2019, la ubicación de instalación típica en un equipo de 64 bits es \Archivos de programa (x86)\Microsoft Visual Studio\2019\*edition*, donde *edition* puede ser Community, Professional, Enterprise, BuildTools o cualquier otro nombre que haya proporcionado. La ubicación de Visual Studio 2017 es similar. Para Visual Studio 2015, la ubicación de instalación típica es en \Archivos de programa (x86)\Microsoft Visual Studio 14.0.

El archivo de comandos principal del símbolo del sistema para desarrolladores, VsDevCmd.bat, se encuentra en el subdirectorio Common7\Tools del directorio de instalación. Cuando no se especifica ningún parámetro, esto establece el entorno y las arquitecturas de compilación de host y de destino para usar las herramientas x86 de 32 bits para compilar código x86 de 32 bits.

Hay otros archivos de comandos disponibles para configurar determinadas arquitecturas de compilación, en función de la arquitectura del procesador y las opciones y las cargas de trabajo de Visual Studio que haya instalado. En Visual Studio 2017 y Visual Studio 2019, estos archivos se encuentran en el subdirectorio VC\Auxiliary\Build del directorio de instalación de Visual Studio. En Visual Studio 2015, se encuentran en los subdirectorios VC, VC\bin o VC\bin\\*architectures* del directorio de instalación, donde *architectures* es una de las opciones del compilador nativo o cruzado. Estos archivos de comandos establecen los parámetros predeterminados y llaman a VsDevCmd.bat para configurar el entorno de arquitectura de compilación especificada. Una instalación típica puede incluir estos archivos de comandos:

|Archivo de comandos|Arquitecturas de host y de destino|
|---|---|
|**vcvars32.bat**| Usa las herramientas nativas x86 de 32 bits para compilar código x86 de 32 bits.|
|**vcvars64.bat**| Usa las herramientas nativas x64 de 64 bits para compilar código x64 de 64 bits.|
|**vcvarsx86_amd64.bat**| Usa las herramientas nativas x86 de 32 bits para compilar código x64 de 64 bits.|
|**vcvarsamd64_x86.bat**| Usa las herramientas cruzadas nativas x64 de 64 bits para compilar código x86 de 32 bits.|
|**vcvarsx86_arm.bat**| Usa las herramientas nativas x86 de 32 bits para compilar código ARM.|
|**vcvarsamd64_arm.bat**| Usa las herramientas cruzadas nativas x64 de 64 bits para compilar código ARM.|
|**vcvarsall.bat**| Usa parámetros para especificar las arquitecturas de host y de destino, así como las opciones de SDK y de plataforma. Para obtener una lista de las opciones admitidas, realice una llamada mediante el parámetro **/help**.|

> [!CAUTION]
> El archivo vcvarsall.bat y otros archivos de comandos de Visual Studio pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el instalador de Visual Studio para reemplazar el archivo que falta.
>
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si se instala la versión actual de Visual Studio en un equipo que también tiene una versión anterior de Visual Studio, no ejecute vcvarsall.bat o cualquier otro archivo de comandos de Visual Studio de versiones diferentes en la misma ventana del símbolo del sistema.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Usar las herramientas de desarrollo en una ventana de comandos existente

La manera más sencilla de especificar una arquitectura de compilación determinada en una ventana de comandos existente consiste en usar el archivo vcvarsall.bat. El archivo vcvarsall.bat sirve para lo siguiente: establecer las variables del entorno para configurar la línea de comandos para la compilación nativa de 32 bits o 64 bits, o para la compilación cruzada en procesadores x86, x64 o ARM; admitir plataformas como Microsoft Store, Plataforma universal de Windows o plataformas de escritorio de Windows; especificar qué Windows SDK se usará, y especificar la versión del conjunto de herramientas de la plataforma. Si no se proporcionan argumentos, vcvarsall.bat configura las variables del entorno para usar el compilador nativo de 32 bits actual para los destinos de escritorio de Windows de x86. Pero puede usarlo para configurar cualquiera de las herramientas del compilador nativo o cruzado. Si especifica una configuración de compilación que no se instala ni está disponible en la arquitectura de su equipo de compilación, se muestra un mensaje de error.

### <a name="vcvarsall-syntax"></a>Sintaxis de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=**_vcversion_]

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
Especifica, de manera opcional, el conjunto de herramientas del compilador de Visual Studio que se van a usar. De forma predeterminada, se configura el entorno para usar el conjunto de herramientas del compilador de Visual Studio actual. Use **-vcvars_ver=14.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2015 o **-vcvars_ver=15.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2017.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Para configurar el entorno de compilación en una ventana del símbolo del sistema existente

1. En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. Después, vuelva a usar CD para cambiar al subdirectorio que contiene los archivos de comandos específicos de la configuración. Para Visual Studio 2017 y Visual Studio 2019, es el subdirectorio VC\Auxiliary\Build. Para Visual Studio 2015, use el subdirectorio de VC.

1. Escriba el comando para el entorno de desarrollo preferido. Por ejemplo, para compilar código ARM para UWP en una plataforma de 64 bits mediante la versión más reciente de Windows SDK y del conjunto de herramientas del compilador de Visual Studio 2019, use esta línea de comandos:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Crear su propio acceso directo del símbolo del sistema

Si abre el cuadro de diálogo Propiedades para uno de los accesos directos existentes del símbolo del sistema para desarrolladores, puede ver el destino del comando usado. Por ejemplo, el destino del acceso directo **Símbolo del sistema de las herramientas nativas x64 para VS 2019** es algo parecido a esto:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

Los archivos por lotes específicos de la arquitectura establecen el parámetro *arquitectura* y llaman a vcvarsall.bat. Puede pasar las mismas opciones adicionales a estos archivos por lotes, del mismo modo que los pasa a vcvarsall.bat, o puede simplemente llamar a vcvarsall.bat directamente. Para especificar parámetros para su propio acceso directo de comandos, agréguelos al final del comando con comillas dobles. Por ejemplo, para configurar un acceso directo para compilar código ARM para UWP en una plataforma de 64 bits mediante la versión más reciente de Windows SDK y un conjunto de herramientas del compilador anterior a la versión actual, debe especificar el número de versión. Use algo parecido a este destino de comando en el acceso directo:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=15.0"`

Debe ajustar la ruta de acceso para reflejar el directorio de instalación de Visual Studio. El archivo vcvarsall.bat tiene información adicional sobre los números de versión específicos.

## <a name="command-line-tools"></a>Herramientas de la línea de comandos

Para compilar un proyecto de C/C++ en la línea de comandos, Visual Studio proporciona estas herramientas de línea de comandos:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.

[Vínculo](reference/linking.md)<br/>
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Use MSBuild (msbuild.exe) y un archivo de proyecto (.vcxproj) para configurar una compilación e invocar el conjunto de herramientas indirectamente. Equivale a ejecutar el proyecto **Build** o el comando **Build Solution** en el IDE de Visual Studio. La ejecución de MSBuild desde la línea de comandos es un escenario avanzado y no se suele recomendar.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Use DEVENV (devenv.exe) combinado con un modificador de la línea de comandos (por ejemplo, **/Build** o **/Clean**) para ejecutar determinados comandos de compilación sin mostrar el IDE de Visual Studio. En general se prefiere esto a usar MSBuild directamente porque puede dejar que Visual Studio controle las complejidades de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Use NMAKE (nmake.exe) en Windows para compilar proyectos de C++ basados en un archivo Make tradicional.

Cuando se compila en la línea de comandos, el comando F1 no está disponible para obtener ayuda instantánea. En su lugar, puede usar un motor de búsqueda para obtener información sobre advertencias, errores y mensajes, o puede usar los archivos de ayuda sin conexión. Para usar la búsqueda en [docs.microsoft.com](https://docs.microsoft.com/cpp/), escriba la cadena de búsqueda en el cuadro de búsqueda en la parte superior de la página.

## <a name="in-this-section"></a>En esta sección

En los artículos de esta sección de la documentación se muestra cómo compilar aplicaciones en la línea de comandos, se describe cómo personalizar el entorno de compilación de la línea de comandos para usar conjuntos de herramientas de 64 bits y tener como destinos las plataformas x86, x64 y ARM, y se indica cómo usar las herramientas de compilación de la línea de comandos MSBuild y NMAKE.

[Tutorial: Compilación de un programa nativo de C++ en la línea de comandos](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Ofrece un ejemplo que muestra cómo crear y compilar un programa de C++ sencillo en la línea de comandos.

[Tutorial: Compilar un programa de C en la línea de comandos](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Describe cómo compilar un programa escrito en el lenguaje de programación C.

[Tutorial: Compilación de un programa de C++/CLI en la línea de comandos](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CLI que utilice .NET Framework.

[Tutorial: Compilación de un programa de C++/CX en la línea de comandos](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CX que utilice Windows en tiempo de ejecución.

[Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Describe cómo iniciar una ventana del símbolo del sistema que tenga establecidas las variables de entorno necesarias para realizar desde la línea de comandos compilaciones destinadas a las plataformas x86, x64 y ARM con un conjunto de herramientas de 32 o 64 bits.

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