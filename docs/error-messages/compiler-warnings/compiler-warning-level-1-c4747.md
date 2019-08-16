---
title: Advertencia del compilador (nivel 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: ecaabd482049771b1d3915470a2be7a52e36d361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404031"
---
# <a name="compiler-warning-level-1-c4747"></a>Advertencia del compilador (nivel 1) C4747

Llamada administrada 'entrypoint': No se puede ejecutar código administrado en un bloqueo del cargador, incluido el DLL entrypoint y las llamadas alcanzadas desde el punto

El compilador encontró un punto de entrada DLL (probable) compilado para MSIL.  Debido a posibles problemas con la carga de un archivo DLL cuyo punto de entrada se ha compilado en MSIL, se desaconseja encarecidamente compilar una función de punto de entrada DLL en MSIL.

Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) y [Error de las herramientas del vinculador LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. No se compile el módulo con **/CLR**.

1. Marque la función de punto de entrada con `#pragma unmanaged`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4747.

```
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