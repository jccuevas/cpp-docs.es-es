---
title: Error del compilador C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: c4534b11f3aedf638f69337fb6a7af778e086bb4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778038"
---
# <a name="compiler-error-c3671"></a>Error del compilador C3671

'function_1': función no invalida 'function_2'

Cuando se usa la sintaxis de invalidación explícita, el compilador genera un error si no se reemplaza una función.  Consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3671.

```
// C3671.cpp
// compile with: /clr /c
ref struct S {
   virtual void f();
};

ref struct S1 : S {
   virtual void f(int) new sealed = S::f;   // C3671
   virtual void f() new sealed = S::f;
};
```