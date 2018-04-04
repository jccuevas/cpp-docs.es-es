---
title: Compilar el código de C o C++ en la línea de comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc4ec1034d4d77542df4a4241ad3ba5c087602ae
ms.sourcegitcommit: 78e5e5cdbafd29e2a6ccf68d4cce215136952907
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>Compilar el código de C o C++ en la línea de comandos

Puede compilar aplicaciones de C y C++ en la línea de comandos mediante el uso de herramientas que se incluyen en Visual Studio.

## <a name="how-to-get-the-command-line-tools"></a>Cómo obtener las herramientas de línea de comandos

Al elegir una de las cargas de trabajo de C++ en el instalador de Visual Studio, instala Visual Studio *conjunto de herramientas de plataforma*. Un conjunto de herramientas de plataforma dispone de herramientas de C y C++ para una versión específica de Visual Studio, incluidos los compiladores de C o C++, vinculadores, ensambladores y otras herramientas de compilación, así como las bibliotecas de búsqueda de coincidencias. Puede usar todas estas herramientas en la línea de comandos, y también se usan internamente por el IDE de Visual Studio. Hay ARM64 destinos y herramientas para compilar código para ARM x86, x 64 y los compiladores de hospedados en x86 y x64 hospedado independientes. Cada conjunto de herramientas para una determinada arquitectura de compilación de host y de destino se almacena en su propio directorio.

Para que funcione correctamente, las herramientas requieren varias variables de entorno específico para establecerse. Se utilizan para agregarlos a la ruta de acceso y establecer incluir ubicaciones de SDK, archivo de biblioteca y archivos. Para que sea más sencillo definir estas variables de entorno, el instalador crea personalizado *archivos de comandos*, o los archivos por lotes, durante la instalación. Puede ejecutar uno de estos archivos de comandos en una ventana del símbolo del sistema para establecer un host específico y arquitectura de compilación de destino, versión del SDK de Windows, plataforma de destino y el conjunto de herramientas de plataforma. Para mayor comodidad, el programa de instalación también crea accesos directos en el menú de inicio (o la página de inicio en Windows 8.x) que está al principio ventanas del símbolo de programador mediante el uso de estos archivos de comandos, por lo que todas las variables de entorno necesarias son establecido y preparado para su uso.

Las variables de entorno necesarias son específicas para la instalación y la arquitectura de compilación que elija y se puede cambiar las actualizaciones del producto. Por lo tanto, se recomienda usar uno de los métodos abreviados del símbolo instalados o archivos de comandos en lugar de establecer las variables de entorno de Windows. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Los conjuntos de herramientas de línea de comandos, archivos de comandos y métodos abreviados del símbolo que se instalan dependen de procesador del equipo y las opciones seleccionadas durante la instalación. Como mínimo, se instalan las herramientas de x86 hospedados de 32 bits que compilación código x86 nativo de 32 bits y cross herramientas que generan código x64 nativo de 64 bits. Si tiene Windows de 64 bits, también se instalan las herramientas de x64 hospedado de 64 bits que compilación código nativo de 64 bits y cross herramientas que genera código nativo de 32 bits. Si decide instalar las herramientas de plataforma Universal de Windows de C++ opcionales, también se instalan las herramientas nativas de 32 bits y 64 bits que compilación código ARM. Otras cargas de trabajo pueden instalar herramientas adicionales.

## <a name="developer-command-prompt-shortcuts"></a>Métodos abreviados del símbolo de desarrollador

Los métodos abreviados de línea de comandos se instalan en una carpeta de Visual Studio específicos de la versión en el menú de inicio. Esta es una lista de los accesos directos del símbolo del sistema base y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores** -establece el entorno para usar herramientas de 32 bits, nativo x86 para compilar el código de 32 bits, nativo x86.
- **x86 símbolo herramientas nativas** -establece el entorno para usar herramientas de 32 bits, nativo x86 para compilar el código de 32 bits, nativo x86.
- **x64 símbolo herramientas nativas** -establece el entorno para usar las herramientas de 64 bits, x64 nativo para compilar el código de 64 bits, nativo x64.
- **x86_x64 entre herramientas de símbolo del sistema** -establece el entorno para usar herramientas de 32 bits, nativo x86 para compilar el código de 64 bits, nativo x64.
- **x64_x86 entre herramientas de símbolo del sistema** -establece el entorno para usar las herramientas de 64 bits, x64 nativo para compilar el código de 32 bits, nativo x86.

