---
title: Error del compilador C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 1fbbc3d63386ebe98a447de8b7166a5263d2168f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208420"
---
# <a name="compiler-error-c2728"></a>Error del compilador C2728

'type': una matriz nativa no puede contener este tipo

Se usó la sintaxis de creación de matrices para crear una matriz de objetos administrados u objetos de WinRT. No se puede crear una matriz de objetos administrados u objetos de WinRT mediante la sintaxis de matriz nativa.

Para obtener más información, vea [Matriz](../../extensions/arrays-cpp-component-extensions.md).

El ejemplo siguiente genera el error C2728 y muestra cómo corregirlo:

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
