---
title: Error del compilador C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 9edb30e574e212bd30fd60dd3ce5aaddc650dc11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744438"
---
# <a name="compiler-error-c2433"></a>Error del compilador C2433

' Identifier ': ' modificador ' no se permite en declaraciones de datos

Los modificadores `friend`, `virtual`y `inline` no se pueden utilizar para las declaraciones de datos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2433.

```cpp
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```
