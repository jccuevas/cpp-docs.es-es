---
title: Compilador advertencia (nivel 1) C4584 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9db97bf35034f7ca628f860924bfb9a1fccc942f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036259"
---
# <a name="compiler-warning-level-1-c4584"></a>Advertencia del compilador (nivel 1) C4584

'class1': clase base 'clase2' ya es una clase base de 'Clase3'

La clase definida se hereda de dos clases, uno de los cuales hereda de la otra. Por ejemplo:

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

En este caso, podría generarse una advertencia en la clase C, ya que hereda de una clase y clase B, que también se hereda de la clase A. Esta advertencia sirve como recordatorio de que debe calificar totalmente el uso de los miembros de estas clases base o se generará un error del compilador debido a la ambigüedad en cuanto a qué miembro de clase se hace referencia.