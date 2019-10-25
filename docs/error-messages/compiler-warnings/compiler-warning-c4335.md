---
title: Advertencia del compilador C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: d44a1ae5354e8d22e41694f4d6df42ad22c3986d
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127166"
---
# <a name="compiler-warning-c4335"></a>Advertencia del compilador C4335

Se detectó un formato de archivo Mac: convierta el archivo de origen en formato de DOS o UNIX.

El carácter de finalización de línea de la primera línea de un archivo de código fuente es Macintosh Style (' \r ') en lugar de UNIX (' \n ') o DOS (' \r\n ').

Esta advertencia siempre se emite como error.  Consulte pragma [Warning](../../preprocessor/warning.md) para obtener información sobre cómo deshabilitar esta advertencia.  Además, esta advertencia solo se emite una vez por operación de compilación. Por lo tanto, si hay `#include` varias directivas que especifican archivos en formato de Macintosh, C4335 solo se emitirá una vez.

Una manera de generar archivos en formato Macintosh es usar las **Opciones avanzadas para guardar** (en el menú **archivo** ) de Visual Studio.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4335.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
