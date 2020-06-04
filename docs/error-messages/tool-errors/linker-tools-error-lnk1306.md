---
title: Error de las herramientas del vinculador LNK1306
ms.date: 11/04/2016
f1_keywords:
- LNK1306
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
ms.openlocfilehash: ddaa8797e0cf8ff617408aedc770b21cc656cec4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160463"
---
# <a name="linker-tools-error-lnk1306"></a>Error de las herramientas del vinculador LNK1306

> No se pueden administrar la función de punto de entrada de archivo DLL; compilar a código nativo

`DllMain` no se puede compilar en MSIL; se debe compilar en código nativo.

Para resolver este problema,

- Compile el archivo que contiene el punto de entrada sin **/CLR**.

- Coloque el punto de entrada en un `#pragma unmanaged` sección.

Para obtener más información, consulte:

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [managed, unmanaged](../../preprocessor/managed-unmanaged.md)

- [Inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md)

- [Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](../../build/run-time-library-behavior.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK1306.

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

Para corregir este problema, no use la opción /clr para compilar este archivo, o usar un `#pragma` directiva para colocar la definición de punto de entrada en una sección no administrada como se muestra en este ejemplo:

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```
