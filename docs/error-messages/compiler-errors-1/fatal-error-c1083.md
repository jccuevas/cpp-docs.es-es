---
title: Error irrecuperable C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: b982c3adf59789f6c48e7e0f54ed4e71539692ad
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630773"
---
# <a name="fatal-error-c1083"></a>Error irrecuperable C1083

> No se puede abrir el archivo *filetype* : '*File*': *mensaje*

El compilador genera un error C1083 cuando no puede encontrar un archivo que requiere. Hay muchas causas posibles de este error. Una ruta de acceso de búsqueda de inclusión incorrecta o archivos de encabezado que faltan o que son incorrectos son las causas más comunes, pero otros tipos de archivo y problemas también pueden provocar C1083. Estos son algunos de los motivos comunes por los que el compilador genera este error.

## <a name="the-specified-file-name-is-wrong"></a>El nombre de archivo especificado es incorrecto

El nombre de un archivo está mal escrito. Por ejemplo,

`#include <algorithm.h>`

no se encuentra el archivo deseado. La C++ mayoría de los archivos de encabezado de la biblioteca estándar no tienen una extensión de nombre de archivo. h. La \< `#include` Directiva no encontró el encabezado > del algoritmo. Para corregir este problema, compruebe que se ha escrito el nombre de archivo correcto, como en este ejemplo:

`#include <algorithm>`

Algunos encabezados de la biblioteca de C en tiempo de ejecución se encuentran en un subdirectorio del directorio de inclusión estándar. Por ejemplo, para incluir sys/Types. h, debe incluir el nombre del subdirectorio sys en `#include` la Directiva:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>El archivo no se incluye en la ruta de acceso de búsqueda de inclusión

El compilador no puede encontrar el archivo utilizando las reglas de búsqueda establecidas por una directiva `#include` o `#import`. Por ejemplo, cuando un nombre de archivo de encabezado está entre comillas,

`#include "myincludefile.h"`

Esto indica al compilador que busque el archivo en el mismo directorio que contiene primero el archivo de código fuente y, a continuación, busque en otras ubicaciones especificadas por el entorno de compilación. Si las comillas contienen una ruta de acceso absoluta, el compilador solo busca el archivo en esa ubicación. Si las comillas contienen una ruta de acceso relativa, el compilador busca el archivo en el directorio relativo al directorio de origen.

Si el nombre está entre corchetes angulares,

`#include <stdio.h>`

