---
title: Usar el conjunto de herramientas MSVC desde la línea de comandos - Visual Studio
description: Utilice la cadena de herramientas de compilador de Microsoft C++ (MSVC) desde la línea de comandos fuera del IDE de Visual Studio.
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 5f9ac1e4753fdba412af26bcc45022dee354cacf
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877131"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>Usar el conjunto de herramientas MSVC desde la línea de comandos

Puede crear aplicaciones de C y C++ en la línea de comandos mediante las herramientas que se incluyen en Visual Studio. También puede descargar el conjunto de herramientas del compilador como un paquete independiente desde el [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) página. Forma parte de la **Build Tools para Visual Studio** del paquete; puede elegir descargar sólo las herramientas que necesita para C++ desarrollo.

## <a name="how-to-use-the-command-line-tools"></a>Cómo usar las herramientas de línea de comandos

Al elegir una de las cargas de trabajo de C++ en el instalador de Visual Studio, instala Visual Studio *conjunto de herramientas de plataforma*. Un conjunto de herramientas de plataforma tiene herramientas de C y C++ para una versión específica de Visual Studio, incluidos los compiladores de C o C++, vinculadores, ensambladores y otras herramientas de compilación, así como las bibliotecas de búsqueda de coincidencias. Puede usar todas estas herramientas en la línea de comandos, y también se usan internamente por el IDE de Visual Studio. Existen compiladores hospedados x86 y hospedadas en x64 64 independientes y herramientas para crear código para x86, x 64, ARM y ARM64 destinos. Cada conjunto de herramientas para una arquitectura de compilación concreta de host y de destino se almacena en su propio directorio.

Los conjuntos de herramientas del compilador que se instalan dependen de procesador del equipo y las opciones seleccionadas durante la instalación. Como mínimo, se instalan las herramientas de 32 bits x86 hospedado que generación código x86 nativo de 32 bits y entre las herramientas que compilación código x64 nativo de 64 bits. Si tiene Windows de 64 bits, también se instalan las herramientas hospedadas en x64 64 de 64 bits que generación código nativo de 64 bits y entre las herramientas que se basan en código nativo de 32 bits. Si decide instalar las herramientas de C++ Universal Windows Platform opcionales, también se instalan las herramientas nativas de 32 bits y 64 bits que compilación código ARM. Otras cargas de trabajo pueden instalar herramientas adicionales.

## <a name="environment-variables-and-developer-command-prompts"></a>Variables de entorno y los símbolos del sistema para desarrolladores

Para que funcione correctamente, las herramientas requieren varias variables de entorno específico debe establecerse. Se utilizan para agregarlos a la ruta de acceso y establecer incluyen archivo, archivo de biblioteca y ubicaciones de SDK. Para que sea fácil de establecer estas variables de entorno, el instalador crea personalizado *archivos de comandos*, o por lotes, los archivos durante la instalación. Puede ejecutar uno de estos archivos de comandos en una ventana del símbolo del sistema para establecer un host específico y arquitectura de la compilación de destino, versión del SDK de Windows, plataforma de destino y el conjunto de herramientas de plataforma. Para mayor comodidad, el programa de instalación también crea accesos directos en el menú Inicio que iniciar windows de símbolo del sistema para desarrolladores mediante el uso de estos archivos de comandos, por lo que todas las variables de entorno necesarias son la lista usar.

Las variables de entorno necesarias son específicas para la instalación y la arquitectura de compilación que elija y se puede cambiar las actualizaciones del producto. Por lo tanto, se recomienda encarecidamente usar uno de los métodos abreviados del símbolo del sistema instalados o archivos de comandos en lugar de establecer las variables de entorno de Windows. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="developer_command_prompt_shortcuts"></a> Métodos abreviados del símbolo del sistema de desarrollador

Los métodos abreviados de línea de comandos se instalan en una carpeta específica de la versión de Visual Studio en el menú Inicio. Esta es una lista de los accesos directos del símbolo del sistema base y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores** -establece el entorno para usar las herramientas de 32 bits, nativo x86 para compilar código de 32 bits, nativo x86.
- **x86 símbolo herramientas nativas** -establece el entorno para usar las herramientas de 32 bits, nativo x86 para compilar código de 32 bits, nativo x86.
- **x64 símbolo herramientas nativas** -establece el entorno para usar las herramientas de 64 bits, nativo x64 para compilar código de 64 bits, nativo x64.
- **x86_x64 entre las herramientas de símbolo del sistema** -establece el entorno para usar las herramientas de 32 bits, nativo x86 para compilar código de 64 bits, nativo x64.
- **x64_x86 entre las herramientas de símbolo del sistema** -establece el entorno para usar las herramientas de 64 bits, nativo x64 para compilar código de 32 bits, nativo x86.

