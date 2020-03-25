---
title: Advertencia del compilador (nivel 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: 5d6e89efb042b8f757feec3911b160961e51f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199698"
---
# <a name="compiler-warning-level-1-c4624"></a>Advertencia del compilador (nivel 1) C4624

'derived class': el destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se ha eliminado

Un destructor no está accesible o se eliminó en una clase base y, por tanto, no se generó para una clase derivada. Cualquier intento de crear un objeto de este tipo en la pila provocará un error del compilador.

El ejemplo siguiente genera el error C4624 y muestra cómo corregirlo:

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```
