---
title: Advertencia del compilador (nivel 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: dd150621ad3474444861982c095ae8a6addb52fa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779211"
---
# <a name="compiler-warning-level-1-c4489"></a>Advertencia del compilador (nivel 1) C4489

'especificador': no se permite en el método de interfaz 'method'; invalidar especificadores solo se permiten en métodos de clase de valor y de clase ref

Se usó incorrectamente una palabra clave de especificador en un método de interfaz.

Para obtener más información, consulte [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

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