---
title: Error del compilador C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 26819f1928223b5fa96d275290105f32787057f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208329"
---
# <a name="compiler-error-c2733"></a>Error del compilador C2733

segunda vinculación C de la función sobrecargada 'function' no permitido

Se declara más de una función sobrecargada con vinculación C. Cuando se usa la vinculación C, sólo una forma de una función especificada puede ser externa. Puesto que las funciones sobrecargadas tienen el mismo nombre no representativo, que no pueden utilizarse con programas de C.

El ejemplo siguiente genera C2733:

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```