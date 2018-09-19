---
title: Compilador advertencia (nivel 4) C4339 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4339
dev_langs:
- C++
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab96374beffed9822b20f4f10db812f170ea6cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025235"
---
# <a name="compiler-warning-level-4-c4339"></a>Advertencia del compilador (nivel 4) C4339

'type': se detectó el uso de un tipo no definido en los metadatos de WinRT o CLR; el uso de este tipo puede provocar una excepción en tiempo de ejecución

No se definió un tipo en el código que se compiló para Windows Runtime o Common Language Runtime. Defina el tipo para evitar una posible excepción en tiempo de ejecución.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El ejemplo siguiente genera el error C4339 y muestra cómo corregirlo:

```
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```