---
title: Advertencia del compilador (nivel 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: 4da96fd13fe9ba03c19808d32d3cdd9c73ec2b18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584735"
---
# <a name="compiler-warning-level-1-c4489"></a>Advertencia del compilador (nivel 1) C4489

'especificador': no se permite en el método de interfaz 'method'; invalidar especificadores solo se permiten en métodos de clase de valor y de clase ref

Se usó incorrectamente una palabra clave de especificador en un método de interfaz.

Para obtener más información, consulte [especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4489.

```
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```