---
title: '##include (directiva) (C/C ++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#include'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdf60755591dd37a541c02330554fa4fe9b92ca6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062488"
---
# <a name="include-directive-cc"></a>#include (Directiva) (C/C++)
Indica al preprocesador que trate el contenido de un archivo especificado como si apareciera en el programa de origen en el punto donde aparece la directiva.

## <a name="syntax"></a>Sintaxis

```
#include  "path-spec"
#include  <path-spec>
```

## <a name="remarks"></a>Comentarios

Puede organizar las definiciones de constantes y de macro en los archivos de inclusión y, a continuación, usar **#include** directivas para agregarlos a los archivos de origen. Los archivos de inclusión son también útiles para incorporar declaraciones de variables externas y tipos de datos complejos. Los tipos solo se pueden definir y denominar una sola vez en un archivo de inclusión creado para ese propósito.

`path-spec` es un nombre de archivo que opcionalmente puede ir precedido de una especificación de directorio. El nombre de archivo debe designar un archivo existente. La sintaxis de `path-spec` depende del sistema operativo en el que se compila el programa.

Para obtener información acerca de cómo hacer referencia a ensamblados en una aplicación de C++ que se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), consulte [#using](../preprocessor/hash-using-directive-cpp.md).

Los dos formatos de sintaxis producen el reemplazo de esa directiva por el contenido completo del archivo de inclusión especificado. La diferencia entre los dos formatos es el orden en el que el preprocesador busca los archivos de encabezado si la ruta de acceso que se especifica está incompleta. En la siguiente tabla se muestran las diferencias entre ambos formatos de sintaxis.

|Formato de sintaxis|Acción|
|-----------------|------------|
|Formato con comillas|El preprocesador realiza la búsqueda de archivos de inclusión en este orden:<br /><br /> (1) en el mismo directorio que el archivo que contiene el **#include** instrucción.<br /><br /> (2) en los directorios de abiertas actualmente incluyen archivos, en el orden inverso en el que se abrieron. La búsqueda comienza en el directorio del archivo de inclusión principal y continúa hacia arriba por los directorios de cualquier archivo de inclusión primario principal.<br /><br /> (3) a lo largo de la ruta de acceso especificada por cada `/I` opción del compilador.<br /><br /> 4)<br /><br /> A lo largo de las rutas de acceso especificadas por la variable de entorno INCLUDE.|
|Formato con corchetes angulares|El preprocesador realiza la búsqueda de archivos de inclusión en este orden:<br /><br /> (1) a lo largo de la ruta de acceso especificada por cada `/I` opción del compilador.<br /><br /> (2) cuando se compila desde la línea de comandos, a lo largo de las rutas de acceso especificadas por la variable de entorno INCLUDE.|

El preprocesador detiene la búsqueda en cuanto encuentra un archivo con el nombre especificado. Si incluye una especificación completa y no ambigua de la ruta de acceso del archivo de inclusión entre comillas dobles (" "), el preprocesador busca solo en esa especificación de ruta y omite los directorios estándar.

Si el nombre de archivo que está entre comillas es una especificación incompleta de ruta, el preprocesador busca primero en el directorio de archivo "principal". Un archivo principal es el archivo que contiene el **#include** directiva. Por ejemplo, si incluye un archivo denominado `file2` en un archivo denominado `file1`, `file1` es el archivo principal.

Incluir archivos que pueden ser "anidados"; es decir, un **#include** directiva puede aparecer en un archivo que se denomina por otro **#include** directiva. Por ejemplo, `file2` podría incluir `file3`. En este caso, `file1` todavía sería el elemento primario de `file2` pero sería el "elemento primario principal" de `file3`.

Cuando se anidan los archivos de inclusión y cuando se compila desde la línea de comandos, la búsqueda en los directorios comienza por los directorios del archivo primario y después continúa por los directorios de cualquier archivo primario principal. Es decir, la búsqueda comienza en relación con el directorio que contiene el origen que se procesa actualmente. Si no se encuentra el archivo, la búsqueda se desplaza a los directorios especificados por el `/I` opción del compilador. Por último, se busca en los directorios especificados por la variable de entorno INCLUDE.

En el entorno de desarrollo, se omite la variable de entorno INCLUDE. Para obtener información acerca de cómo establecer los directorios que se buscan archivos de inclusión: Esto también se aplica a la variable de entorno LIB, vea [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md).

Este ejemplo muestra la inclusión de archivo mediante corchetes angulares:

```
#include <stdio.h>
```

En este ejemplo se agrega el contenido del archivo denominado STDIO.H al programa de origen. Los corchetes angulares hacen que el preprocesador busca en los directorios especificados por la variable de entorno INCLUDE para STDIO. H, después de buscar en los directorios especificados por el `/I` opción del compilador.

En el ejemplo siguiente se muestra la inclusión de archivo mediante el formato con comillas:

```
#include "defs.h"
```

En este ejemplo se agrega el contenido del archivo especificado por DEFS.H al programa de origen. Las comillas indican que el preprocesador busca primero en el directorio que contiene el archivo de código fuente primario.

El anidamiento de archivos de inclusión puede continuar hasta 10 niveles. Cuando el anidado **#include** está procesado, el preprocesador continúa insertando el archivo de inclusión envolvente en el archivo de origen.

**Específicos de Microsoft**

Para buscar archivos de origen pueden incluir, el preprocesador busca primero en los directorios especificados por el `/I` opción del compilador. Si el `/I` opción no está presente o se produce un error, el preprocesador utiliza la variable de entorno INCLUDE para buscar los archivos de inclusión entre corchetes angulares. La variable de entorno INCLUDE y `/I` la opción del compilador pueden contener varias rutas de acceso, separadas por punto y coma (;). Si aparece más de un directorio como parte de la `/I` opción o dentro de la variable de entorno INCLUDE, el preprocesador los busca en el orden en que aparecen.

Por ejemplo, el comando

```
CL /ID:\MSVC\INCLUDE MYPROG.C
```

hace que el preprocesador busque en el directorio D: \MSVC\INCLUDE\ archivos de inclusión tales como STDIO.H. Los comandos

```
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

producen el mismo efecto. Si se produce un error en ambos conjuntos de búsquedas, se genera un error grave del compilador.

Si se especifica completamente el nombre de un archivo de inclusión con una ruta de acceso que incluye dos puntos (por ejemplo, F:\MSVC\SPECIAL\INCL\TEST.H), el preprocesador sigue la ruta de acceso.

Archivos de inclusión que se especifican como `#include` "`path-spec`", la búsqueda de directorio comienza con el directorio del archivo primario y, a continuación, continúa con los directorios de los archivos primarios principales. Es decir, la búsqueda comienza en relación con el directorio que contiene el archivo de origen que contiene el **#include** directiva que se está procesando. Si no hay ningún archivo primario principal y no se ha encontrado el archivo, la búsqueda continúa como si el nombre de archivo estuviese entre corchetes angulares.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)