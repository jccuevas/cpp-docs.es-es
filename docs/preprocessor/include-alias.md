---
title: include_alias
ms.date: 12/16/2018
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: 9d32cad2533b6044348651797d0278bcbebcafd6
ms.sourcegitcommit: ae2f71fe0d64f1a90ef722759fe93c82abc064ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53587881"
---
# <a name="includealias"></a>include_alias

Especifica que, cuando *alias_filename* se encuentra en un `#include` la directiva, el compilador sustituye *actual_filename* en su lugar.

## <a name="syntax"></a>Sintaxis

> #<a name="pragma-includealiasaliasfilename-actualfilename"></a>pragma include_alias ("*alias_filename*","*actual_filename*")
> #<a name="pragma-includealiasaliasfilename-actualfilename"></a>pragma include_alias (\<*alias_filename*>, \< *actual_filename*>)

## <a name="remarks"></a>Comentarios

El **include_alias** directiva pragma permite sustituir los archivos que tienen nombres diferentes o las rutas de acceso para los nombres de archivo incluidos archivos de código fuente. Por ejemplo, algunos sistemas de archivos permiten nombres de archivo de encabezado más largo que el límite del sistema de archivos FAT 8.3. No basta con que el compilador trunque los nombres más largos a 8.3, porque los ocho primeros caracteres de los nombres de archivo de encabezado más largos pueden no ser únicos. Cada vez que el compilador encuentra la *alias_filename* cadena, sustituye *actual_filename*y busca el archivo de encabezado *actual_filename* en su lugar. Esta directiva pragma debe aparecer antes de las directivas `#include` correspondientes. Por ejemplo:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

El alias que se esté buscando debe coincidir exactamente con la especificación, tanto en uso de mayúsculas y minúsculas, como de ortografía y comillas dobles o corchetes angulares. El **include_alias** pragma realiza la búsqueda de coincidencias en los nombres de archivo de cadena simple; se realiza ninguna otra validación de nombre de archivo. Por ejemplo, dadas las siguientes directivas,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

no se realiza ninguna operación de alias (sustitución), ya que las cadenas del archivo de encabezado no coinciden exactamente. Además, los nombres de encabezado utilizados como argumentos para el `/Yu` y `/Yc` opciones del compilador, o el `hdrstop` pragma, no se sustituyen. Por ejemplo, si el archivo de código fuente contiene la siguiente directiva,

```cpp
#include <AppleSystemHeaderStop.h>
```

la opción del compilador correspondiente debe ser

> /YcAppleSystemHeaderStop.h

Puede usar el **include_alias** pragma para asignar cualquier nombre de archivo de encabezado a otro. Por ejemplo:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

No mezcle los nombres de archivo delimitados por comillas con los nombres de archivo entre corchetes angulares. Por ejemplo, dadas las dos anteriores `#pragma include_alias` directivas, el compilador no realiza ninguna sustitución en las siguientes `#include` directivas:

```cpp
#include <api.h>
#include "stdio.h"
```

Además, la directiva siguiente genera un error:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Tenga en cuenta que el nombre de archivo indicado en mensajes de error, o como el valor de predefinido `__FILE__` macro, es el nombre del archivo después de haber realizado la sustitución. Por ejemplo, puede ver la salida después de las siguientes directivas:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Un error en VERYLONGFILENAME. H, genera el mensaje de error siguiente:

```Output
myfile.h(15) : error C2059 : syntax error
```

Observe también que no se admite la transitividad. Dadas las siguientes directivas,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

el compilador busca el archivo two.h en lugar de Three.h.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
