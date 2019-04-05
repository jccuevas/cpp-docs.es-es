---
title: Error del compilador C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781918"
---
# <a name="compiler-error-c3622"></a>Error del compilador C3622

'class': una clase declarada como 'palabra clave' no pueden crearse instancias

Se intentó crear una instancia de una clase marcada como [abstracta](../../extensions/abstract-cpp-component-extensions.md). Una clase marcada como `abstract` puede ser una clase base, pero no pueden crearse instancias.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
