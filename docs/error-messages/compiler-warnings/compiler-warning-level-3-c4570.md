---
title: Advertencia del compilador (nivel 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 386d7c210c77469d67a75d66f7d8ae35c105b3b0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777918"
---
# <a name="compiler-warning-level-3-c4570"></a>Advertencia del compilador (nivel 3) C4570

'type': no se declara explícitamente como abstracto pero tiene funciones abstractas

Un tipo que contiene [abstracta](../../extensions/abstract-cpp-component-extensions.md) funciones deben estar marcadas como abstracto.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4570.

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```