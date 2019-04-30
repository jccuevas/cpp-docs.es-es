---
title: Error irrecuperable C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: e1c00a001c807b0cc6a5946b61ca4e9d5dc0167a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229128"
---
# <a name="fatal-error-c1197"></a>Error irrecuperable C1197

no puede hacer referencia 'a mscorlib.dll_1' porque el programa ya hacía referencia a ''a mscorlib.dll_2'

El compilador se asocia a una versión de common language runtime.  Sin embargo, se ha intentado hacer referencia a una versión de un archivo de common language runtime desde una versión anterior.

Para resolver este error, solo los archivos de referencia de la versión de common language runtime que se incluye con la versión de Visual C++ se compilación con.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```