Los reales nombres de carpeta y el acceso directo de la menú inicio varían según la versión de Visual Studio que tenga instalada y el alias de la instalación si establece uno. Por ejemplo, si tiene Visual Studio de 2017 instalado y se ha especificado una instalación de sobrenombres de *vista previa*, el acceso directo del símbolo para desarrolladores se denomina **símbolo del sistema para desarrolladores de VS 2017 (versión preliminar)**, en una carpeta denominada **2017 de Visual Studio**.

Si ha instalado el [Build Tools para Visual Studio de 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) (que también incluye el conjunto de herramientas del compilador de Visual Studio 2015 Update 3), solo el nativo específicas de la arquitectura o entre herramientas se instalan las opciones de símbolo para desarrolladores y no en la ficha general **símbolo** acceso directo.

<a name="developer_command_prompt"></a>
### <a name="to-open-a-developer-command-prompt-window"></a>Para abrir una ventana de símbolo del sistema para desarrolladores

1. En el escritorio, abra las ventanas **iniciar** menú y, a continuación, desplácese para buscar y abrir la carpeta para su versión de Visual Studio, por ejemplo, **2017 de Visual Studio**. En algunas versiones anteriores de Visual Studio, los métodos abreviados se encuentran en una subcarpeta denominada **Visual Studio Tools**.

1. En la carpeta, elija la **símbolo** para su versión de Visual Studio. Este acceso directo inicia una ventana de símbolo del sistema para desarrolladores que usa la arquitectura predeterminada de la compilación de herramientas de 32 bits, nativo x86 para compilar el código de 32 bits, nativo x86. Si prefiere una arquitectura de compilación no predeterminado, elija uno de nativo o entre herramientas de símbolo del sistema para especificar la arquitectura de host y de destino.

Es una forma más rápida para abrir una ventana de símbolo del sistema para desarrolladores escribir *símbolo* en el cuadro de búsqueda en el escritorio, a continuación, elija el resultado deseado.

## <a name="developer-command-files-and-locations"></a>Ubicaciones y los archivos de comandos de desarrollador

Si lo prefiere establecer el entorno de generación de arquitectura en una ventana de símbolo del sistema existente, puede usar uno de los archivos de comandos (archivos por lotes) creado por el instalador para establecer el entorno necesario. Solo se recomienda haga esto en una nueva ventana de símbolo del sistema y no se recomienda los entornos de conmutador posteriores en la misma ventana de comandos. La ubicación de estos archivos depende de la versión de Visual Studio que tenga instalada y de ubicación y nomenclaturas decisiones tomadas durante la instalación. Para Visual Studio de 2017, la ubicación de instalación típica en un equipo de 64 bits se encuentra en \Program archivos (x86) \Microsoft Visual Studio\2017\\*edición*, donde *edición* puede ser la Comunidad, Professional, Enterprise, BuildTools o a otro nombre que proporcionó. Para Visual Studio 2015, la ubicación de instalación típica es \Program Files (x86) \Microsoft 14.0 de Visual Studio.

El archivo de comandos del símbolo del sistema de desarrollador principal, VsDevCmd.bat, se encuentra en el subdirectorio Common7\Tools del directorio de instalación. Cuando se especifica ningún parámetro, se establece el entorno y el host y el destino de la arquitectura para utilizar las herramientas de x86 nativo de 32 bits para generar x86 32 bits de compilación código.

Archivos de comandos adicionales están disponibles para configurar las arquitecturas de compilación concreta, dependiendo de la arquitectura del procesador y las opciones que se ha instalado y las cargas de trabajo de Visual Studio. En Visual Studio de 2017, estos se encuentran en el subdirectorio VC\Auxiliary\Build del directorio de instalación de Visual Studio. En Visual Studio 2015, éstos se encuentran en VC, VC\bin o VC\bin\\*arquitecturas* subdirectorios del directorio de instalación, donde *arquitecturas* es uno de nativo o Opciones del compilador cruzado. Estos archivos de comandos establece los parámetros predeterminados y llamar a VsDevCmd.bat para configurar el entorno de arquitectura de compilación especificada. Una instalación típica puede incluir estos archivos de comandos:

|Archivo de comandos|Arquitecturas de host y de destino|
|---|---|
|**vcvars32.bat**| Usar las herramientas de x86 nativo de 32 bits para generar 32-bit x86 código.|
|**vcvars64.bat**| Usar las herramientas de x64 nativo de 64 bits para generar 64-bit x64 código.|
|**vcvarsx86_amd64.bat**| Usar las herramientas cruzadas de x86 nativo de 32 bits a 64 bits x64 de compilación código.|
|**vcvarsamd64_x86.bat**| Usar las herramientas cruzadas de x64 nativo de 64 bits para crear 32-bit x86 código.|
|**vcvarsx86_arm.bat**| Use las herramientas cruzadas de x86 nativo de 32 bits para generar código ARM.|
|**vcvarsamd64_arm.bat**| Use las herramientas cruzadas de x64 nativo de 64 bits para generar código ARM.|
|**vcvarsall.bat**| Usar parámetros para especificar el host y de arquitecturas de destino, así como las opciones de SDK y plataforma. Para obtener una lista de opciones admitidas, llame a mediante un **/help** parámetro.|

