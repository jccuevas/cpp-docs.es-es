---
title: ADVERTENCIA del compilador (nivel 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: 78ceecb5918ccb74bd61afe62bbf8b542d585f81
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966201"
---
# <a name="compiler-warning-level-1-c4489"></a>ADVERTENCIA del compilador (nivel 1) C4489

' Specifier ': no se permite en el método de interfaz ' Method '; los especificadores de invalidación solo se permiten en métodos de clase Ref y de clase de valor

Una palabra clave de especificador se usó incorrectamente en un método de interfaz.

Para obtener más información, vea [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4489.

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```