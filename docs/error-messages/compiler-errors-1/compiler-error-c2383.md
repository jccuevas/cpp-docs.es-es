---
title: Error del compilador C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 06d4c19208bd242169e1cd07a71e8a568f46f7b1
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344813"
---
# <a name="compiler-error-c2383"></a>Error del compilador C2383

'*símbolo*': no se permiten argumentos predeterminados en este símbolo

El compilador de C++ no permiten argumentos predeterminados en punteros a funciones.

Este código fue aceptado por el compilador de Visual C++ en las versiones anteriores de Visual Studio 2005, pero ahora produce un error. Para el código que funciona en todas las versiones de Visual C++, no asigne un valor predeterminado para un argumento de puntero a función.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2383 y muestra una posible solución:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```