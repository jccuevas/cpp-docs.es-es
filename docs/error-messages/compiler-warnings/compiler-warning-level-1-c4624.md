---
title: Compilador advertencia (nivel 1) C4624 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4624
dev_langs:
- C++
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbc482fe693da366a3ba3ce7e53d5e8bbf23618c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118396"
---
# <a name="compiler-warning-level-1-c4624"></a>Advertencia del compilador (nivel 1) C4624

'derived class': el destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se ha eliminado

Un destructor no está accesible o se eliminó en una clase base y, por tanto, no se generó para una clase derivada. Cualquier intento de crear un objeto de este tipo en la pila provocará un error del compilador.

El ejemplo siguiente genera el error C4624 y muestra cómo corregirlo:

```
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```