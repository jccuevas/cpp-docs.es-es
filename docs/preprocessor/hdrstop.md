---
title: hdrstop | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs:
- C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e571229602a311633fc7425384544c53813b935
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059719"
---
# <a name="hdrstop"></a>hdrstop
Proporciona control adicional sobre los nombres de archivo de la precompilación y sobre la ubicación en la que se guarda el estado de la compilación.

## <a name="syntax"></a>Sintaxis

```
#pragma hdrstop [( "filename" )]
```

## <a name="remarks"></a>Comentarios

El *filename* es el nombre del archivo de encabezado precompilado para utilizar o crear (dependiendo de si [/Yu](../build/reference/yu-use-precompiled-header-file.md) o [/Yc](../build/reference/yc-create-precompiled-header-file.md) se especifica). Si *filename* no contiene una especificación de ruta de acceso, se supone que el archivo de encabezado precompilado en el mismo directorio que el archivo de origen.

Si un archivo de C o C++ contiene una **hdrstop** pragma cuando se compila con `/Yc`, el compilador guarda el estado de la compilación hasta la ubicación de la directiva pragma. El estado compilado del código que aparece detrás de la instrucción pragma no se guarda.

Use *filename* un nombre al archivo de encabezado precompilado en el que se guarda el estado compilado. Un espacio entre **hdrstop** y *filename* es opcional. El nombre de archivo especificado en el **hdrstop** pragma es una cadena y, por tanto, está sujeto a las restricciones de cualquier cadena de C o C++. En concreto, debe incluirse entre comillas y usar el carácter de escape (la barra diagonal inversa) para especificar nombres de directorio. Por ejemplo:

```
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

El nombre del archivo de encabezado precompilado se determina según las reglas siguientes, en orden de prioridad:

1. El argumento para el `/Fp` opción del compilador

2. El *filename* argumento `#pragma hdrstop`

3. El nombre base del archivo de código fuente con una extensión .PCH

Para el `/Yc` y `/Yu` opciones, si ninguna de las dos opciones de compilación ni la **hdrstop** pragma especifica un nombre de archivo, el nombre base del archivo de origen se utiliza como el nombre base del archivo de encabezado precompilado.

Puede usar también comandos de preprocesamiento para realizar la sustitución de macros del modo siguiente:

```
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Las siguientes reglas determinan dónde el **hdrstop** se puede colocar la pragma:

- Debe aparecer fuera de cualquier declaración o definición de datos o función.

- Se debe especificar en el archivo de código fuente, no en un archivo de encabezado.

## <a name="example"></a>Ejemplo

```
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    ...                              // Some code to display string
}
#pragma hdrstop
```

En este ejemplo, el **hdrstop** pragma aparece después de que se han incluido dos archivos y se ha definido una función insertada. Esto podría parecer, a primera vista, una colocación extraña de una instrucción pragma. Tenga en cuenta, sin embargo, que con las opciones de precompilación manuales, `/Yc` y `/Yu`, con el **hdrstop** pragma hace posible que se precompilen los archivos de código fuente completo, incluido el código insertado. El compilador de Microsoft no le limita a precompilar solo las declaraciones de datos.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)