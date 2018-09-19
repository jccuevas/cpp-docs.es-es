---
title: Error del compilador C3252 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70a38090bcbe1a984e643d6d995abe2c79339163
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080628"
---
# <a name="compiler-error-c3252"></a>Error del compilador C3252

'método': no se puede reducir la accesibilidad de un método virtual en un tipo administrado o WinRT

Una clase que implementa un método virtual de una clase base o cualquier método de una interfaz no puede reducir el acceso a ese método.

Tenga en cuenta que todos los métodos de una interfaz son públicos.

En el ejemplo siguiente se genera el error C3252 y se muestra cómo corregirlo.

```
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```