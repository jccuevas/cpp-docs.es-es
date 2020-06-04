---
title: hdrstop (Pragma)
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221022"
---
# <a name="hdrstop-pragma"></a>hdrstop (Pragma)

Proporciona un mayor control sobre los nombres de archivo de precompilación y sobre la ubicación en la que se guarda el estado de compilación.

## <a name="syntax"></a>Sintaxis

> **#pragma hdrstop** [("*nombre de archivo*")]

## <a name="remarks"></a>Comentarios

*Filename* es el nombre del archivo de encabezado precompilado que se va a usar o crear (dependiendo de si se especifica [/Yu](../build/reference/yu-use-precompiled-header-file.md) o [/YC](../build/reference/yc-create-precompiled-header-file.md) ). Si *filename* no contiene una especificación de ruta de acceso, se supone que el archivo de encabezado precompilado está en el mismo directorio que el archivo de origen.

Si un archivo C C++ o contiene una pragma **hdrstop** cuando se compila `/Yc`con, el compilador guarda el estado de la compilación en la ubicación de la Directiva pragma. El estado compilado de cualquier código que sigue a Pragma no se guarda.

Use *filename* para asignar un nombre al archivo de encabezado precompilado en el que se guarda el estado compilado. Un espacio entre **hdrstop** y *filename* es opcional. El nombre de archivo especificado en el pragma **hdrstop** es una cadena y, por tanto, está sujeto a las restricciones de cualquier C++ C o cadena. En concreto, debe incluirse entre comillas y usar el carácter de escape (la barra diagonal inversa) para especificar nombres de directorio. Por ejemplo:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

El nombre del archivo de encabezado precompilado se determina según las reglas siguientes, en orden de prioridad:

1. El argumento para la `/Fp` opción del compilador

2. El argumento *filename* para`#pragma hdrstop`

3. El nombre base del archivo de código fuente con una extensión .PCH

Para las `/Yc` opciones `/Yu` y, si ninguna de las dos opciones de compilación ni la pragma **hdrstop** especifican un nombre de archivo, el nombre base del archivo de código fuente se utiliza como el nombre base del archivo de encabezado precompilado.

Puede usar también comandos de preprocesamiento para realizar la sustitución de macros del modo siguiente:

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Las siguientes reglas rigen dónde se puede colocar la pragma **hdrstop** :

- Debe aparecer fuera de cualquier declaración o definición de datos o función.

- Se debe especificar en el archivo de código fuente, no en un archivo de encabezado.

## <a name="example"></a>Ejemplo

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

En este ejemplo, la pragma **hdrstop** aparece después de que se hayan incluido dos archivos y se haya definido una función insertada. En primer lugar, es posible que esta ubicación parezca ser una ubicación impar para la pragma. No obstante, tenga en cuenta que el uso de las opciones `/Yc` de `/Yu`precompilación manual, y, con la pragma **hdrstop** permite precompilar archivos de código fuente completos, incluso código en línea. El compilador de Microsoft no le limita a precompilar solo las declaraciones de datos.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
