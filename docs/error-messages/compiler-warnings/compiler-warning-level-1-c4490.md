---
title: Advertencia del compilador (nivel 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: 0a14b99a7c4c222bbb8020a27c630a42b1cf0329
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186600"
---
# <a name="compiler-warning-level-1-c4490"></a>Advertencia del compilador (nivel 1) C4490

' override ': uso incorrecto del especificador de invalidación; ' function ' no coincide con un método de clase Ref base

Se usó incorrectamente un especificador de invalidación. Por ejemplo, no se invalida una función de interfaz, sino que se implementa.

Para obtener más información, vea [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4490.

```cpp
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