> [!CAUTION]
> El archivo vcvarsall.bat y otros archivos de comandos de Visual Studio pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el instalador de Visual Studio para reemplazar el archivo que falta.
>
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si la versión actual de Visual Studio está instalada en un equipo que también tiene una versión anterior de Visual Studio, no ejecute vcvarsall.bat u otro archivo de comandos de Visual Studio de versiones diferentes en la misma ventana del símbolo del sistema.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Usar las herramientas de desarrollo en una ventana de comandos existente

Es la manera más sencilla para especificar una arquitectura de compilación determinada en una ventana de comandos existentes usar el archivo vcvarsall.bat. Puede utilizar vcvarsall.bat para establecer variables de entorno para configurar la línea de comandos para la compilación nativa de 32 bits o 64 bits, o para la compilación cruzada para x86, x64 o procesadores ARM; para tener como destino Microsoft Store, plataforma Universal de Windows o plataformas de escritorio de Windows; para especificar qué SDK de Windows a utilizar; y para especificar la versión del conjunto de herramientas de plataforma. Si no se proporcionan argumentos, vcvarsall.bat configura las variables de entorno para usar el compilador nativo de 32 bits actual para x86 destinos de escritorio de Windows. Sin embargo, puede utilizarlo para configurar cualquiera de nativo o entre herramientas del compilador. Si se especifica una configuración de compilador que no está instalada o no está disponible en la arquitectura del equipo de compilación, se muestra un mensaje de error.

### <a name="vcvarsall-syntax"></a>sintaxis de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
Este argumento opcional especifica la arquitectura de host y de destino para usar. Si *arquitectura* no se especifica, se utiliza el entorno de compilación de forma predeterminada. Se admiten los siguientes argumentos:

|*architecture*|Compilador|Arquitectura del equipo host|Crear la arquitectura de salida (destino)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 nativo de 32 bits|x86, x64|x86|
|**x86\_amd64** o **x86\_x64**|cross x64 en x86|x86, x64|x64|
|**x86_arm**|ARM en x86 cruzado|x86, x64|ARM|
|**x86_arm64**|ARM64 en x86 cross|x86, x64|ARM64|
|**AMD64** o **x64**|x64 nativo de 64 bits|x64|x64|
|**AMD64\_x86** o **x64\_x86**|cross x86 en x64|x64|x86|
|**AMD64\_arm** o **x64\_arm**|ARM en x64 cross|x64|ARM|
|**AMD64\_arm64** o **x64\_arm64**|ARM64 en x64 cross|x64|ARM64|

*platform_type*<br/>
Este argumento opcional permite especificar **almacenar** o **uwp** como el tipo de plataforma. De forma predeterminada, se establece el entorno para compilar aplicaciones de escritorio o la consola.

*winsdk_version*<br/>
Opcionalmente, especifica la versión del SDK de Windows para usar. De forma predeterminada, se usa el SDK de Windows más reciente instalada. Para especificar la versión del SDK de Windows, puede usar un número completo de SDK de Windows 10 como **10.0.10240.0**, o especifique **8.1** para usar el SDK de Windows 8.1.

*vcversion*<br/>
Opcionalmente, especifica el conjunto de herramientas del compilador de Visual Studio para usar. De forma predeterminada, el entorno está configurado para usar el conjunto de herramientas de compilador de Visual Studio de 2017 actual. Use **-vcvars_ver = 14.0** para especificar el conjunto de herramientas del compilador de Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Para configurar el entorno de compilación en una ventana de símbolo del sistema existente

1. En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. A continuación, utilice de nuevo CD para cambiar al subdirectorio que contiene los archivos de comandos específicas de la configuración. Para Visual Studio de 2017, este es el subdirectorio VC\Auxiliary\Build. Para Visual Studio 2015, use el subdirectorio de VC.

1. Escriba el comando para el entorno del desarrollador preferido. Por ejemplo, para compilar código ARM para UWP en una plataforma de 64 bits mediante el SDK de Windows más reciente y el conjunto de herramientas del compilador de Visual Studio de 2017 RTM, utilice esta línea de comandos:

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>Crear su propio método abreviado de la ventana símbolo del sistema

