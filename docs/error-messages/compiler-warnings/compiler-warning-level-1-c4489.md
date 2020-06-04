---
title: Advertencia del compilador (nivel 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: e9811e9f9c17463fdcd550ffd82af4f81a40bb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186613"
---
# <a name="compiler-warning-level-1-c4489"></a>Advertencia del compilador (nivel 1) C4489

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
