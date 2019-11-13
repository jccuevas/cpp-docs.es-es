---
title: ADVERTENCIA del compilador (nivel 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 623b29d345a850cc312f23e4c521aa0be5b47242
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052444"
---
# <a name="compiler-warning-level-1-c4747"></a>ADVERTENCIA del compilador (nivel 1) C4747

Llamando a ' EntryPoint ' administrado: el código administrado no se puede ejecutar en un bloqueo del cargador, incluido el punto de entrada del archivo DLL y las llamadas alcanzadas desde el punto de entrada del archivo DLL

El compilador encontró un punto de entrada de DLL (probable) compilado en MSIL.  Debido a los posibles problemas de carga de un archivo DLL cuyo punto de entrada se ha compilado en MSIL, no se recomienda compilar una función de punto de entrada de DLL en MSIL.

Para obtener más información, vea [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) y [error de las herramientas del vinculador LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. No compile el módulo con **/CLR**.

1. Marque la función de punto de entrada con `#pragma unmanaged`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4747.

```cpp
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```