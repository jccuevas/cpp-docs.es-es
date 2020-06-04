---
title: Error del compilador C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206033"
---
# <a name="compiler-error-c2383"></a>Error del compilador C2383

'*Symbol*': no se permiten argumentos predeterminados en este símbolo

El C++ compilador no permite argumentos predeterminados en punteros a funciones.

Este código fue aceptado por el compilador de Microsoft C++ en las versiones anteriores a Visual Studio 2005, pero ahora produce un error. Para el código que funciona en todas las versiones C++de Visual, no asigne un valor predeterminado a un argumento de puntero a función.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2383 y se muestra una posible solución:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
