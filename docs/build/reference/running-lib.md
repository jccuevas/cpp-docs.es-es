---
title: Ejecutar LIB
description: Describe las opciones de línea de comandos que puede usar con lib. exe.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
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
ms.openlocfilehash: 871b92809f38b4dcbf84de802b1ac9940ea6f1e9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438939"
---
# <a name="running-lib"></a>Ejecutar LIB

Se pueden utilizar varias opciones de línea de comandos para controlar LIB.

## <a name="lib-command-line"></a>Línea de comandos de LIB

Para ejecutar LIB, escriba el comando `lib`, seguido de las opciones y los nombres de archivo de la tarea para la que está usando LIB. LIB también acepta la entrada de la línea de comandos en los archivos de comandos, que se describen en la sección siguiente. LIB no utiliza una variable de entorno.

## <a name="lib-command-files"></a>Archivos de comandos LIB

Puede pasar argumentos de línea de comandos a LIB en un archivo de comandos con la siguiente sintaxis:

> <em>Archivo de comandos de</em> **\@lib**

El archivo *de comandos de* archivo es un archivo de texto. No se permiten espacios ni tabulaciones entre el signo de arroba ( **\@** ) y el nombre de archivo. El nombre del *archivo de comandos* no tiene ninguna extensión predeterminada. Especifique el nombre de archivo completo, incluida cualquier extensión. No se pueden usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo.

En el archivo de comandos, los argumentos pueden estar separados por espacios o tabulaciones, como pueden hacerlo en la línea de comandos. Los argumentos también se pueden separar por caracteres de nueva línea. Use un punto y coma ( **;** ) para marcar un comentario. LIB omite todo el texto del punto y coma hasta el final de la línea.

Puede especificar toda o parte de la línea de comandos en un archivo de comandos, y puede usar más de un archivo de comandos en un comando LIB. LIB acepta la entrada del archivo de comandos como si se hubiera especificado en esa ubicación en la línea de comandos. Los archivos de comandos no se pueden anidar. LIB repite el contenido de los archivos de comandos a menos que se use la opción **/nologo** .

## <a name="using-lib-options"></a>Usar las opciones de LIB

Una opción consta de un especificador de opción, que puede ser un guión ( **-** ) o una barra diagonal ( **/** ), seguido del nombre de la opción. Los nombres de opciones no se pueden abreviar. Algunas opciones toman un argumento, que se especifica después de un signo de dos puntos ( **:** ). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opciones y sus argumentos de palabra clave o nombre de archivo no distinguen mayúsculas de minúsculas, pero los identificadores usados como argumentos distinguen mayúsculas de minúsculas. LIB procesa las opciones en el orden especificado en la línea de comandos y en los archivos de comandos. Si una opción se repite con argumentos diferentes, tendrá prioridad la última que se va a procesar.

Las siguientes opciones se aplican a todos los modos de LIB:

> **/Errorreport** \[**None** &#124; **prompt** &#124; **Queue** &#124; **send**]

La opción/ERRORREPORT está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

> **/LINKREPRO:** _ruta de acceso de directorio_ \
> **/LINKREPROTARGET:** _nombre de archivo_

Para ayudar a que Microsoft diagnostique los bloqueos de lib. exe y los errores internos, puede usar la opción [/LINKREPRO](linkrepro.md) . Esta opción genera una *reproducción de vínculo*, un conjunto de artefactos de compilación que permiten a Microsoft reproducir un problema que se produce durante las operaciones de la biblioteca. La opción [/LINKREPROTARGET](linkreprotarget.md) se puede usar con la opción **/LINKREPRO** . Solo genera artefactos de reproducción de vínculos cuando lib. exe genera el archivo especificado. Para obtener más información, vea [Cómo notificar un problema con el C++ conjunto de herramientas de Microsoft](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

> **/LTCG**

"LTCG" representa *la generación de código en tiempo de vínculo*. Esta característica requiere la cooperación entre el compilador ([cl. exe](compiler-options.md)), lib y el vinculador ([Link](linker-options.md)). Juntos pueden optimizar el código más allá de lo que cualquier componente puede hacer por sí solo.

La opción **/LTCG** de lib especifica que las entradas de cl. exe incluyen archivos objeto generados mediante la opción del compilador [/GL](gl-whole-program-optimization.md) . Si LIB encuentra tales entradas y no se especifica **/LTCG** , se reinicia con/LTCG habilitado después de mostrar un mensaje informativo. En otras palabras, no es necesario establecer esta opción explícitamente, pero acelera el rendimiento de la compilación. Esto se debe a que LIB no tiene que reiniciarse.

En el proceso de compilación, la salida de LIB se envía al vínculo. LINK tiene su propia opción **/LTCG** independiente. Se usa para realizar varias optimizaciones, incluida la optimización de programas completos y la instrumentación de optimización guiada por perfiles (PGO). Para obtener más información acerca de la opción de vínculo, vea [/LTCG](ltcg-link-time-code-generation.md).

> **/MACHINE**

Especifica la plataforma de destino para el programa. Normalmente, no es necesario especificar **/Machine**. LIB infiere el tipo de máquina a partir de los archivos. obj. Sin embargo, en algunas circunstancias, LIB no puede determinar el tipo de equipo y emite un mensaje de error. Si se produce un error de este tipo, especifique **/Machine**. En el modo **/Extract** , esta opción solo se puede comprobar. Use `lib /?` en la línea de comandos para ver los tipos de máquina disponibles.

> **/NOLOGO**

Suprime la presentación del mensaje de copyright y el número de versión de LIB y evita que se repitan los archivos de comandos.

> **/VERBOSE**

Muestra detalles sobre el progreso de la sesión, incluidos los nombres de los archivos. obj que se van a agregar. La información se envía a la salida estándar y puede redirigirse a un archivo.

> **/WX**[ **: no**]

Trata las advertencias como errores. Para obtener más información, consulte [/WX (Tratar advertencias del enlazador como errores)](wx-treat-linker-warnings-as-errors.md).

Otras opciones solo se aplican a los modos específicos de LIB. Estas opciones se describen en las secciones que describen cada modo.

## <a name="see-also"></a>Consulte también

[Referencia de LIB](lib-reference.md)
