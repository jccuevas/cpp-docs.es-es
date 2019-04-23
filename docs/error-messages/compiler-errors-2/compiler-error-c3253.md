---
title: Error del compilador C3253
ms.date: 11/04/2016
f1_keywords:
- C3253
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
ms.openlocfilehash: 5d161dfab8dff48a1ddd5a8a5036c0bb4d5549aa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775771"
---
# <a name="compiler-error-c3253"></a>Error del compilador C3253

'function': error con invalidación explícita

Invalidación explícita se especificó incorrectamente. Por ejemplo, no se puede especificar una implementación para un reemplazo que también se especifica como puro. Para obtener más información, consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

El ejemplo siguiente genera C3253:

```
// C3253.cpp
// compile with: /clr
public interface struct I {
   void a();
   void b();
   void c();
};

public ref struct R : I {
   virtual void a() = 0, I::a {}   // C3253
   virtual void b() = I::a {}   // OK
   virtual void c() = 0;   // OK
};
```