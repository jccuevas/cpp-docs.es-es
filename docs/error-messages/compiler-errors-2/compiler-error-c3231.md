---
title: Error del compilador C3231 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57727fbd71314201ec76119d37ab9c73b01d471d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097320"
---
# <a name="compiler-error-c3231"></a>Error del compilador C3231

'arg': argumento de tipo de plantilla no puede usar un parámetro de tipo genérico

Las instancias de las plantillas se crean en tiempo de compilación, mientras que las instancias de los genéricos se crean en tiempo de ejecución. Por consiguiente, no es posible generar código genérico que pueda llamar a la plantilla, porque no se pueden crear instancias de la plantilla en tiempo de ejecución si finalmente se conoce el tipo genérico.

El ejemplo siguiente genera C3231:

```
// C3231.cpp
// compile with: /clr /LD
template <class T> class A;

generic <class T>
ref class C {
   void f() {
      A<T> a;   // C3231
   }
};
```