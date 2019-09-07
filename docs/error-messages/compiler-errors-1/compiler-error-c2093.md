---
title: Error del compilador C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741154"
---
# <a name="compiler-error-c2093"></a>Error del compilador C2093

' variable1 ': no se puede inicializar con la dirección de la variable automática ' variable2 '

Al compilar con [/za](../../build/reference/za-ze-disable-language-extensions.md), el programa ha intentado usar la dirección de una variable automática como inicializador.

En el ejemplo siguiente se genera C2093:

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```