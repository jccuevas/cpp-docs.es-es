---
title: Error del compilador C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: c1467a3c67cccf28cc6b9bd0f987fe77b8da8988
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757883"
---
# <a name="compiler-error-c2833"></a>Error del compilador C2833

' operator Operator ' no es un operador o tipo reconocido

La palabra `operator` debe ir seguida de un operador que desee invalidar o de un tipo que desee convertir.

Para obtener una lista de los operadores que se pueden definir en un tipo administrado, vea [operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).

En el ejemplo siguiente se genera C2833:

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
