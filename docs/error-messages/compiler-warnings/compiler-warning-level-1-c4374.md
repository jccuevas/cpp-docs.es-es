---
title: Compilador advertencia (nivel 1) C4374 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4374
dev_langs:
- C++
helpviewer_keywords:
- C4374
ms.assetid: 4ac9aaec-d815-4b6e-825f-fa872092dd3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4a1372e6a9608781b4f57a10b57641efd02a89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116066"
---
# <a name="compiler-warning-level-1-c4374"></a>Advertencia del compilador (nivel 1) C4374

'function1': el método no virtual 'function2' no implementará el método de interfaz

El compilador esperaba encontrar el [virtual](../../cpp/virtual-specifier.md) palabra clave en una definición de método.

El ejemplo siguiente genera C4374:

```
// C4374.cpp
// compile with: /clr /W1 /c /WX
public interface class I {
   void f();
};

public ref struct B {
   void f() {
      System::Console::WriteLine("B::f()");
   }
};

public ref struct C {
   virtual void f() {
      System::Console::WriteLine("C::f()");
   }
};

public ref struct D : B, I {};   // C4374
public ref struct E : C, I {};   // OK
```