El inicio menú contextual y carpeta nombres reales varían según la versión de Visual Studio que ha instalado y el alias de instalación si establece uno. Por ejemplo, si tiene instalado Visual Studio 2017 y se ha dado una instalación de sobrenombres de *Preview*, el acceso directo del símbolo para desarrolladores se denomina **símbolo del sistema para desarrolladores para VS 2019**, en un carpeta denominada **2019 de Visual Studio**.

## <a name="developer_command_prompt"></a> Para abrir una ventana de símbolo del sistema para desarrolladores

1. En el escritorio, abra el Windows **iniciar** menú y, a continuación, desplácese para buscar y abrir la carpeta para su versión de Visual Studio, por ejemplo, **2019 de Visual Studio**. En algunas versiones anteriores de Visual Studio, los accesos directos están en una subcarpeta denominada **Visual Studio Tools**.

1. En la carpeta, elija la **símbolo** para su versión de Visual Studio. Este método abreviado inicia una ventana de símbolo del sistema para desarrolladores que utiliza la arquitectura de compilación predeterminado de 32 bits, nativo x86 herramientas para generar código de 32 bits, nativo x86. Si prefiere una arquitectura de compilación no predeterminado, elija uno de nativo o entre herramientas símbolos del sistema para especificar la arquitectura de host y de destino.

Es una forma más rápida para abrir una ventana de símbolo del sistema para desarrolladores escribir *símbolo* en el cuadro de búsqueda en el escritorio, a continuación, elija el resultado deseado.

## <a name="developer_command_file_locations"></a> Ubicaciones de archivos de comandos para desarrolladores

Si prefiere configurar el entorno de arquitectura de compilación en una ventana de símbolo del sistema existente, puede usar uno de los archivos de comandos (archivos por lotes) creado por el instalador para establecer el entorno requerido. Le recomendamos que sólo lo hace en una nueva ventana de símbolo del sistema y no se recomienda cambie los entornos más adelante en la misma ventana de comandos. La ubicación de estos archivos depende de la versión de Visual Studio que haya instalado y en la ubicación y nomenclatura elecciones que ha realizado durante la instalación. Para Visual Studio 2019, la ubicación de instalación típica en un equipo de 64 bits se encuentra en \Program archivos (x86) \Microsoft Visual Studio\2019\\*edition*, donde *edition* puede ser la Comunidad, Professional, Enterprise, BuildTools u otro nombre que proporcionó. La ubicación de Visual Studio 2017 es similar. Para Visual Studio 2015, la ubicación de instalación típica es en \Program (x86) \Microsoft 14.0 de Visual Studio.

El archivo de comandos del símbolo del sistema de desarrollador principal, VsDevCmd.bat, se encuentra en el subdirectorio Common7\Tools del directorio de instalación. Cuando se especifica ningún parámetro, esto establece el entorno y el host y el destino de compilación arquitectura para utilizar las herramientas de x86 nativo de 32 bits para compilar los 32 bits x86 código.

Archivos de comandos adicionales están disponibles para configurar las arquitecturas de compilación concreta, dependiendo de la arquitectura del procesador y las opciones que se ha instalado y las cargas de trabajo de Visual Studio. En Visual Studio 2017 y Visual Studio de 2019, estos se encuentran en el subdirectorio VC\Auxiliary\Build del directorio de instalación de Visual Studio. En Visual Studio 2015, estos se encuentran en el VC, VC\bin o VC\bin\\*arquitecturas* subdirectorios del directorio de instalación, donde *arquitecturas* es uno de nativo o Opciones del compilador cruzado. Estos archivos de comandos establece los parámetros predeterminados y llamar a VsDevCmd.bat para configurar el entorno de arquitectura de compilación especificada. Una instalación típica puede incluir estos archivos de comandos:

