---
title: Error irrecuperable C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747246"
---
# <a name="fatal-error-c1197"></a>Error irrecuperable C1197

no se puede hacer referencia a ' mscorlib. dll_1 ' porque el programa ya hacía referencia a ' mscorlib. dll_2 '

El compilador coincide con una versión de la Common Language Runtime.  No obstante, se ha intentado hacer referencia a una versión de un archivo Common Language Runtime de una versión anterior.

Para resolver este error, solo se deben hacer referencia a los archivos de la versión de la Common Language Runtime que se C++ incluyen con la versión de visual con la que se está compilando.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C1197:

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
