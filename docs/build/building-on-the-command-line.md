---
title: "Compilar el código de C o C++ en la línea de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5780fb725ab9ccfbba189894c22c991c415f6c2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>Compilar el código de C o C++ en la línea de comandos

Con las herramientas incluidas en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], puede compilar aplicaciones de C y C++ en la línea de comandos.

Cuando se elige una de las cargas de trabajo de C++ en el [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Installer, instala un conjunto de herramientas que incluye los compiladores de C o C++, vinculadores, y otras herramientas de compilación. Estas herramientas se usan por el [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE y también pueden utilizarse en la línea de comandos. Hay compiladores hospedados en x86 y x64 hospedado independientes y las herramientas para generar código para destinos ARM, x64 y x86. Cada conjunto de herramientas para una determinada arquitectura de compilación de host y de destino se almacena en su propio directorio. Para que funcione correctamente, estas herramientas requieren varias variables de entorno concretas para agregarlos a la ruta de acceso y establecer incluyen ubicaciones de SDK, archivo de biblioteca y archivos. Para que sea más sencillo definir estas variables de entorno, el programa de instalación crea archivos de comandos personalizada, también conocido como archivos por lotes, durante la instalación. Puede ejecutar uno de estos archivos de comandos en una ventana del símbolo del sistema para establecer una arquitectura de compilación concreta. Para mayor comodidad, el programa de instalación también crea accesos directos en el menú de inicio (o la página de inicio en Windows 8.x) que está al principio ventanas del símbolo de programador mediante el uso de estos archivos de comandos, por lo que todas las variables de entorno necesarias son establecido y preparado para su uso. 

Las variables de entorno necesarias son específicas para la instalación y la arquitectura de compilación que elija y se puede cambiar las actualizaciones del producto. Por lo tanto, se recomienda usar uno de los métodos abreviados del símbolo instalados o archivos de comandos en lugar de establecer las variables de entorno de Windows. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  

Los conjuntos de herramientas de línea de comandos, archivos de comandos y métodos abreviados del símbolo que se instalan dependen de procesador del equipo y las opciones seleccionadas durante la instalación. Como mínimo, se instalan las herramientas de x86 hospedados de 32 bits que compilación código x86 nativo de 32 bits y cross herramientas que generan código x64 nativo de 64 bits. Si tiene Windows de 64 bits, también se instalan las herramientas de x64 hospedado de 64 bits que compilación código nativo de 64 bits y cross herramientas que genera código nativo de 32 bits. Si decide instalar las herramientas de plataforma Universal de Windows de C++ opcionales, también se instalan las herramientas nativas de 32 bits y 64 bits que compilación código ARM. Otras cargas de trabajo pueden instalar herramientas adicionales.

<a name="developer_command_prompt_shortcuts"></a>
## <a name="developer-command-prompt-shortcuts"></a>Métodos abreviados del símbolo de desarrollador

Los métodos abreviados de línea de comandos se instalan en una versión específica [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] carpeta en el menú de inicio. Esta es una lista de los accesos directos del símbolo del sistema base y las arquitecturas de compilación que admiten:

- **Símbolo del sistema para desarrolladores** establece el entorno para usar herramientas de 32 bits, nativo x86 para compilar el código de 32 bits, nativo x86.  
- **x86 símbolo herramientas nativas** establece el entorno para usar herramientas de 32 bits, nativo x86 para compilar el código de 32 bits, nativo x86.  
- **x64 símbolo herramientas nativas** establece el entorno para usar las herramientas de 64 bits, x64 nativo para compilar el código de 64 bits, nativo x64.  
- **x86_x64 entre herramientas de símbolo del sistema** establece el entorno para usar herramientas de 32 bits, nativo x86 para compilar el código de 64 bits, nativo x64.  
- **x64_x86 entre herramientas de símbolo del sistema** establece el entorno para usar las herramientas de 64 bits, x64 nativo para compilar el código de 32 bits, nativo x86.  

El inicio menú contextual y carpeta nombres reales varían según la versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] ha instalado y la instalación alias si establece uno. Por ejemplo, si tiene Visual Studio de 2017 instalado y se le ha dado una instalación sobrenombre de 15.3, el acceso directo del símbolo para desarrolladores se denomina **símbolo del sistema para desarrolladores de VS 2017 (15.3)**, en una carpeta denominada  **Visual Studio de 2017**. 

Si ha instalado el [Build Tools para Visual Studio de 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) o [herramientas de compilación de Visual C++ 2015](http://landinghub.visualstudio.com/visual-cpp-build-tools) edition, solo puede haber nativo específico o entre herramientas opciones de línea de comandos del programador. 

<a name="developer_command_prompt"></a>
## <a name="to-open-a-developer-command-prompt-window"></a>Para abrir una ventana de símbolo del sistema para desarrolladores  
  
1.  En el escritorio, abra las ventanas **iniciar** menú y, a continuación, desplácese para buscar y abrir la carpeta para su versión de Visual Studio, por ejemplo, **2017 de Visual Studio**. En algunas versiones anteriores de Visual Studio, los métodos abreviados se encuentran en una subcarpeta denominada **Visual Studio Tools**.  
  
2.  En la carpeta, elija la **símbolo** para su versión de Visual Studio. Este acceso directo inicia una ventana de símbolo del sistema para desarrolladores que usa la arquitectura predeterminada de la compilación de herramientas de 32 bits, nativo x86 para compilar el código de 32 bits, nativo x86. Si prefiere una arquitectura de compilación no predeterminado, elija uno de nativo o entre herramientas de símbolo del sistema para especificar la arquitectura de host y de destino. 

Es una forma más rápida para abrir una ventana de símbolo del sistema para desarrolladores escribir *símbolo* en el cuadro de búsqueda en el escritorio, a continuación, elija el resultado deseado.

<a name="developer_command_files"></a>
## <a name="developer-command-files-and-locations"></a>Ubicaciones y los archivos de comandos de desarrollador

Si lo prefiere establecer el entorno de generación de arquitectura en una ventana de símbolo del sistema existente, puede usar uno de los archivos de comandos creados por el programa de instalación. La ubicación de estos archivos depende de la versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] ha instalado y en la ubicación y las opciones de nomenclatura realizado durante la instalación. Para Visual Studio de 2017, la ubicación de instalación típica en un equipo de 64 bits se encuentra en \Program archivos (x86) \Microsoft Visual Studio\2017\\*edición*, donde *edición* puede ser la Comunidad, Professional, Enterprise, BuildTools o a otro nombre que proporcionó. Para Visual Studio 2015, la ubicación de instalación típica es \Program Files (x86) \Microsoft 14.0 de Visual Studio. 

El archivo de comandos del símbolo del sistema de desarrollador principal, VsDevCmd.bat, se encuentra en el subdirectorio Common7\Tools del directorio de instalación. Cuando se especifica ningún parámetro, se establece la arquitectura de entorno y la compilación para usar las herramientas de x86 nativo de 32 bits para generar 32-bit x86 código.

Archivos de comandos adicionales están disponibles para configurar las arquitecturas de compilación concreta, dependiendo de la arquitectura de procesador y la [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] las cargas de trabajo y las opciones que ha instalado. En Visual Studio de 2017, éstos se encuentran en el subdirectorio VC\Auxiliary\Build de la [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] directorio de instalación. En Visual Studio 2015, éstos se encuentran en VC, VC\bin o VC\bin\\*arquitecturas* subdirectorios del directorio de instalación, donde *arquitecturas* es uno de nativo o cruzada Opciones del compilador. Estos archivos de comandos establezca los parámetros y llamar a VsDevCmd.bat para configurar el entorno de arquitectura de compilación especificada. Una instalación típica puede incluir estos archivos de comandos:

- **vcvars32.bat** usar las herramientas de x86 nativo de 32 bits para generar 32-bit x86 código.  
- **vcvars64.bat** usar las herramientas de x64 nativo de 64 bits para generar 64-bit x64 código.  
- **vcvarsx86_amd64.bat** usar las herramientas cruzadas de x86 nativo de 32 bits a 64 bits x64 de compilación código.  
- **vcvarsamd64_x86.bat** usar las herramientas cruzadas de x64 nativo de 64 bits para crear 32-bit x86 código.  
- **vcvarsx86_arm.bat** usar las herramientas cruzadas de x86 nativo de 32 bits para compilar código ARM.  
- **vcvarsamd64_arm.bat** usar las herramientas cruzadas de x64 nativo de 64 bits para compilar código ARM.  
- **vcvarsall.bat** usar parámetros para especificar el host y de arquitecturas de destino, así como las opciones de SDK y plataforma. Llamar a mediante un `/help` parámetro para obtener una lista de opciones.  

> [!CAUTION]
>  Otros archivos de comandos y el archivo vcvarsall.bat pueden variar de un equipo a otro. Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo. Vuelva a ejecutar el [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalador para reemplazar el archivo que falta.  
>   
> El archivo vcvarsall.bat también puede variar de una versión a otra. Si la versión actual de Visual C++ se instala en un equipo que también tiene una versión anterior de Visual C++, no ejecute vcvarsall.bat u otro archivo de comandos de versiones diferentes en la misma ventana del símbolo del sistema.  
 
Es la manera más sencilla para especificar una arquitectura de compilación determinada en una ventana de comandos existentes usar el archivo vcvarsall.bat. Puede utilizar vcvarsall.bat para establecer variables de entorno para configurar la línea de comandos para la compilación nativa de 32 bits o 64 bits, o para la compilación cruzada para x86, x64 o procesadores ARM; Tienda de Windows de destino, la plataforma Universal de Windows o plataformas de escritorio de Windows; para especificar qué SDK de Windows a utilizar; y para especificar la versión del conjunto de herramientas de plataforma. Si no se proporcionan argumentos, vcvarsall.bat configura las variables de entorno para usar el compilador nativo de 32 bits actual para x86 destinos de escritorio de Windows. Sin embargo, puede utilizarlo para configurar cualquiera de nativo o entre herramientas del compilador. Si se especifica una configuración de compilador que no está instalada o no está disponible en la arquitectura del equipo de compilación, se muestra un mensaje de error. Esta tabla muestra los argumentos de la arquitectura admitida:  
  
|Argumento de vcvarsall.bat arquitectura|Compilador|Arquitectura del equipo host|Arquitectura de salida de compilación|  
|----------------------------|--------------|----------------------------------|-------------------------------|  
|x86|x86 nativo de 32 bits|x86, x64|x86|  
|x86\_amd64 o x86\_x64|cross x64 en x86|x86, x64|x64|  
|x86_arm|ARM en x86 cruzado|x86, x64|ARM|  
|AMD64 o x64|x64 nativo de 64 bits|x64|x64|  
|AMD64\_x86 o x x64\_x86|cross x86 en x64|x64|x86|  
|AMD64\_x64 o arm\_arm|ARM en x64 cross|x64|ARM|  
  
Puede usar el **almacenar** o **uwp** opciones para especificar el tipo de plataforma o ninguna de ellas para especificar una aplicación de escritorio. Para especificar la versión del SDK de Windows, puede usar un número de SDK de Windows 10 completo como 10.0.10240.0 o especificar 8.1 para usar el SDK de Windows 8.1. Use 14.0 para especificar el conjunto de herramientas del compilador de Visual Studio 2015; de forma predeterminada, el entorno está configurado para usar el conjunto de herramientas del compilador de Visual Studio de 2017.

<a name="vcvarsall"></a>
## <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Para configurar el entorno de compilación en una ventana de símbolo del sistema existente  
  
1.  En el símbolo del sistema, use el comando CD para cambiar al directorio de instalación de Visual Studio. A continuación, utilice de nuevo CD para cambiar al subdirectorio que contiene los archivos de comandos específicas de la configuración. Para Visual Studio de 2017, este es el subdirectorio VC\Auxiliary\Build. Para Visual Studio 2015, use el subdirectorio de VC.  
  
1.  Para configurar esta ventana de símbolo del sistema para usar herramientas de 32 bits para generar código para x86 plataformas, en el símbolo del sistema, escriba:  
  
     `vcvarsall`  

1.  Para configurar esta ventana de símbolo del sistema para usar herramientas de 32 bits para generar código para x64 plataformas, en el símbolo del sistema, escriba:  
  
     `vcvarsall x86_amd64`  
  
1.  Para configurar esta ventana de símbolo del sistema para usar herramientas de 32 bits para generar código para las plataformas ARM, en el símbolo del sistema, escriba:  
  
     `vcvarsall x86_arm`  
  
1.  Para configurar esta ventana de símbolo del sistema para usar las herramientas de 64 bits para generar código para x64 plataformas, en el símbolo del sistema, escriba:  
  
     `vcvarsall amd64`  
  
1.  Para configurar esta ventana de símbolo del sistema para usar las herramientas de 64 bits para generar código para x86 plataformas, en el símbolo del sistema, escriba:  
  
     `vcvarsall amd64_x86`  
  
1.  Para configurar esta ventana de símbolo del sistema para usar las herramientas de 64 bits para generar código para las plataformas ARM, en el símbolo del sistema, escriba:  
  
     `vcvarsall amd64_arm`  

El archivo de comandos establece las variables de entorno necesarias para las rutas de acceso a las herramientas de compilación, bibliotecas y encabezados. Ahora puede utilizar esta ventana de símbolo del sistema para ejecutar el compilador de línea de comandos y herramientas.  
  
Si utilizas [DEVENV](/visualstudio/ide/reference/devenv-command-line-switches) para las compilaciones de línea de comandos, el entorno establecido por vcvarsall.bat u otros archivos de comando no afecta a las compilaciones, a menos que especifique también la **/useenv** opción.  

## <a name="command-line-tools"></a>Herramientas de línea de comandos
  
Para compilar un proyecto de C o C++ en la línea de comandos, puede usar estas herramientas de línea de comandos de Visual C++:  
  
[CL](../build/reference/compiling-a-c-cpp-program.md)  
Utilice el compilador (cl.exe) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.  
  
[Vínculo](../build/reference/linking.md)  
Utilice el enlazador (link.exe) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
Usar MSBuild (msbuild.exe) para compilar proyectos de Visual C++ y [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] soluciones. Esto equivale a ejecutar el **generar** proyecto o **generar solución** comando en el [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE.  
  
[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)  
Utilice DEVENV (devenv.exe) combinado con un modificador de línea de comandos, por ejemplo, **/generar** o **/limpiar**: para realizar determinados comandos de compilación sin mostrar el [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE.  
  
[NMAKE](../build/nmake-reference.md)  
Utilice NMAKE (nmake.exe) para automatizar las tareas que compilan proyectos de Visual C++ mediante el uso de un archivo MAKE tradicional.  
  
Al compilar en la línea de comandos, puede obtener información sobre advertencias, errores y mensajes. Iniciar [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y, a continuación, en la barra de menús, elija **ayuda**, **búsqueda**.  
  
## <a name="in-this-section"></a>En esta sección  

En los artículos de esta sección de la documentación se muestra cómo compilar aplicaciones en la línea de comandos, se describe cómo personalizar el entorno de compilación de la línea de comandos para usar conjuntos de herramientas de 64 bits y tener como destinos las plataformas x86, x64 y ARM, y se indica cómo usar las herramientas de compilación de la línea de comandos MSBuild y NMAKE.  
  
[Tutorial: Compilar un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
Ofrece un ejemplo que muestra cómo crear y compilar un programa de C++ sencillo en la línea de comandos.  
  
[Tutorial: Compilar un programa de C en la línea de comandos](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
Describe cómo compilar un programa escrito en el lenguaje de programación C.  
  
[Tutorial: Compilar un programa de C++/CLI en la línea de comandos](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
Describe cómo crear y compilar un programa de C++/CLI que utilice .NET Framework.  
  
[Tutorial: Compilar un programa de C++/CX en la línea de comandos](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
Describe cómo crear y compilar un programa de C++/CX que utilice Windows Runtime.  
  
[Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
Describe cómo iniciar una ventana de símbolo del sistema que tiene las variables de entorno necesarias establecido para las compilaciones de línea de comandos que tienen como destino x86, x64, plataformas y ARM con un conjunto de herramientas de 32 bits o 64 bits.  
  
[Referencia de NMAKE](../build/nmake-reference.md)  
Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft (NMAKE.EXE).  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
Proporciona vínculos a artículos en los que se explica cómo utilizar MSBuild.EXE.  
  
## <a name="related-sections"></a>Secciones relacionadas  

[/ MD, / MT, /LD (utilizar la biblioteca en tiempo de ejecución)](../build/reference/md-mt-ld-use-run-time-library.md)  
Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.  
  
[Opciones del compilador de C o C++](../build/reference/compiler-options.md)  
Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C++, y CL.exe.  
  
[Opciones del vinculador](../build/reference/linker-options.md)  
Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.  
  
[Herramientas de compilación de C/C++](../build/reference/c-cpp-build-tools.md)  
Proporciona vínculos a las herramientas de compilación de C/C++ que se incluyen en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vea también  

[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)