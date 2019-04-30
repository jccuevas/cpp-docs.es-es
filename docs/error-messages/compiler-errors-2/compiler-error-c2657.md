---
title: Error del compilador C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: 4e2816092b3c0c210ae2c544e9bf9a823a9c5d18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360442"
---
# <a name="compiler-error-c2657"></a>Error del compilador C2657

' clase:: *' se encuentra al principio de una instrucción (¿olvidó especificar un tipo?)

La línea comenzaba con un identificador de puntero a miembro.

Este error puede deberse a un especificador de tipo que falta en la declaración de un puntero a un miembro.

El ejemplo siguiente genera C2657:

```
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```