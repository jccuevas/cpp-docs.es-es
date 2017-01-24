---
title: "Compilar en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compilaciones [C++], línea de comandos"
  - "línea de comandos [C++], compilar desde"
  - "línea de comandos [C++], compiladores"
  - "compilaciones desde la línea de comandos [C++]"
  - "compilar código fuente [C++], línea de comandos"
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con las herramientas incluidas en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], puede compilar aplicaciones de C y C\+\+ en la línea de comandos.  Cada edición de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instala un conjunto de herramientas de línea de comandos que incluye un compilador, un enlazador y otras herramientas de compilación, además de un archivo de comandos que establece el entorno de compilación necesario.  De forma predeterminada, estas herramientas se instalan en *unidad*:\\Archivos de programa \(x86\)\\Microsoft Visual Studio *versión*\\VC\\bin\\.  \(El directorio de cada equipo depende del sistema, la versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y las opciones elegidas durante la instalación\).  
  
 Para que funcionen correctamente, las herramientas de línea de comandos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] requieren varias variables de entorno que estén personalizadas para su instalación.  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], cuando se instala, crea el archivo de comandos vcvarsall.bat, que se puede ejecutar para establecer las variables de entorno necesarias.  También crea un acceso directo que inicia una ventana del Símbolo del sistema para desarrolladores en la que ya están establecidas estas variables.  Estas variables de entorno corresponden específicamente a su instalación y las actualizaciones del producto pueden cambiarlas.  Por ello, le recomendamos que use vcvarsall.bat o un acceso directo del Símbolo del sistema para desarrolladores en lugar de establecerlas por su cuenta.  Para obtener más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
### Para abrir una ventana del Símbolo del sistema para desarrolladores  
  
1.  En la pantalla Inicio de Windows 8, escriba Visual Studio Tools.  Observe que los resultados de búsqueda cambian a medida que escribe. Cuando aparezca **Visual Studio Tools**, elíjalo.  
  
     En las versiones anteriores de Windows, elija **Inicio** y, luego, en el cuadro de búsqueda, escriba Visual Studio Tools.  Cuando aparezca **Visual Studio Tools** en los resultados de la búsqueda, elíjalo.  
  
2.  En la carpeta **Visual Studio Tools**, abra el **Símbolo del sistema para desarrolladores** de su versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Para compilar un proyecto de C\/C\+\+ en la línea de comandos, puede usar estas herramientas de línea de comandos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]:  
  
 [CL](../build/reference/compiling-a-c-cpp-program.md)  
 Utilice el compilador \(cl.exe\) para compilar y vincular archivos de código fuente en aplicaciones, bibliotecas y DLL.  
  
 [Link](../build/reference/linking.md)  
 Utilice el enlazador \(link.exe\) para vincular bibliotecas y archivos de objeto compilados en aplicaciones y DLL.  
  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)  
 Utilice MSBuild \(msbuild.exe\) para compilar proyectos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] y soluciones de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  Equivale a ejecutar el proyecto **Build** o el comando **Build Solution** en el IDE de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 [DEVENV](../Topic/Devenv%20Command%20Line%20Switches.md)  
 Utilice DEVENV \(devenv.exe\) combinado con un modificador de la línea de comandos \(por ejemplo, **\/Build** o **\/Clean**\) para ejecutar determinados comandos de compilación sin mostrar el IDE de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 [NMAKE](../build/nmake-reference.md)  
 Utilice NMAKE \(nmake.exe\) para automatizar las tareas que compilan proyectos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] con un archivo Make tradicional.  
  
 Al compilar en la línea de comandos, puede obtener información sobre advertencias, errores y mensajes: para ello, inicie [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y, luego, en la barra de menús, elija **Ayuda** y **Buscar**.  
  
## En esta sección  
 En los artículos de esta sección de la documentación se muestra cómo compilar aplicaciones en la línea de comandos, se describe cómo personalizar el entorno de compilación de la línea de comandos para usar conjuntos de herramientas de 64 bits y tener como destinos las plataformas x86, x64 y ARM, y se indica cómo usar las herramientas de compilación de la línea de comandos MSBuild y NMAKE.  
  
 [Tutorial: Compilar un programa nativo de C\+\+ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
 Ofrece un ejemplo que muestra cómo crear y compilar un programa de C\+\+ sencillo en la línea de comandos.  
  
 [Tutorial: Compilar un programa escrito en C en la línea de comandos](../Topic/Walkthrough:%20Compiling%20a%20C%20Program%20on%20the%20Command%20Line.md)  
 Describe cómo compilar un programa escrito en el lenguaje de programación C.  
  
 [Tutorial: Compilar un programa de C\+\+\/CLI en la línea de comandos](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
 Describe cómo crear y compilar un programa de C\+\+\/CLI que utilice .NET Framework.  
  
 [Tutorial: Compilar un programa de C\+\+\/CX en la línea de comandos](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
 Describe cómo crear y compilar un programa de C\+\+\/CX que utilice Windows en tiempo de ejecución.  
  
 [Establecimiento de la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
 Describe cómo iniciar una ventana del símbolo del sistema que tenga establecidas las variables de entorno necesarias para realizar desde la línea de comandos compilaciones destinadas a las plataformas x86, x64 y ARM con un conjunto de herramientas de 32 o 64 bits.  
  
 [Referencia de NMAKE](../build/nmake-reference.md)  
 Proporciona vínculos a artículos que describen la Utilidad de mantenimiento de programas de Microsoft \(NMAKE.EXE\).  
  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)  
 Proporciona vínculos a artículos en los que se explica cómo utilizar MSBuild.EXE.  
  
## Secciones relacionadas  
 [\/MD, \/MT, \/LD \(utilizar la biblioteca en tiempo de ejecución\)](../build/reference/md-mt-ld-use-run-time-library.md)  
 Describe cómo utilizar estas opciones del compilador para usar una biblioteca en tiempo de ejecución Debug o Release.  
  
 [Opciones del compilador de C\/C\+\+](../build/reference/compiler-options.md)  
 Proporciona vínculos a artículos en los que se explican las opciones del compilador de C y C\+\+, y CL.exe.  
  
 [Opciones del enlazador](../build/reference/linker-options.md)  
 Proporciona vínculos a artículos en los que se explican las opciones del enlazador y LINK.exe.  
  
 [Herramientas de compilación de C\/C\+\+](../build/reference/c-cpp-build-tools.md)  
 Proporciona vínculos a las herramientas de compilación de C\/C\+\+ que se incluyen en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## Vea también  
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)