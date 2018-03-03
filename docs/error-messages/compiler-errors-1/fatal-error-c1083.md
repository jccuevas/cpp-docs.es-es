---
title: Error irrecuperable C1083 | Documentos de Microsoft
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1083
dev_langs:
- C++
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd929403afc86beabf185d099a79bfab5578482a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1083"></a>Error irrecuperable C1083

> No se puede abrir *filetype* archivo: '*archivo*': *mensaje*

El compilador genera un error C1083 cuando no se puede encontrar un archivo requiere. Hay varias causas posibles para este error. Una búsqueda de inclusión incorrecto ruta de acceso o nombre incorrecto o que faltan archivos de encabezado son las causas más comunes, pero otros tipos de archivo y los problemas pueden hacer C1083. Estas son algunas de las razones comunes por qué el compilador genera este error.

## <a name="the-specified-file-name-is-wrong"></a>El nombre de archivo especificado es incorrecto

El nombre de un archivo está mal escrito. Por ejemplo,

`#include <algorithm.h>`

no se encuentra el archivo deseado. Mayoría de los archivos de encabezado de biblioteca estándar de C++ no tiene una extensión de nombre de archivo .h. El \<algoritmo > encabezado no se encontraría por este `#include` directiva. Para corregir este problema, compruebe que se ha especificado el nombre de archivo correcto, como en este ejemplo:

`#include <algorithm>`

Algunos encabezados de la biblioteca de C en tiempo de ejecución se encuentran en un subdirectorio del directorio de inclusión estándar. Por ejemplo, para incluir sys/Types.h, debe incluir el nombre del subdirectorio sys en el `#include` directiva:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>El archivo no se incluye en la ruta de acceso de búsqueda de inclusión

El compilador no puede encontrar el archivo utilizando las reglas de búsqueda establecidas por una directiva `#include` o `#import`. Por ejemplo, cuando un nombre de archivo de encabezado está entre comillas,

`#include "myincludefile.h"`

Esto indica al compilador que busque el archivo en el mismo directorio que contiene el archivo de origen en primer lugar y, a continuación, busque en otras ubicaciones especificadas por el entorno de compilación. Si las comillas contienen una ruta de acceso absoluta, el compilador solo busca el archivo en esa ubicación. Si las comillas contienen una ruta de acceso relativa, el compilador busca el archivo en el directorio relativo al directorio de origen.

Si el nombre está incluido entre corchetes angulares,

`#include <stdio.h>`

