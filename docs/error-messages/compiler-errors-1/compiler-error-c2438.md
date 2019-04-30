---
title: Error del compilador C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: b2861090b5f7629c7f0cd94ea38a99e888909258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375761"
---
# <a name="compiler-error-c2438"></a>Error del compilador C2438

'identifier': no se puede inicializar los datos de clase estáticos mediante un constructor

Un constructor se utiliza para inicializar a un miembro estático de una clase. Los miembros estáticos se deben inicializar en una definición fuera de la declaración de clase.

El ejemplo siguiente genera C2438:

```
// C2438.cpp
struct X {
   X(int i) : j(i) {}   // C2438
   static int j;
};

int X::j;

int main() {
   X::j = 1;
}
```