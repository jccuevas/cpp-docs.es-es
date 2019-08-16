---
title: Error del compilador C3252
ms.date: 11/04/2016
f1_keywords:
- C3252
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
ms.openlocfilehash: ee9245fb8eb89b9234e76dc10304b1d05bc1fdcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164844"
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