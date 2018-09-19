---
title: Advertencia del compilador C4335 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b28909d0c4b663fffeacbec58ad694131bb008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036584"
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