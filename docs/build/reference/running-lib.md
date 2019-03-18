---
title: Ejecutar LIB
ms.date: 09/28/2018
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
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
ms.openlocfilehash: e95427b571cd14ad39a7ba4f368b90e806f13862
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820369"
---
# <a name="running-lib"></a>Ejecutar LIB

Diversas opciones de línea de comandos pueden usarse para controlar LIB.

## <a name="lib-command-line"></a>Línea de comandos LIB

Para ejecutar LIB, escriba el comando `lib` seguido de las opciones y los nombres de archivo para la tarea está usando LIB para realizar. Esta herramienta también acepta entrada de línea de comandos en archivos de comandos, que se describen en la sección siguiente. LIB no utiliza una variable de entorno.

> [!NOTE]
> Si está acostumbrado a la LINK32.exe y LIB32.exe de las herramientas proporcionadas con el Kit de desarrollo de Software de Win32 de Microsoft para Windows NT, que haya utilizado el comando `link32 -lib` o el comando `lib32` para administrar las bibliotecas y crear bibliotecas de importación. No olvide cambiar los archivos por lotes y de archivos MAKE para usar el `lib` comando en su lugar.

## <a name="lib-command-files"></a>Archivos de comandos LIB

Puede pasar argumentos de línea de comandos a LIB en un archivo de comandos utilizando la sintaxis siguiente:

> **LIB \@**  <em>/commandfile</em>

El archivo */commandfile* es un archivo de texto. No se permite ningún espacio o tabulación entre la arroba (**\@**) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluido cualquier extensión. No se puede usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo.

En el archivo de comandos, se pueden separar los argumentos con espacios o tabulaciones, como puedan en la línea de comandos; También pueden separarse por caracteres de nueva línea. Use un punto y coma (**;**) para marcar un comentario. LIB omite todo el texto desde el punto y coma al final de la línea.

Puede especificar todos o parte de la línea de comandos en un archivo de comandos, y puede usar más de un archivo de comandos en un comando LIB. LIB acepta la entrada de archivo de comandos como si se especificaron en esa ubicación en la línea de comandos. Archivos de comandos no se pueden anidar. LIB refleje el contenido de archivos de comandos, a menos que se usa la opción /NOLOGO.

## <a name="using-lib-options"></a>Uso de las opciones de LIB

Una opción consta de un especificador de opción, que es ya sea un guión (**-**) o una barra diagonal (**/**), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, especificado después de dos puntos (**:**). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opción y sus argumentos de nombre de archivo o la palabra clave no distinguen mayúsculas de minúsculas, pero los identificadores utilizados como argumentos distinguen mayúsculas de minúsculas. LIB procesa las opciones en el orden especificado en la línea de comandos y en archivos de comandos. Si se repite una opción con distintos argumentos, la última de ellas para procesarse tiene prioridad.

Las siguientes opciones se aplican a todos los modos de LIB:

> **/ERRORREPORT** [**NONE** &#124; **PROMPT** &#124; **QUEUE** &#124; **SEND**]

Si lib.exe genera un error en tiempo de ejecución, puede usar **/errorreport** para enviar información a Microsoft sobre estos errores internos.

Para obtener más información acerca de **/errorreport**, consulte [/errorReport (informar de errores de compilador interno)](errorreport-report-internal-compiler-errors.md).

> **/LTCG**

Es el acrónimo "LTCG" *generación de código en tiempo de vínculo*. Esta característica requiere la cooperación entre el compilador ([cl.exe](compiler-options.md)), LIB y el vinculador ([vínculo](linker-options.md)) con el fin de optimizar el código más allá de lo que puede hacer cualquier componente por sí mismo.

Para LIB, el **/LTCG** opción especifica que las entradas de cl.exe incluyen los archivos de objeto que se generaron mediante el [/GL](gl-whole-program-optimization.md) opción del compilador. Si LIB encuentra esas entradas y **/LTCG** no se especifica, se reiniciará con/LTCG habilita después de mostrar un mensaje informativo. En otras palabras, no es necesario establecer explícitamente esta opción, pero acelera el rendimiento de compilación debido a que LIB no tiene que reiniciarse.

En el proceso de compilación, se envía la salida de LIB al vínculo. VÍNCULO tiene su propio independiente **/LTCG** opción que se usa para realizar varias optimizaciones, incluida la optimización de todo el programa y la instrumentación de optimización guiada por perfiles (PGO). Para obtener más información acerca de la opción de vínculo, vea [/LTCG](ltcg-link-time-code-generation.md).

> **/MACHINE**

Especifica la plataforma de destino para el programa. Por lo general, no es necesario especificar/Machine. LIB infiere el tipo de equipo desde los archivos .obj. Sin embargo, en algunas circunstancias, LIB no puede determinar el tipo de equipo y emite un mensaje de error. Si se produce un error de este tipo, especifique /MACHINE. En el modo/Extract, esta opción es solamente para verificar. Use `lib /?` en la línea de comandos para ver los tipos de equipos disponibles.

> **/NOLOGO**

Suprime la presentación de la LIB copyright mensaje y número de versión e impide que un eco de los archivos de comandos.

> **/VERBOSE**

Muestra los detalles sobre el progreso de la sesión, incluidos los nombres de los archivos .obj que se va a agregar. La información se envía a la salida estándar y puede redirigirse a un archivo.

> **/WX**[**:NO**]

Tratar advertencias como errores. Consulte [/WX (tratar advertencias del vinculador como errores)](wx-treat-linker-warnings-as-errors.md) para obtener más información.

Otras opciones se aplican solo a los modos específicos de LIB. Estas opciones se describen en las secciones que describen cada modo.

## <a name="see-also"></a>Vea también

[Referencia de LIB](lib-reference.md)
