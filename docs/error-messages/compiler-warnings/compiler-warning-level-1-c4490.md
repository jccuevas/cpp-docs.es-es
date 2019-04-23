---
title: Advertencia del compilador (nivel 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: bf51994c210bd751e0d29bec169dfc4366784486
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779432"
---
# <a name="compiler-warning-level-1-c4490"></a>Advertencia del compilador (nivel 1) C4490

'override': uso incorrecto del especificador de invalidación; 'function' no coincide con un método de clase ref base

Un especificador de invalidación se usó incorrectamente. Por ejemplo, no reemplaza una función de la interfaz, implementarla.

Para obtener más información, consulte [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4490.

```
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```