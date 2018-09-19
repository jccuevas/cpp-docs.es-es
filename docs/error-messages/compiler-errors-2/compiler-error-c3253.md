---
title: Error del compilador C3253 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3253
dev_langs:
- C++
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f47ff3ab9094e7926453ec4eb5964485cf16f945
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065613"
---
# <a name="compiler-error-c3253"></a>Error del compilador C3253

'function': error con invalidación explícita

Invalidación explícita se especificó incorrectamente. Por ejemplo, no se puede especificar una implementación para un reemplazo que también se especifica como puro. Para obtener más información, consulte [invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md).

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