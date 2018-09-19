---
title: Error del compilador C3910 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3910
dev_langs:
- C++
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc5a719cac97a16ef6b8eaff277a9526a2f135ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073843"
---
# <a name="compiler-error-c3910"></a>Error del compilador C3910

'evento': debe definir el miembro 'método'

Se definió un evento, pero no contiene el método de descriptor de acceso especificada, se requiere.

Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).

El ejemplo siguiente genera C3910:

```
// C3910.cpp
// compile with: /clr /c
delegate void H();
ref class X {
   event H^ E {
      // uncomment the following lines
      // void add(H^) {}
      // void remove( H^ h ) {}
      // void raise( ) {}
   };   // C3910

   event H^ E2; // OK data member
};
```