|Archivo de comandos|Arquitecturas de host y de destino|
|---|---|
|**vcvars32.bat**| Usar las herramientas de x86 nativo de 32 bits para compilar los 32 bits x86 código.|
|**vcvars64.bat**| Usar las herramientas de x64 nativo de 64 bits para compilar 64-bit x64 código.|
|**vcvarsx86_amd64.bat**| Usar las herramientas cruzadas de x86 nativo de 32 bits para compilar 64-bit x64 código.|
|**vcvarsamd64_x86.bat**| Usar las herramientas cruzadas de 64 bits nativo x64 para compilar los 32 bits x86 código.|
|**vcvarsx86_arm.bat**| Use las herramientas cruzadas de x86 nativo de 32 bits para compilar código ARM.|
|**vcvarsamd64_arm.bat**| Use las herramientas cruzadas de 64 bits nativo x64 para compilar código ARM.|
|**vcvarsall.bat**| Usar parámetros para especificar el host y las arquitecturas de destino, así como las opciones de SDK y plataforma. Para obtener una lista de opciones admitidas, llame a mediante un **/ayuda** parámetro.|

> [!CAUTION]
> Otros archivos de comandos de Visual Studio y el archivo vcvarsall.bat pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el instalador de Visual Studio para reemplazar el archivo que falta.
>
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si la versión actual de Visual Studio está instalada en un equipo que también tiene una versión anterior de Visual Studio, no ejecute vcvarsall.bat u otro archivo de comandos de Visual Studio de versiones diferentes en la misma ventana de símbolo del sistema.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Usar las herramientas de desarrollo en una ventana de comandos existente

Es la manera más sencilla para especificar la arquitectura de una compilación determinada en una ventana de comandos existentes usar el archivo vcvarsall.bat. Puede utilizar vcvarsall.bat para establecer las variables de entorno para configurar la línea de comandos para la compilación nativa de 32 bits o 64 bits, o para la compilación cruzada para procesadores ARM; x64 o x86 para tener como destino Microsoft Store, la plataforma Universal de Windows o plataformas de escritorio de Windows; para especificar qué SDK de Windows para su uso; y para especificar la versión de herramientas de plataforma. Si no se proporcionan argumentos, vcvarsall.bat configura las variables de entorno para usar el compilador nativo de 32 bits actual para x86 destinos de escritorio de Windows. Sin embargo, puede usar para configurar cualquiera de nativo o entre las herramientas del compilador. Si especifica una configuración de compilador que no está instalada o no está disponible en la arquitectura de su equipo de compilación, se muestra un mensaje de error.

### <a name="vcvarsall-syntax"></a>sintaxis de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
Este argumento opcional especifica la arquitectura de host y de destino para usar. Si *arquitectura* no se especifica, se usa el entorno de compilación predeterminada. Se admiten los siguientes argumentos:

|*architecture*|Compilador|Arquitectura del equipo host|Crear la arquitectura de salida (destino)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 nativo de 32 bits|x86, x64|x86|
|**x86\_amd64** o **x86\_x64**|cross x64 en x86|x86, x64|x64|
|**x86_arm**|ARM en x86 cruzado|x86, x64|ARM|
|**x86_arm64**|ARM64 en x86 cruzadas|x86, x64|ARM64|
|**AMD64** o **x64**|x64 nativo de 64 bits|x64|x64|
|**AMD64\_x86** o **x64\_x86**|cross x86 en x64|x64|x86|
|**AMD64\_arm** o **x64\_arm**|ARM en x64 cruzadas|x64|ARM|
|**AMD64\_arm64** o **x64\_arm64**|ARM64 en x64 cruzadas|x64|ARM64|

*platform_type*<br/>
Este argumento opcional permite especificar **almacenar** o **uwp** como el tipo de plataforma. De forma predeterminada, se establece el entorno para compilar aplicaciones de escritorio o la consola.

*winsdk_version*<br/>
Opcionalmente, especifica la versión del SDK de Windows para usar. De forma predeterminada, se usa el SDK de Windows más reciente instalado. Para especificar la versión del SDK de Windows, puede usar un número completo de SDK de Windows 10 como **10.0.10240.0**, o especifique **8.1** para usar el SDK de Windows 8.1.

*vcversion*<br/>
Opcionalmente, especifica el conjunto de herramientas del compilador de Visual Studio para usar. De forma predeterminada, el entorno se establece para usar el conjunto de herramientas de compilador de Visual Studio actual. Use **-vcvars_ver = 14.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2015 o **-vcvars_ver = 15.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2017.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Para configurar el entorno de compilación en una ventana de símbolo del sistema existente