el compilador sigue una ruta de búsqueda definida por el entorno de compilación, la opción del compilador **/i** , la opción del compilador **/x** y la variable de entorno **include** . Para obtener más información, incluidos los detalles específicos sobre el orden de búsqueda usado para buscar un archivo, vea [Directiva deC++#include (C/)](../../preprocessor/hash-include-directive-c-cpp.md) y [#import Directiva](../../preprocessor/hash-import-directive-cpp.md).

Si los archivos de inclusión están en otro directorio relativo al directorio de origen y utiliza una ruta de acceso relativa en las directivas de inclusión, debe usar comillas dobles en lugar de corchetes angulares. Por ejemplo, si el archivo de encabezado MyHeader. h se encuentra en un subdirectorio de los orígenes de proyecto denominados headers, este ejemplo no podrá encontrar el archivo y provocará C1083:

`#include <headers\myheader.h>`

pero este ejemplo funciona:

`#include "headers\myheader.h"`

Las rutas de acceso relativas también se pueden usar con directorios en la ruta de búsqueda de inclusión. Si agrega un directorio a la variable de entorno **include** o a la ruta de acceso de los **directorios de inclusión** en Visual Studio, no agregue también parte de la ruta de acceso a las directivas Include. Por ejemplo, si el encabezado se encuentra en \path\example\headers\myheader.h y agrega \path\example\headers\ a la ruta de acceso de los **directorios de inclusión** en Visual Studio `#include` , pero la Directiva hace referencia al archivo como

`#include <headers\myheader.h>`

no se encuentra el archivo. Use la ruta de acceso correcta en relación con el directorio especificado en la ruta de acceso de búsqueda de inclusión. En este ejemplo, puede cambiar la ruta de acceso de búsqueda de\, inclusión a \path\example o quitar los encabezados \ segmento de `#include` ruta de acceso de la Directiva.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de la biblioteca de terceros y Vcpkg

Si ve este error al intentar configurar una biblioteca de terceros como parte de la compilación, considere la posibilidad de usar [Vcpkg](../../vcpkg.md), el administrador de paquetes C++ visuales, para instalar y compilar la biblioteca. Vcpkg admite una lista grande y creciente [de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports), y establece todas las propiedades de configuración y las dependencias necesarias para compilaciones correctas como parte del proyecto. Para obtener más información, consulte la entrada de [blog visual C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) relacionada.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>El archivo está en el proyecto, pero no en la ruta de acceso de búsqueda de inclusión

Incluso cuando los archivos de encabezado se muestran en **Explorador de soluciones** como parte de un proyecto, el compilador solo busca los archivos cuando se hace referencia a `#include` ellos `#import` mediante una directiva o en un archivo de código fuente, y se encuentran en una ruta de búsqueda de inclusión. Los diferentes tipos de compilaciones podrían usar distintas rutas de búsqueda. La opción del compilador **/x** se puede usar para excluir directorios de la ruta de acceso de búsqueda de inclusión. Esto permite que distintas compilaciones puedan usar diferentes archivos de inclusión que tienen el mismo nombre, pero se mantienen en directorios distintos. Ésta es una alternativa a la compilación condicional utilizando los comandos de preprocesador. Para obtener más información acerca de la opción del compilador **/x** , vea [/x (omitir rutas de acceso de inclusión estándar)](../../build/reference/x-ignore-standard-include-paths.md).

Para corregir este problema, corrija la ruta que el compilador utiliza para buscar el archivo incluido o importado. Un nuevo proyecto utiliza rutas de acceso de búsqueda de inclusión predeterminadas. Es posible que tenga que modificar la ruta de acceso de búsqueda de inclusión para agregar un directorio para el proyecto. Si está compilando en la línea de comandos, agregue la ruta de acceso a la variable de entorno **include** o la opción del compilador **/i** para especificar la ruta de acceso al archivo.

Para establecer la ruta de acceso al directorio de inclusión en Visual Studio, abra el cuadro de diálogo **páginas de propiedades** del proyecto. Seleccione **directorios de VC + +** en **propiedades de configuración** en el panel izquierdo y, a continuación, edite la propiedad **directorios de inclusión** . Para obtener más información sobre los directorios por usuario y por proyecto buscados por el compilador en Visual Studio, consulte la [Página de propiedades directorios de VC + +](../../build/reference/vcpp-directories-property-page.md). Para obtener más información acerca de la opción del compilador **/i** , vea [/i (directorios de inclusión adicionales)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>La línea de comandos INCLUDE o el entorno de LIB no están establecidos

Cuando el compilador se invoca en la línea de comandos, suelen usarse las variables de entorno para especificar rutas de búsqueda. Si la ruta de acceso de búsqueda descrita por la variable de entorno **include** o **lib** no se ha establecido correctamente, se puede generar un error C1083. Se recomienda encarecidamente usar un acceso directo del símbolo del sistema para desarrolladores para establecer el entorno básico para las compilaciones de línea de comandos. Para obtener más información, vea compilar [C/C++ en la línea de comandos](../../build/building-on-the-command-line.md). Para obtener más información sobre cómo usar variables de entorno, [consulte Cómo: Usar variables de entorno en una](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)compilación.

## <a name="the-file-may-be-locked-or-in-use"></a>El archivo puede estar bloqueado o en uso

Si usa otro programa para editar o tener acceso al archivo, es posible que el archivo esté bloqueado. Intente cerrar el archivo en el otro programa. En ocasiones, el otro programa puede ser Visual Studio, si usa opciones de compilación paralelas. Si al desactivar la opción compilación paralela se elimina el error, este es el problema. Otros sistemas de compilación en paralelo también pueden tener este problema. Tenga cuidado al establecer las dependencias de archivo y de proyecto para que el orden de compilación sea correcto. En algunos casos, considere la posibilidad de crear un proyecto intermedio para forzar el orden de las dependencias de compilación para un archivo común que pueda estar compilado en varios proyectos. A veces, los programas antivirus bloquean temporalmente los archivos modificados recientemente para su análisis. Si es posible, considere la posibilidad de excluir los directorios de compilación del proyecto del detector de virus.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Se ha incluido una versión incorrecta de un nombre de archivo

Un error C1083 también puede indicar que la versión incorrecta de un archivo está incluida. Por ejemplo, una compilación podría incluir la versión incorrecta de un archivo que tiene una directiva `#include` para un archivo de encabezado que no está previsto para esa compilación. Por ejemplo, ciertos archivos solo se pueden aplicar a las compilaciones x86 o a las compilaciones de depuración. Cuando el archivo de encabezado no se encuentra, el compilador genera un error C1083. La corrección para este problema es utilizar el archivo correcto y no agregar el archivo de encabezado o directorio a la compilación.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Los encabezados precompilados aún no se precompilan

Cuando se configura un proyecto para usar encabezados precompilados, los archivos pertinentes .pch se tienen que crear para que los archivos que utilizan el contenido del encabezado puedan compilarse. Por ejemplo, el archivo *PCH. cpp* (*stdafx. cpp* en Visual Studio 2017 y versiones anteriores) se crea automáticamente en el directorio del proyecto para los proyectos nuevos. Se compila primero el archivo para crear archivos de encabezado precompilados. En el diseño del proceso de compilación típico, esto se hace automáticamente. Para obtener más información, vea [crear archivos de encabezado](../../build/creating-precompiled-header-files.md)precompilados.

## <a name="additional-causes"></a>Otras causas

- Ha instalado un SDK o una biblioteca de terceros, pero no ha abierto una nueva ventana del símbolo del sistema para desarrolladores después de instalar el SDK o la biblioteca. Si el SDK o la biblioteca agrega archivos a la ruta de acceso de **inclusión** , puede que tenga que abrir una nueva ventana del símbolo del sistema del desarrollador para seleccionar estos cambios de variables de entorno.

- El archivo utiliza código administrado, pero no se especifica la opción del compilador **/CLR** . Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

- El archivo se compila con un valor de opción del compilador **/Analyze** diferente al que se usa para precompilar los encabezados. Cuando se precompilan los encabezados de un proyecto, todos deben usar la misma configuración de **/Analyze** . Para obtener más información, consulte [/analize (Análisis de código)](../../build/reference/analyze-code-analysis.md).

- El archivo o directorio creado por el subsistema de Windows para Linux, está habilitada la distinción de mayúsculas y minúsculas por directorio, y el caso especificado de una ruta de acceso o un archivo no coincide con el de la ruta de acceso o el archivo del disco.

- El archivo, el directorio o el disco es de solo lectura.

- Visual Studio o las herramientas de línea de comandos no tienen permisos suficientes para leer el archivo o el directorio. Esto puede ocurrir, por ejemplo, cuando los archivos de proyecto tienen una propiedad diferente que el proceso que ejecuta Visual Studio o las herramientas de línea de comandos. A veces, este problema se puede solucionar ejecutando Visual Studio o el símbolo del sistema para desarrolladores como administrador.

- No hay suficientes identificadores de archivo. Cierre algunas aplicaciones y, a continuación, compile de nuevo. Esta condición es poco habitual en circunstancias normales. Sin embargo, puede aparecer cuando se compilan proyectos grandes en un equipo con memoria física limitada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un error C1083 cuando el `"test.h"` archivo de encabezado no existe en el directorio de origen o en la ruta de acceso de búsqueda de inclusión.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Para obtener información sobre cómo compilarC++ proyectos de C/en el IDE o en la línea de comandos, así como información sobre cómo establecer las variables de entorno, vea [proyectos y sistemas de compilación](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Vea también

- [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties)
