---
title: Advertencia del compilador C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: 43c2f5d9092cdbad14e429349bd7d04e236b75e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151856"
---
# <a name="compiler-warning-c4335"></a>Advertencia del compilador C4335

Formato de archivo Mac detectado: convierta el archivo de origen en formato DOS o UNIX

El carácter de terminación de la línea de la primera línea de un archivo de origen es el estilo de Macintosh ('\r') en lugar de UNIX ('\n') o DOS ('\r\n').

Esta advertencia siempre se emite como un error.  Consulte [advertencia](../../preprocessor/warning.md) pragma para obtener información acerca de cómo deshabilitar esta advertencia.  Además, esta advertencia solo se emite una vez por operación de compilación. Por lo tanto, si hay varios `#include` directivas que especifican los archivos en formato Macintosh, C4335 solo se emitirá una vez.

Es una manera de generar archivos en formato Macintosh mediante el **opciones avanzadas para guardar** (en el **archivo** menú) en Visual Studio.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4335.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```