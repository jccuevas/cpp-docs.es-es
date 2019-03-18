---
title: Opciones de BSCMAKE
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: bf4c3648079dff16481dbdd56b9a70093fd22d8d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812062"
---
# <a name="bscmake-options"></a>Opciones de BSCMAKE

En esta sección se describen las opciones disponibles para controlar BSCMAKE. Varias opciones controlan el contenido del archivo de información de examen mediante la exclusión o inclusión de cierta información. Las opciones de exclusión pueden permitir que BSCMAKE se ejecute con mayor rapidez y que se genere un archivo .bsc menor. Los nombres de opción distinguen mayúsculas de minúsculas (excepto para **/ayuda** y **/NOLOGO**).

Solo **/NOLOGO** y **/o** están disponibles en el entorno de desarrollo de Visual Studio.  Consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md) para obtener información sobre acceso a páginas de propiedades de un proyecto.

**/Ei (** *filename*...**)**<br/>
Excluye del archivo de información de examen el contenido de los archivos de inclusión especificados. Para especificar varios archivos, separe los nombres con un espacio y encierre la lista entre paréntesis. Los paréntesis no son necesarios si se especifica solo una *filename*. Use **/EI** junto con el **/es** opción para excluir los archivos no excluidos mediante **/es**.

**/El**<br/>
Excluye los símbolos locales. La opción predeterminada es incluir los símbolos locales. Para obtener más información sobre los símbolos locales, vea [crear un archivo .sbr](creating-an-dot-sbr-file.md).

**/Em**<br/>
Excluye los símbolos en el cuerpo de las macros. Use **/Em** para incluir solo los nombres de macros en el archivo de información de examen. La opción predeterminada es incluir tanto los nombres de macros como el resultado de las expansiones de macros.

**/ ER (** *símbolo*... **)**<br/>
Excluye los símbolos especificados del archivo de información de examen. Para especificar varios nombres de símbolos, separe los nombres con un espacio y encierre la lista entre paréntesis. Los paréntesis no son necesarios si se especifica solo una *símbolo*.

**/Es**<br/>
Excluye del archivo de información de examen todos los archivos de inclusión especificados con una ruta de acceso absoluta o que se encuentran en una ruta de acceso absoluta especificada en la variable de entorno INCLUDE. (Normalmente, estos son los archivos de inclusión del sistema, que contienen gran cantidad de información posiblemente innecesaria en el archivo de información de examen). Esta opción no excluye los archivos especificados sin una ruta de acceso, los especificados con rutas de acceso relativas ni los que se encuentran en una ruta de acceso relativa en INCLUDE. Puede usar el **/EI** junto con la opción **/es** para excluir los archivos que **/es** no excluye. Si desea excluir sólo algunos de los archivos que **/es** excluye, use **/EI** en lugar de **/es** y enumerar los archivos que desea excluir.

**/errorreport:**[**none** &#124; **prompt** &#124; **queue** &#124; **send**]<br/>
Permite enviar información a Microsoft sobre errores internos de bscmake.exe.

Para obtener más información sobre **/errorreport**, consulte [/errorReport (informar de errores de compilador interno)](errorreport-report-internal-compiler-errors.md).

**/HELP**<br/>
Muestra un resumen de la sintaxis de línea de comandos de BSCMAKE.

**/Iu**<br/>
Incluye los símbolos sin referencia. De forma predeterminada, BSCMAKE no registra los símbolos definidos a los que no se hace referencia. Si se ha empaquetado un archivo .sbr, esta opción no afecta a ese archivo de entrada porque el compilador ya ha quitado los símbolos sin referencia.

**/n**<br/>
Fuerza una compilación no incremental. Use **/n** para forzar una compilación completa del archivo de información de examen si existe o no un archivo .bsc e impedir que los archivos .sbr que se va a truncar. Consulte [cómo compila BSCMAKE un archivo .bsc](how-bscmake-builds-a-dot-bsc-file.md).

**/NOLOGO**<br/>
Suprime el mensaje de copyright de BSCMAKE.

**/o** *filename*<br/>
Especifica un nombre para el archivo de información de examen. De forma predeterminada, BSCMAKE asigna al archivo de información de examen el mismo nombre base del primer archivo .sbr y una extensión .bsc.

**/S (** *filename*...**)**<br/>
Indica a BSCMAKE que procese el archivo de inclusión especificado la primera vez que lo encuentre y que lo excluya en otro caso. Esta opción se utiliza para ahorrar tiempo de procesamiento cuando un archivo (por ejemplo, un archivo de encabezado o .h para un archivo de código fuente .c o .cpp) se incluye en varios archivos de código fuente, pero no lo modifican las directivas de preprocesamiento cada vez. También puede ser conveniente usar esta opción si un archivo sufre cambios que no son importantes para el archivo de información de examen que se está creando. Para especificar varios archivos, separe los nombres con un espacio y encierre la lista entre paréntesis. Los paréntesis no son necesarios si se especifica solo una *filename*. Si desea excluir el archivo cada vez que se incluye, use el **/EI** o **/es** opción.

**/v**<br/>
Proporciona un resultado detallado que incluye el nombre de cada uno de los archivos .sbr que se están procesando e información sobre la ejecución completa de BSCMAKE.

**/?**<br/>
Muestra un breve resumen de la sintaxis de línea de comandos de BSCMAKE.

La siguiente línea de comandos indica a BSCMAKE que realice una compilación completa de MAIN.bsc a partir de tres archivos .sbr. También indica a BSCMAKE que excluya las instancias duplicadas de TOOLBOX.h:

```
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Vea también

[Referencia de BSCMAKE](bscmake-reference.md)
