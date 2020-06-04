---
title: Opciones de BSCMAKE
description: Referencia a las opciones de la línea de comandos de la utilidad BSCMAKE de Microsoft.
ms.date: 02/09/2020
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
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257798"
---
# <a name="bscmake-options"></a>Opciones de BSCMAKE

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Como Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo de *`.sdf`* de SQL Server en la carpeta de la solución.

En esta sección se describen las opciones disponibles para controlar BSCMAKE. Varias opciones controlan el contenido del archivo de información de examen mediante la exclusión o inclusión de cierta información. Las opciones de exclusión pueden permitir que BSCMAKE se ejecute más rápido y puede dar lugar a un archivo de *`.bsc`* más pequeño. Los nombres de opción distinguen mayúsculas de minúsculas (excepto **/Help** y **/nologo**).

Solo los objetos **/nologo** y **/o** están disponibles en el entorno de desarrollo de Visual Studio.  Vea [establecer C++ las propiedades del compilador y compilación en Visual Studio](../working-with-project-properties.md) para obtener información sobre el acceso a las páginas de propiedades de un proyecto.

**/EI (** _nombre de archivo_... **)** \
Excluye del archivo de información de examen el contenido de los archivos de inclusión especificados. Para especificar varios archivos, separe los nombres con un espacio y encierre la lista entre paréntesis. Los paréntesis no son necesarios si solo se especifica un *nombre de archivo*. Use **/EI** junto con la opción **/es** para excluir archivos no excluidos por **/es**.

\ **/el**
Excluye los símbolos locales. La opción predeterminada es incluir los símbolos locales. Para obtener más información sobre los símbolos locales, vea [crear un archivo. SBR](creating-an-dot-sbr-file.md).

\ **/em**
Excluye los símbolos en el cuerpo de las macros. Use **/em** para incluir solo los nombres de macros en el archivo de información de examen. La opción predeterminada es incluir tanto los nombres de macros como el resultado de las expansiones de macros.

**/Er (** _símbolo_... **)** \
Excluye los símbolos especificados del archivo de información de examen. Para especificar varios nombres de símbolos, separe los nombres con un espacio y encierre la lista entre paréntesis. Los paréntesis no son necesarios si solo se especifica un *símbolo*.

\ **/es**
Excluye todos los archivos de inclusión especificados con una ruta de acceso absoluta o que se encuentran en una ruta de acceso absoluta especificada en la variable de entorno INCLUDE. (Normalmente, estos archivos son los archivos de inclusión del sistema, que contienen mucha información que es posible que no necesite en el archivo de información de examen). Esta opción no excluye los archivos especificados sin una ruta de acceso o con rutas de acceso relativas, o los archivos que se encuentran en una ruta de acceso relativa en INCLUDE. Puede usar la opción **/EI** junto con **/es** para excluir los archivos que **/es** no excluya. Si desea excluir solo algunos de los archivos, use **/EI** en lugar de **/es**y enumere los archivos que desea excluir.

**/errorreport:** [**None** &#124; **prompt** &#124; **Queue** &#124; **send**] \
Esta función está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

**/Help**\
Muestra un resumen de la sintaxis de línea de comandos de BSCMAKE.

\ **/IU**
Incluye los símbolos sin referencia. De forma predeterminada, BSCMAKE no registra ningún símbolo que esté definido pero al que no se haga referencia. Si se ha empaquetado un archivo *`.sbr`* , esta opción no tiene ningún efecto para ese archivo de entrada porque el compilador ya ha quitado los símbolos sin referencia.

**/n**\
Fuerza una compilación no incremental. Use **/n** para forzar una compilación completa del archivo de información de examen tanto si existe un archivo *`.bsc`* como si no, y para evitar que *`.sbr`* archivos se trunquen. Vea [Cómo BSCMAKE compila un archivo. BSC](how-bscmake-builds-a-dot-bsc-file.md).

**/Nologo**\
Suprime el mensaje de copyright de BSCMAKE.

**/o** *nombrearchivo*\
Especifica un nombre para el archivo de información de examen. De forma predeterminada, BSCMAKE proporciona al archivo de información de examen el nombre base del primer *`.sbr`* archivo y una extensión de *`.bsc`* .

**/S (** _nombre de archivo_... **)** \
Indica a BSCMAKE que procese el archivo de inclusión especificado la primera vez que se encuentre y que lo excluya de otro modo. Utilice esta opción para ahorrar tiempo de procesamiento cuando un archivo (por ejemplo, un encabezado o *`.h`* archivo para un archivo de código fuente de *`.c`* o *`.cpp`* ) se incluye en varios archivos de código fuente, pero no se modifican las directivas de preprocesamiento cada vez. Utilice esta opción si se cambia un archivo de manera no importante para el archivo de información de examen que está creando. Para especificar varios archivos, separe los nombres con un espacio y encierre la lista entre paréntesis. Los paréntesis no son necesarios si solo se especifica un *nombre de archivo*. Si desea excluir el archivo cada vez que se incluye, use la opción **/EI** o **/es** .

**/v**\
Proporciona una salida detallada, que incluye el nombre de cada archivo *`.sbr`* que se está procesando e información sobre la ejecución completa de BSCMAKE.

**/?** \
Muestra un breve resumen de la sintaxis de línea de comandos de BSCMAKE.

La siguiente línea de comandos indica a BSCMAKE que realice una compilación completa de MAIN. BSC de tres archivos *`.sbr`* . También indica a BSCMAKE que excluya las instancias duplicadas de TOOLBOX.h:

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Consulte también

[Referencia de BSCMAKE](bscmake-reference.md)
