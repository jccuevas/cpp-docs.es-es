---
title: include_alias (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218903"
---
# <a name="include_alias-pragma"></a>include_alias (Pragma)

Especifica que cuando se encuentra *alias_filename* en una `#include` Directiva, el compilador sustituye *actual_filename* en su lugar.

## <a name="syntax"></a>Sintaxis

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename*>  **,** *actual_filename*) \<> 

## <a name="remarks"></a>Comentarios

La Directiva pragma **include_alias** permite sustituir archivos que tienen nombres o rutas de acceso diferentes para los nombres de archivo incluidos en los archivos de código fuente. Por ejemplo, algunos sistemas de archivos permiten nombres de archivo de encabezado más largos que el límite del sistema de archivos FAT 8,3. El compilador no puede simplemente truncar los nombres más largos a 8,3, porque los primeros ocho caracteres de los nombres de archivo de encabezado más largos pueden no ser únicos. Siempre que el compilador ve la cadena `#include` *alias_filename* en una directiva, sustituye el nombre *actual_filename* en su lugar. A continuación, carga el archivo de encabezado *actual_filename* . Esta directiva pragma debe aparecer antes de las directivas `#include` correspondientes. Por ejemplo:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

El alias que se va a buscar debe coincidir exactamente con la especificación. El caso, la ortografía y el uso de comillas dobles o corchetes angulares deben coincidir. La Directiva pragma **include_alias** realiza una coincidencia de cadena simple en los nombres de archivo. No se realiza ninguna otra validación de nombre de archivo. Por ejemplo, dadas las siguientes directivas,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

no se realiza ninguna sustitución de alias, ya que las cadenas del archivo de encabezado no coinciden exactamente. Además, los nombres de archivo de encabezado que se `/Yu` usan `/Yc` como argumentos para las opciones `hdrstop` del compilador y, o la pragma, no se sustituyen. Por ejemplo, si el archivo de código fuente contiene la siguiente directiva,

```cpp
#include <AppleSystemHeaderStop.h>
```

la opción del compilador correspondiente debe ser

> **/YcAppleSystemHeaderStop.h**

Puede usar la Directiva pragma **include_alias** para asignar cualquier nombre de archivo de encabezado a otro. Por ejemplo:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

No mezcle nombres de archivo entre comillas dobles con nombres de archivo entre corchetes angulares. Por ejemplo, dadas las dos `#pragma include_alias` directivas anteriores, el compilador no realiza ninguna `#include` sustitución en las siguientes directivas:

```cpp
#include <api.h>
#include "stdio.h"
```

Además, la directiva siguiente genera un error:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

El nombre de archivo indicado en los mensajes de error, o como el valor `__FILE__` de la macro predefinida, es el nombre del archivo una vez finalizada la sustitución. Por ejemplo, vea la salida después de las siguientes directivas:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Error en *VERYLONGFILENAME. H* genera el siguiente mensaje de error:

```Output
myfile.h(15) : error C2059 : syntax error
```

Tenga en cuenta también que no se admite la transitividad. Dadas las siguientes directivas,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

el compilador busca el archivo *Two. h* en lugar de *tres. h*.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