1. En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. A continuación, utilice de nuevo CD para cambiar al subdirectorio que contiene los archivos de comandos específicos de la configuración. Para Visual Studio 2017 y 2019, este es el subdirectorio de VC\Auxiliary\Build. Para Visual Studio 2015, utilice el subdirectorio de VC.

1. Escriba el comando para su entorno de desarrollo preferido. Por ejemplo, para compilar código ARM para UWP en una plataforma de 64 bits mediante el SDK de Windows más reciente y el conjunto de herramientas del compilador de Visual Studio de 2019, use esta línea de comandos:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Crear su propio acceso directo del símbolo

Si abre el cuadro de diálogo de propiedades para uno de los accesos directos existentes símbolo del sistema de desarrollador, puede ver el destino del comando utilizado. Por ejemplo, el destino de la **x64 nativo símbolo de herramientas para VS 2019** acceso directo es algo parecido a:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

Conjunto de archivos de lote específicos de la arquitectura del *arquitectura* vcvarsall.bat parámetro y la llamada. Puede pasar las mismas opciones adicionales para estos archivos por lotes que se pasaría a vcvarsall.bat o, simplemente puede llamar directamente vcvarsall.bat. Para especificar parámetros para su propio acceso directo de comando, agréguelos al final del comando de comillas dobles. Por ejemplo, para configurar un acceso directo para compilar código ARM para UWP en una plataforma de 64 bits mediante el SDK de Windows más reciente y un conjunto de herramientas del compilador anterior a la versión actual, deberá especificar el número de versión. Use algo parecido a este destino de comando en el método abreviado:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=15.0"`

Debe ajustar la ruta de acceso para reflejar el directorio de instalación de Visual Studio. El archivo vcvarsall.bat tiene información adicional acerca de los números de versión específica.

## <a name="command-line-tools"></a>Herramientas de línea de comandos

Para compilar un proyecto de C o C++ en la línea de comandos, Visual Studio proporciona estas herramientas de línea de comandos:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.

[Vínculo](reference/linking.md)<br/>
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Usar MSBuild (msbuild.exe) y un archivo de proyecto (.vcxproj) para configurar una compilación e invocar el conjunto de herramientas indirectamente. Esto equivale a ejecutar el **compilar** proyecto o **compilar solución** comando en el IDE de Visual Studio. Ejecutar MSBuild desde la línea de comandos es un escenario avanzado y generalmente no se recomienda.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Utilice DEVENV (devenv.exe) combinado con un conmutador de línea de comandos, por ejemplo, **/Build** o **/limpiar**: para realizar determinados comandos de compilación sin mostrar el IDE de Visual Studio. En general se prefiere a usar MSBuild directamente porque puede dejar que Visual Studio controlan las complejidades de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Utilice NMAKE (nmake.exe) en Windows para compilar proyectos de C++ en función de un archivo MAKE tradicional.

Cuando se compila en la línea de comandos, el comando F1 no está disponible para obtener ayuda de instantánea. En su lugar, puede usar un motor de búsqueda para obtener información sobre advertencias, errores y mensajes, o puede usar los archivos de Ayuda sin conexión. Para usar la búsqueda en [docs.microsoft.com](https://docs.microsoft.com/cpp/), escriba la cadena de búsqueda en el cuadro de búsqueda en la parte superior de la página.

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
Describe cómo iniciar una ventana de símbolo del sistema que tiene las variables de entorno necesarias establecido para las compilaciones de línea de comandos que tienen como destino x86, x64 y las plataformas de ARM mediante el uso de un conjunto de herramientas de 32 bits o 64 bits.

[Referencia de NMAKE](reference/nmake-reference.md)<br/>
Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft (NMAKE.EXE).

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)<br/>
Proporciona vínculos a artículos que tratan cómo usar msbuild.exe desde la línea de comandos.

## <a name="related-sections"></a>Secciones relacionadas

[/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](reference/md-mt-ld-use-run-time-library.md)<br/>
Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.

[Opciones del compilador de C o C++](reference/compiler-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C++, y CL.exe.

[Opciones del enlazador MSVC](reference/linker-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.

[Herramientas de generación MSVC adicionales](reference/c-cpp-build-tools.md)<br/>
Proporciona vínculos a la C o C++ crear herramientas que se incluyen en Visual Studio.

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)