el compilador sigue una ruta de acceso de búsqueda definida por el entorno de compilación, el **/I** opción del compilador, el **/X** opción del compilador y la **INCLUDE** variable de entorno. Para obtener más información, incluidos detalles concretos sobre el orden de búsqueda usado para buscar un archivo, consulte [#include (directiva) (C/C ++)](../../preprocessor/hash-include-directive-c-cpp.md) y [#import (directiva)](../../preprocessor/hash-import-directive-cpp.md).

Si los archivos de inclusión en otro directorio en relación con el directorio de origen, y utilizar una ruta de acceso relativa en su incluyen directivas, debe usar comillas dobles en lugar de corchetes angulares. Por ejemplo, si su myheader.h del archivo de encabezado está en un subdirectorio de los orígenes del proyecto con el nombre de encabezados, este ejemplo no se puede encontrar el archivo y hace C1083:

`#include <headers\myheader.h>`

pero este ejemplo funciona:

`#include "headers\myheader.h"`

Rutas de acceso relativas también pueden utilizarse con los directorios en la ruta de acceso de búsqueda de inclusión. Si agrega un directorio a la **INCLUDE** variable de entorno o a su **directorios de inclusión** ruta de acceso en Visual Studio, no agregue también parte de la ruta de acceso a las directivas de inclusión. Por ejemplo, si el encabezado se encuentra en \path\example\headers\myheader.h y agregue \path\example\headers\ a la **directorios de inclusión** ruta de acceso en Visual Studio, pero el `#include` directiva hace referencia al archivo como

`#include <headers\myheader.h>`

a continuación, no se encuentra el archivo. Utilice la ruta de acceso correcta en relación con el directorio especificado en la ruta de acceso de búsqueda de inclusión. En este ejemplo, puede cambiar la ruta de acceso de búsqueda de inclusión a \path\example\, o quitar el segmento de ruta de acceso de headers\ desde el `#include` directiva.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de bibliotecas de terceros y Vcpkg

Si ve este error al tratar de configurar una biblioteca de terceros como parte de la compilación, considere la posibilidad de usar [Vcpkg](../../vcpkg.md), el Administrador de paquetes de Visual C++, para instalar y compile la biblioteca. Vcpkg admite un elevado y creciente [lista de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports)y establece todas las propiedades de configuración y las dependencias necesarias para las compilaciones correcta como parte de su proyecto. Para obtener más información, vea relacionado [Blog de Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) post.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>El archivo está en el proyecto, pero no la ruta de acceso de búsqueda de inclusión

Incluso si los archivos de encabezado se indican en **el Explorador de soluciones** como parte de un proyecto, los archivos solo se encuentran por el compilador cuando se conocen por un `#include` o `#import` la directiva en un origen de archivo y se encuentran en un incluir la ruta de acceso de búsqueda. Los diferentes tipos de compilaciones podrían usar distintas rutas de búsqueda. El **/X** opción del compilador puede utilizarse para excluir directorios de la ruta de acceso de búsqueda de inclusión. Esto permite que distintas compilaciones puedan usar diferentes archivos de inclusión que tienen el mismo nombre, pero se mantienen en directorios distintos. Ésta es una alternativa a la compilación condicional utilizando los comandos de preprocesador. Para obtener más información sobre la **/X** opción del compilador, vea [/X (omitir estándar incluyen rutas de acceso)](../../build/reference/x-ignore-standard-include-paths.md).

Para corregir este problema, corrija la ruta que el compilador utiliza para buscar el archivo incluido o importado. Un nuevo valor predeterminado de usos de proyecto incluyen rutas de acceso de búsqueda. Tendrá que modificar la ruta de acceso de búsqueda de inclusión para agregar un directorio para el proyecto. Si realiza la compilación en la línea de comandos, agregue la ruta de acceso a la **INCLUDE** variable de entorno o el **/I** opción del compilador para especificar la ruta de acceso al archivo.

Para establecer la ruta de acceso del directorio de inclusión en Visual Studio, abra el proyecto **páginas de propiedades** cuadro de diálogo. Seleccione **directorios de VC ++** en **propiedades de configuración** en el panel izquierdo y, a continuación, edite la **directorios de inclusión** propiedad. Para obtener más información acerca de los directorios de CAL por usuario y por proyecto realiza la búsqueda del compilador en Visual Studio, vea [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md). Para obtener más información sobre la **/I** opción del compilador, vea [/I (directorios de inclusión adicionales)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>No se establece la inclusión de línea de comandos o el entorno de LIB

Cuando el compilador se invoca en la línea de comandos, suelen usarse las variables de entorno para especificar rutas de búsqueda. Si la ruta de acceso de búsqueda descrita por la **INCLUDE** o **LIB** variable de entorno no está configurada correctamente, puede generar un error C1083. Se recomienda usar un acceso directo del símbolo para desarrolladores para establecer el entorno básico para la línea de comandos genera. Para obtener más información, consulte vea [generar C o C++ en la línea de comandos](../../build/building-on-the-command-line.md). Para obtener más información sobre cómo usar las variables de entorno, consulte [Cómo: utilizar Variables de entorno en una compilación](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>El archivo esté bloqueado o en uso

Si está utilizando otro programa para editar o tener acceso al archivo, puede tener bloqueado el archivo. Cierre el archivo en el otro programa. A veces, el otro programa puede ser propio Visual Studio, si está utilizando opciones de compilación paralela. Si al desactivar la opción de compilación paralela hace que el error desaparece, a continuación, éste es el problema. Otros sistemas de compilación paralelo también pueden tener este problema. Tenga cuidado establecer las dependencias de archivos y proyectos, por lo que el orden de compilación es correcta. En algunos casos, considere la posibilidad de crear un proyecto intermedio para forzar el orden de dependencia de compilación para un archivo común que se puede crear varios proyectos. Los programas antivirus a veces temporalmente bloquean archivos modificados recientemente para el análisis. Si es posible, considere la posibilidad de excluir los directorios de compilación del proyecto desde el programa antivirus.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Se ha incluido una versión incorrecta de un nombre de archivo

Un error C1083 también puede indicar que la versión incorrecta de un archivo está incluida. Por ejemplo, una compilación podría incluir la versión incorrecta de un archivo que tiene una directiva `#include` para un archivo de encabezado que no está previsto para esa compilación. Por ejemplo, determinados archivos sólo se pueden aplicar a x86 se compila, o para las compilaciones de depuración. Cuando el archivo de encabezado no se encuentra, el compilador genera un error C1083. La corrección para este problema es utilizar el archivo correcto y no agregar el archivo de encabezado o directorio a la compilación.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Los encabezados precompilados aún no se precompilan

Cuando se configura un proyecto para usar encabezados precompilados, los archivos pertinentes .pch se tienen que crear para que los archivos que utilizan el contenido del encabezado puedan compilarse. Por ejemplo, el archivo de stdafx.cpp se crea automáticamente en el directorio del proyecto para los proyectos nuevos. Se compila primero el archivo para crear archivos de encabezado precompilados. En el diseño del proceso de compilación normal, esto se hace automáticamente. Para obtener más información, consulte [crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Otras causas

- Se ha instalado un SDK o una biblioteca de terceros, pero no ha abierto una nueva ventana del símbolo del sistema para desarrolladores después el SDK o biblioteca se instala. Si el SDK o la biblioteca agrega archivos a la **INCLUDE** ruta de acceso, puede que necesite abrir una nueva ventana de símbolo del sistema para desarrolladores para recoger estos cambios de la variable de entorno.

- El archivo usa código administrado, pero la opción del compilador **/CLR** no se ha especificado. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

- El archivo se compila mediante un diferentes **/ analyze** valor de la opción de compilador que se usa para precompilar los encabezados. Cuando los encabezados para un proyecto se precompilan, todos deben usar la misma **/ analyze** configuración. Para obtener más información, consulte [/analize (Análisis de código)](../../build/reference/analyze-code-analysis.md).

- El archivo, el directorio o el disco es de solo lectura.

- Visual Studio o las herramientas de línea de comandos no tiene permisos suficientes para leer el archivo o el directorio. Esto puede ocurrir, por ejemplo, cuando los archivos del proyecto tienen una propiedad diferente que el proceso se ejecuta Visual Studio o las herramientas de línea de comandos. A veces se puede corregir este problema mediante la ejecución de Visual Studio o el símbolo del sistema para desarrolladores como administrador.

- No hay suficientes identificadores de archivo. Cierre algunas aplicaciones y, a continuación, compile de nuevo. Esta condición es poco habitual en circunstancias normales. Sin embargo, puede aparecer cuando se compilan proyectos grandes en un equipo con memoria física limitada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un error C1083 cuando el archivo de encabezado `"test.h"` no existe en el directorio de origen o en la ruta de acceso de búsqueda de inclusión.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Para obtener información sobre cómo compilar proyectos de C o C++ en el IDE o en la línea de comandos e información acerca de cómo establecer variables de entorno, consulte [compilar programas de C o C++](../../build/building-c-cpp-programs.md).

## <a name="see-also"></a>Vea también

[Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties)