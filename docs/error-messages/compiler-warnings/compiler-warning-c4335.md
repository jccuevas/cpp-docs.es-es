---
title: ADVERTENCIA del compilador C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: ccb00118d0c6895eee84976bb01472ea2f98353d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627121"
---
# <a name="compiler-warning-c4335"></a>ADVERTENCIA del compilador C4335

Se detectó un formato de archivo Mac: convierta el archivo de origen en formato de DOS o UNIX.

El carácter de finalización de línea de la primera línea de un archivo de código fuente es Macintosh Style (' \r ') en lugar de UNIX (' \n ') o DOS (' \r\n ').

Esta advertencia siempre se emite como error.  Consulte pragma [Warning](../../preprocessor/warning.md) para obtener información sobre cómo deshabilitar esta advertencia.  Además, esta advertencia solo se emite una vez por operación de compilación. Por lo tanto, si hay varias directivas de `#include` que especifican archivos en formato Macintosh, C4335 solo se emitirá una vez.

Una manera de generar archivos en formato Macintosh es usar las **Opciones avanzadas para guardar** (en el menú **archivo** ) de Visual Studio.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4335.

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
