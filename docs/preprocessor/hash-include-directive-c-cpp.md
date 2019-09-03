---
title: '#include (Directiva) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 0792f522427e5658de992969745878894fbd454d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220247"
---
# <a name="include-directive-cc"></a>#include (Directiva) (C++C/)

Indica al preprocesador que trate el contenido de un archivo especificado como si apareciera en el programa de origen en el punto donde aparece la directiva.

## <a name="syntax"></a>Sintaxis

> **#include** "*ruta de acceso: especificación*" \
> **#include** *ruta de acceso: especificación* \<>

## <a name="remarks"></a>Comentarios

Puede organizar las definiciones de constantes y macros en archivos de inclusión y, a continuación, utilizar directivas de **#include** para agregarlas a cualquier archivo de código fuente. Los archivos de inclusión son también útiles para incorporar declaraciones de variables externas y tipos de datos complejos. Los tipos solo se pueden definir y denominar una sola vez en un archivo de inclusión creado para ese propósito.

La *ruta de acceso* es un nombre de archivo que, opcionalmente, puede ir precedido por una especificación de directorio. El nombre de archivo debe designar un archivo existente. La sintaxis de la *ruta de acceso* depende del sistema operativo en el que se compila el programa.

Para obtener información sobre cómo hacer referencia a ensamblados en una C++ aplicación compilada con [/clr](../build/reference/clr-common-language-runtime-compilation.md), vea [#using](../preprocessor/hash-using-directive-cpp.md).

Los dos formatos de sintaxis producen el reemplazo de esa directiva por el contenido completo del archivo de inclusión especificado. La diferencia entre los dos formatos es el orden en el que el preprocesador busca los archivos de encabezado si la ruta de acceso que se especifica está incompleta. En la siguiente tabla se muestran las diferencias entre ambos formatos de sintaxis.

|Formato de sintaxis|.|
|---|------------|
|Formato con comillas|El preprocesador realiza la búsqueda de archivos de inclusión en este orden:<br/><br/> 1) en el mismo directorio que el archivo que contiene la instrucción **#include** .<br/><br/> 2) en los directorios de los archivos de inclusión abiertos actualmente, en el orden inverso en el que se abrieron. La búsqueda comienza en el directorio del archivo de inclusión principal y continúa hacia arriba por los directorios de cualquier archivo de inclusión primario principal.<br/><br/> 3) a lo largo de la ruta de acceso especificada por cada opción del compilador **/i** .<br/><br/> 4) a lo largo de las rutas de acceso especificadas por la variable de entorno INCLUDE.|
|Formato con corchetes angulares|El preprocesador realiza la búsqueda de archivos de inclusión en este orden:<br/><br/> 1) a lo largo de la ruta de acceso especificada por cada opción del compilador **/i** .<br/><br/> 2) cuando la compilación se produce en la línea de comandos, a lo largo de las rutas de acceso especificadas por la variable de entorno INCLUDE.|

El preprocesador detiene la búsqueda en cuanto encuentra un archivo con el nombre especificado. Si se incluye una especificación de ruta de acceso completa y no ambigua para el archivo de inclusión entre`" "`comillas dobles (), el preprocesador solo busca en esa especificación de ruta de acceso y omite los directorios estándar.

Si el nombre de archivo que está entre comillas es una especificación incompleta de ruta, el preprocesador busca primero en el directorio de archivo "principal". Un archivo primario es el archivo que contiene la Directiva de **#include** . Por ejemplo, si incluye un archivo denominado *archivo2* en un archivo denominado *archivo1*, *archivo1* es el archivo primario.

Los archivos de inclusión pueden estar "anidados": Una directiva de **#include** puede aparecer en un archivo denominado por otra directiva **#include** . Por ejemplo, *archivo2* podría incluir *archivo3*. En este caso, *archivo1* todavía sería el elemento primario de *archivo2*, pero sería el "elemento principal" de *archivo3*.

Cuando se anidan los archivos de inclusión y se produce la compilación en la línea de comandos, la búsqueda de directorio comienza en los directorios del archivo primario. Después, continúa a través de los directorios de los archivos primarios principales. Es decir, la búsqueda comienza en relación con el directorio que contiene el origen que se procesa actualmente. Si no se encuentra el archivo, la búsqueda se desplaza a los directorios especificados por la opción del compilador [/i (directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md) . Por último, se busca en los directorios especificados por la variable de entorno INCLUDE.

En el entorno de desarrollo de Visual Studio, se omite la variable de entorno INCLUDE. Para obtener información sobre cómo establecer los directorios en los que se buscan archivos de inclusión y archivos de biblioteca, vea [Página de propiedades de directorios de VC + +](../build/reference/vcpp-directories-property-page.md).

Este ejemplo muestra la inclusión de archivo mediante corchetes angulares:

```C
#include <stdio.h>
```

En este ejemplo se agrega el contenido del archivo denominado STDIO.H al programa de origen. Los corchetes angulares hacen que el preprocesador busque en los directorios especificados por la variable de entorno INCLUDE para STDIO. H, después de buscar en los directorios especificados por la opción del compilador **/i.**

En el ejemplo siguiente se muestra la inclusión de archivo mediante el formato con comillas:

```C
#include "defs.h"
```

En este ejemplo se agrega el contenido del archivo especificado por DEFS.H al programa de origen. Las comillas indican que el preprocesador busca primero en el directorio que contiene el archivo de código fuente primario.

El anidamiento de archivos de inclusión puede continuar hasta 10 niveles. Cuando se procesa el **#include** anidado, el preprocesador continúa insertando el archivo de inclusión envolvente en el archivo de código fuente original.

**Específicos de Microsoft**

Para buscar archivos de código fuente de includable, el preprocesador busca primero los directorios especificados por la opción del compilador **/i.** Si la opción **/i** no está presente, o si se produce un error, el preprocesador utiliza la variable de entorno include para buscar cualquier archivo de inclusión dentro de los corchetes angulares. La variable de entorno INCLUDE y la opción del compilador **/i** pueden contener varias rutas de acceso, separadas por punto y coma ( **;** ). Si aparece más de un directorio como parte de la opción **/i** o en la variable de entorno include, el preprocesador los busca en el orden en el que aparecen.

Por ejemplo, el comando

```cmd
CL /ID:\MSVC\INCLUDE MYPROG.C
```

hace que el preprocesador busque en el directorio D: \MSVC\INCLUDE\ archivos de inclusión tales como STDIO.H. Los comandos

```cmd
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

producen el mismo efecto. Si se produce un error en ambos conjuntos de búsquedas, se genera un error grave del compilador.

Si se especifica completamente el nombre de un archivo de inclusión con una ruta de acceso que incluye dos puntos (por ejemplo, F:\MSVC\SPECIAL\INCL\TEST.H), el preprocesador sigue la ruta de acceso.

En el caso de los archivos de `#include "path-spec"`inclusión que se especifican como, la búsqueda de directorio comienza con el directorio del archivo primario y, a continuación, continúa a través de los directorios de los archivos primarios principales. Es decir, la búsqueda comienza en relación con el directorio que contiene el archivo de código fuente que contiene la Directiva de **#include** que se está procesando. Si no hay ningún archivo primario principal y no se ha encontrado el archivo, la búsqueda continúa como si el nombre de archivo estuviese entre corchetes angulares.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)\
[/I (directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md)