Si abre el cuadro de diálogo de propiedades para uno de los accesos directos existentes símbolo de desarrollador, puede ver el destino del comando utilizado. Por ejemplo, el destino de la **x64 herramientas símbolo nativas para VS 2017** acceso directo es parecido al:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

Conjunto de archivos de lote específicos de la arquitectura del *arquitectura* vcvarsall.bat parámetro y llame al método. Puede pasar las mismas opciones adicionales para estos archivos por lotes como pasaría a vcvarsall.bat o, simplemente puede llamar vcvarsall.bat directamente. Para especificar parámetros para sus propios métodos abreviados comando, agréguela al final del comando de comillas dobles. Por ejemplo, para configurar un acceso directo para compilar código ARM para UWP en una plataforma de 64 bits mediante el SDK de Windows más reciente y el conjunto de herramientas del compilador de Visual Studio de 2017 RTM, usar algo parecido a este destino del comando en el método abreviado:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

Se debe ajustar la ruta de acceso para reflejar el directorio de instalación de Visual Studio.

## <a name="command-line-tools"></a>Herramientas de línea de comandos

Para compilar un proyecto de C o C++ en la línea de comandos, Visual Studio proporciona estas herramientas de línea de comandos:

[CL](../build/reference/compiling-a-c-cpp-program.md)<br/>
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.

[Link](../build/reference/linking.md)<br/>
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Usar MSBuild (msbuild.exe) para compilar proyectos de Visual C++ y soluciones de Visual Studio. Esto equivale a ejecutar el **generar** proyecto o **generar solución** comando en el IDE de Visual Studio.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Utilice DEVENV (devenv.exe) combinado con un modificador de línea de comandos, por ejemplo, **/generar** o **/limpiar**: para realizar determinados comandos de compilación sin mostrar el IDE de Visual Studio.

[NMAKE](../build/nmake-reference.md)<br/>
Utilice NMAKE (nmake.exe) para automatizar las tareas que compilan proyectos de Visual C++ mediante el uso de un archivo MAKE tradicional.

Al compilar en la línea de comandos, el comando F1 no está disponible para obtener ayuda de instantánea. En su lugar, puede usar un motor de búsqueda para obtener información acerca de las advertencias, errores y mensajes, o puede usar los archivos de Ayuda sin conexión. Para usar la búsqueda en [docs.microsoft.com](https://docs.microsoft.com/cpp/), escriba la cadena de búsqueda en el cuadro de búsqueda en la parte superior de la página.

## <a name="in-this-section"></a>En esta sección

En los artículos de esta sección de la documentación se muestra cómo compilar aplicaciones en la línea de comandos, se describe cómo personalizar el entorno de compilación de la línea de comandos para usar conjuntos de herramientas de 64 bits y tener como destinos las plataformas x86, x64 y ARM, y se indica cómo usar las herramientas de compilación de la línea de comandos MSBuild y NMAKE.

[Tutorial: Compilar un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Ofrece un ejemplo que muestra cómo crear y compilar un programa de C++ sencillo en la línea de comandos.

[Tutorial: Compilar un programa de C en la línea de comandos](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Describe cómo compilar un programa escrito en el lenguaje de programación C.

[Tutorial: Compilar un programa de C++/CLI en la línea de comandos](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CLI que utilice .NET Framework.

[Tutorial: Compilar un programa de C++/CX en la línea de comandos](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Describe cómo crear y compilar un programa de C++/CX que utilice Windows Runtime.

[Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Describe cómo iniciar una ventana de símbolo del sistema que tiene las variables de entorno necesarias establecido para las compilaciones de línea de comandos que tienen como destino x86, x64, plataformas y ARM con un conjunto de herramientas de 32 bits o 64 bits.

[Referencia de NMAKE](../build/nmake-reference.md)<br/>
Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft (NMAKE.EXE).

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Proporciona vínculos a artículos en los que se explica cómo utilizar MSBuild.EXE.

## <a name="related-sections"></a>Secciones relacionadas

[/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](../build/reference/md-mt-ld-use-run-time-library.md)<br/>
Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.

[Opciones del compilador de C o C++](../build/reference/compiler-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C++, y CL.exe.

[Opciones del vinculador](../build/reference/linker-options.md)<br/>
Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.

[Herramientas de compilación de C/C++](../build/reference/c-cpp-build-tools.md)<br/>
Proporciona vínculos a C/C++ de compilación de herramientas que se incluyen en Visual Studio.

## <a name="see-also"></a>Vea también

[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)