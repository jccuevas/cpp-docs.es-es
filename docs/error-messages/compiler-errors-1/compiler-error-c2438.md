---
title: Error del compilador C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: da6443f3f319c864b53f6d077e8bf99faffc5888
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744321"
---
# <a name="compiler-error-c2438"></a>Error del compilador C2438

' Identifier ': no se pueden inicializar datos de clase estáticos mediante el constructor

Un constructor se usa para inicializar un miembro estático de una clase. Los miembros estáticos se deben inicializar en una definición fuera de la declaración de clase.

En el ejemplo siguiente se genera C2438:

```cpp
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
