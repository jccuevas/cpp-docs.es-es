---
title: Error del compilador C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 34d19e8e9f51c90c48ec0d429f98bb82e3d829d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228543"
---
# <a name="compiler-error-c2750"></a>Error del compilador C2750

'type': no se puede utilizar 'new' en el tipo de referencia; Utilice 'gcnew' en su lugar

Para crear una instancia de un tipo CLR, lo que hace que la instancia que se colocará en el montón de recolección, debe usar [gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md).

El ejemplo siguiente genera C2750:

```
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```