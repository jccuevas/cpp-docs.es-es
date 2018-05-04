---
title: Ejecutar LIB | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c306ba58bfef11f92d7e861272aad2aa605c8fde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="running-lib"></a>Ejecutar LIB
Varias opciones de línea de comandos pueden utilizarse para controlar LIB.  
  
## <a name="lib-command-line"></a>Línea de comandos LIB  
 Para ejecutar LIB, escriba el comando `lib` seguido de las opciones y los nombres de archivo para la tarea está usando LIB para realizar. LIB también acepta la entrada de línea de comandos en archivos de comandos, que se describen en la sección siguiente. LIB no utiliza una variable de entorno.  
  
> [!NOTE]
>  Si está acostumbrado a la LINK32.exe y LIB32.exe las herramientas proporcionadas con el Kit de desarrollo de Software de Win32 de Microsoft para Windows NT, que ha estado usando el comando `link32 -lib` o el comando `lib32` para administrar las bibliotecas y crear bibliotecas de importación. No olvide cambiar los archivos MAKE (archivos) y por lotes para usar el `lib` comando en su lugar.  
  
## <a name="lib-command-files"></a>Archivos de comandos LIB  
 También puede pasar argumentos de línea de comandos a LIB en un archivo de comandos utilizando la sintaxis siguiente:  
  
```  
LIB @commandfile  
```  
  
 El archivo `commandfile` es un archivo de texto. No se permite ningún espacio o tabulación entre el signo de arroba (@) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluido cualquier extensión. No se puede usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo.  
  
 En el archivo de comandos, los argumentos se pueden separados por espacios o tabulaciones, como si se tratara de la línea de comandos; También pueden separarse por caracteres de nueva línea. Utilice un punto y coma (;) para marcar un comentario. LIB ignorará todo el texto desde el punto y coma al final de la línea.  
  
 Puede especificar todos o parte de la línea de comandos en un archivo de comandos, y puede usar más de un archivo de comandos en un comando LIB. LIB acepta datos proporcionados por el archivo de comandos como si se especifica en esa ubicación en la línea de comandos. Archivos de comandos no se pueden anidar. LIB repite el contenido de archivos de comandos, a menos que se utiliza la opción/nologo.  
  
## <a name="using-lib-options"></a>Usar opciones de LIB  
 Una opción consta de un especificador de opción, que es un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, ir precedido por dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opción y sus argumentos de nombre de archivo o la palabra clave no distinguen mayúsculas de minúsculas, pero los identificadores usados como argumentos distinguen mayúsculas de minúsculas. LIB procesa las opciones en el orden especificado en la línea de comandos y en archivos de comandos. Si una opción se repite con diferentes argumentos, la última de ellas para procesarse tiene prioridad.  
  
 Las siguientes opciones se aplican a todos los modos de LIB:  
  
 /ERRORREPORT [NONE &AMP;#124; PROMPT &AMP;#124; COLA &AMP;#124; ENVÍO]  
 Si lib.exe genera un error en tiempo de ejecución, puede utilizar /ERRORREPORT para enviar información a Microsoft sobre estos errores internos.  
  
 Para obtener más información sobre/errorreport, vea [/errorReport (informar de errores de compilador interno)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 /LTCG  
 Hace que la biblioteca que se crea utilizando la generación de código en tiempo de vínculo.  Para obtener más información, consulte [/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 /MACHINE  
 Especifica la plataforma de destino para el programa. Por lo general, no es necesario especificar/Machine. LIB infiere el tipo de equipo de los archivos .obj. Sin embargo, en algunas circunstancias LIB no puede determinar el tipo de equipo y emite un mensaje de error. Si se produce un error de este tipo, especifique /MACHINE. En el modo/Extract, esta opción es solamente para verificar. Use `lib /?` en la línea de comandos para ver los tipos de equipos disponibles.  
  
 /NOLOGO  
 Suprime la presentación de la LIB copyright mensaje y número de versión e impide el eco de los archivos de comandos.  
  
 /VERBOSE  
 Muestra los detalles sobre el progreso de la sesión, incluidos los nombres de los archivos .obj que se va a agregar. La información se envía a la salida estándar y puede redirigirse a un archivo.  
  
 /WX [: N]  
 Tratar advertencias como errores. Vea [/WX (tratar advertencias del vinculador como errores)](../../build/reference/wx-treat-linker-warnings-as-errors.md) para obtener más información.  
  
 Otras opciones solo se aplican a modos específicos de LIB. Estas opciones se describen en las secciones que describen cada modo.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)